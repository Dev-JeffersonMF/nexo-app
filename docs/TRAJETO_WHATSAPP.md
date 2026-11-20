# Trajeto do WhatsApp validado no aparelho (adb)

Data: 20/11/2026 · Aparelho: `ZF524N85RP` (moto g84 5G, Android 15) ·
WhatsApp PT-BR · resolução 1080×2400.

Driver usado: `nexo-drive.ps1` (a lógica de tap/screenshot foi reproduzida em
Python com `adb shell uiautomator dump`, muito mais confiável que OCR para
ler os IDs do WhatsApp).

## 1. Enviar mensagem para o contato “Mica”

| Passo | Ação | Evidência (resource-id / texto) |
| --- | --- | --- |
| 1 | Abrir WhatsApp | `am start -n com.whatsapp/.Main` |
| 2 | Tocar na busca | `com.whatsapp:id/my_search_bar` → `com.whatsapp:id/search_text` (“Pergunte à Meta AI ou pesquise”), centro ≈ (610, 316) |
| 3 | Digitar `mica` | `adb shell input text mica` → `com.whatsapp:id/search_input` com “mica” |
| 4 | Tocar no resultado | `com.whatsapp:id/conversations_row_contact_name` = “Mica”, centro ≈ (228, 404) |
| 5 | Conferir a conversa | topo `com.whatsapp:id/conversations_contact_name` = “Mica” |
| 6 | Tocar no campo | `com.whatsapp:id/entry` (placeholder “Mensagem”), centro ≈ (408, 2208) com teclado fechado |
| 7 | Escrever o texto | `TESTE NEXO seta direita` (no app, via `ACTION_SET_TEXT`) |
| 8 | **Tocar na seta** | com teclado aberto a barra sobe: `com.whatsapp:id/send` em `[937,1427][1057,1547]`, centro **(997, 1487)**; content-desc “Enviar” na variante acessível |
| 9 | Confirmar | `com.whatsapp:id/entry` volta a “Mensagem” (placeholder) e a bolha `TESTE NEXO seta direita` aparece em `[283,1316][883,1397]` |

**Nunca** usar `KEYCODE_ENTER` / `input keyevent 66`. O envio é o botão da
seta à direita do campo.

## 2. Enviar mensagem para a lista de transmissão

| Passo | Ação | Evidência |
| --- | --- | --- |
| 1 | Voltar para a lista de conversas | 2× BACK (a 1ª fecha o teclado) |
| 2 | Tocar em “Mais opções” | `com.whatsapp:id/menuitem_overflow`, centro ≈ (1030, 176) |
| 3 | Tocar em “Listas de transmissão” | `com.whatsapp:id/menuitem_new_broadcast`, título `com.whatsapp:id/title` = “Listas de transmissão” |
| 4 | Conferir a tela | `com.whatsapp:id/broadcast_list_header` = “Suas transmissões” |
| 5 | Abrir a lista | `com.whatsapp:id/broadcast_list_name` = “Isak, Leo Novo” (2 destinatários), centro ≈ (540, 845) |
| 6 | Conversa da lista | `com.whatsapp:id/conversation_contact_name` = “2 destinatários” |
| 7 | Escrever no campo | `com.whatsapp:id/entry` |
| 8 | **Tocar na seta** | `com.whatsapp:id/send`, centro (997, 1487) — aparece com o texto |
| 9 | Confirmar | campo volta a “Mensagem”; bolha `TESTE NEXO lista transmissao` aparece |

## 3. Como isso entrou no Nexo

- `app/core/whatsappTrajeto.mjs`: passos exatos (incluindo o `id/send`) usados
  por `recordLearnedPath('whatsapp-message'|'whatsapp-broadcast', …)` no
  `App.tsx`. É o “aprender o caminho” da memória neural.
- `native-android/java/com/jefferson/nexo/rea/ReaLayoutAnalyzer.kt`: o mapa
  `send_button` já aponta para `primaryId = "send"` (a seta), com reservas
  `send_container` / `conversation_entry_action_button` e descrição “Enviar”.
  Os containers não recebem clique; a seta sim.
- `NexusAccessibilityService.kt`: `writeAndSend` espera a seta aparecer,
  `tapSendAndConfirm` toca nela e só devolve sucesso quando o campo volta ao
  placeholder. Não há nenhum `KEYCODE_ENTER` no projeto.
- `App.tsx`: ao terminar o envio, `awaitingAnswerRef` é limpo e um comando
  novo durante uma pergunta pendente não é mais engolido como resposta.

## 4. Música em segundo plano (OiTube)

Validado no aparelho: com o OiTube em segundo plano e a launcher na frente,
`dumpsys media_session` mostra `package=com.skipads.oitube.official`,
`state=PLAYING(3)` — o áudio continua sem o app aberto na tela.

Sequência correta no código (antes estava errada):

1. `MusicLauncher.play()` abre o vídeo (`https://www.youtube.com/watch?v=<id>`)
   no OiTube — a busca no YouTube é feita para achar o `videoId`.
2. O OiTube fica na frente **só até o play ser confirmado** pelo acessibilidade.
3. `onPlaying` traz o `MainActivity` do Nexo para a frente; o som continua.
4. Removido o `minimizeApp()` (tecla HOME) que mandava o usuário para a home e
   impedia o acessibilidade de enxergar o botão de play.
5. Se o OiTube não estiver instalado, `AppDetector.installFromPlayStore()`
   abre `market://details?id=com.skipads.oitube.official` (reserva: URL https).

Comandos com a música tocando (todos viram `media`):
`pula`→next, `voltar`→prev, `pausar`→pause, `continuar`→play,
`parar`/`para musica`→stop (fecha o OiTube e chama `returnToAssistant()`).

Rádio: `toca radio`→`radio-play` (pergunta a emissora); `para radio`/
`para a radio`→`radio-stop`. “toca a rádio Itatiaia **para mim**” continua
sendo play — “para” ali é preposição.

## 5. Limitação

O app Nexo não estava instalado no aparelho durante esta análise, então o
trajeto foi validado diretamente no WhatsApp via adb e depois transcrito para
o código. Para validar ponta a ponta no app é preciso instalar um APK com
estas alterações e deixar a acessibilidade do Nexo ligada (`Auto-Bot`).
