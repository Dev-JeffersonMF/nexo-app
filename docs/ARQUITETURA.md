# Arquitetura do Nexo

Documento de visão geral. O código-fonte é privado; aqui está o que o app faz e como as peças se encaixam.

## Stack

| Camada | Tecnologia |
| --- | --- |
| Interface | React Native 0.88 + Expo 58 + TypeScript |
| Núcleo de linguagem | JavaScript puro (`app/core`) — intenções, comandos, respostas, memória |
| Núcleo nativo | Kotlin + AndroidX |
| Voz neural | sherpa-onnx 2.0.1 (Pocket TTS e Piper) |
| Armazenamento | `SharedPreferences`, `filesDir`, SQLite (Room/WorkManager) |
| Build | Gradle + plugin Expo próprio (`plugins/nexo-native`) |

## Camadas

```
┌─────────────────────────────────────────────────────────────┐
│ Interface (React Native / TypeScript)                       │
│ conversa, ajustes, permissões, mascote, cartão de voz       │
└──────────────────────────┬──────────────────────────────────┘
                           │ ponte nativa (TypeScript ↔ Kotlin)
┌──────────────────────────▼──────────────────────────────────┐
│ Núcleo de linguagem (JS puro, testável)                     │
│ intenção → tarefa → comando → resposta → memória            │
└──────────────────────────┬──────────────────────────────────┘
                           ▼
┌─────────────────────────────────────────────────────────────┐
│ Serviços nativos (Kotlin)                                   │
│ acessibilidade · overlay · chamadas · notificações ·        │
│ lembretes · mídia · atualização · voz                       │
└─────────────────────────────────────────────────────────────┘
```

## Pipeline de voz

```
texto
  │ normalização (acentos, números, abreviações)
  ▼
motor neural
  ├─ 1. Pocket TTS  (modelo clonado, offline, ~190 MB)
  ├─ 2. Piper pt_BR (reserva neural, ~77 MB)
  ├─ 3. Android TTS (voz do sistema)
  └─ 4. expo-speech (último recurso)
  ▼
AudioTrack (streaming) → alto-falante
```

**Decisões de projeto:**

- Carregamento **sob demanda**: o modelo neural só é inicializado na primeira fala, evitando fechamento na abertura do app.
- **Validação de arquivos** antes de carregar; se falhar, o próximo motor assume.
- **Token de parada**: uma nova fala interrompe a anterior sem travar a fila.
- **Acentos preservados** no motor neural; dobrados apenas nas vozes do sistema.

## Automação por acessibilidade

O Nexo usa o `AccessibilityService` do Android para:

- localizar elementos por `resource-id`, texto e `content-desc`;
- aguardar mudanças de estado (por exemplo, o chip “Grupos” ficar selecionado);
- escrever texto e tocar em botões específicos;
- retornar ao app ao concluir.

Boas práticas aplicadas:

- esperas com timeout e novas tentativas;
- seletores com fallback (ID → descrição → coordenadas);
- nunca tocar em elementos não clicáveis (usa o container pai);
- confirmação de envio antes de anunciar sucesso.

## Mascote e segundo plano

- `OverlayService` em primeiro plano, `START_STICKY`.
- `startForeground()` no `onCreate`, evitando o encerramento por atraso.
- Toque curto → microfone; toque longo/duplo → app; arraste → posição salva.
- Nunca aparece sobre a tela do próprio Nexo.
- Áudio de música/rádio é pausado quando o microfone abre.

## Dados no aparelho

| Dado | Onde fica |
| --- | --- |
| Conversa e memória | armazenamento interno do app |
| Notas | armazenamento interno |
| Contatos/grupos ignorados | `SharedPreferences` |
| Lembretes | banco local |
| Modelos de voz | `filesDir/nexo-voice/` |
| Configurações | `SharedPreferences` |

Não há conta, servidor próprio ou sincronização em nuvem.

## Atualização

- Manifesto de atualização versionado e assinado.
- Download do APK oficial, verificação e instalação via `REQUEST_INSTALL_PACKAGES`.
- Builds com assinatura diferente não substituem a oficial.

## Segurança

- APK assinado com certificado próprio (`CN=NEXO`).
- Hash SHA-256 publicado por versão.
- Release privada de código para reduzir cópias alteradas.
- Permissões sensíveis solicitadas de forma explícita e gradual.
- Nenhuma credencial ou chave privada é distribuída no APK.

## Limites conhecidos

- Depende de IDs e layouts de apps de terceiros (WhatsApp), que mudam sem aviso.
- Fabricantes com gerenciamento agressivo de bateria podem encerrar serviços.
- Modelos neurais exigem RAM e armazenamento; em aparelhos modestos há fallback.
- APK grande por levar os modelos embutidos.
