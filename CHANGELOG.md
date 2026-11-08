# Changelog

Todas as mudanças relevantes do Nexo são registradas aqui.
O formato segue [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/) e o versionamento semântico.

---

## [2.4.0] — 2026-11-08

Versão da atualização automática, da tela "Confirmado" e do redesenho de contatos.

### Adicionado

- **Atualização automática**: consulta silenciosa ao abrir e diariamente via `JobScheduler`, download pelo `DownloadManager` e instalação com o instalador do Android.
- **Conferência do APK**: SHA-256, tamanho, pacote, `versionCode` e assinatura digital comparados com o manifesto e com a instalação atual.
- **Tela de novidades pós-atualização** com o botão **Confirmado**, exibida uma única vez por versão.
- **Reabertura automática** do app após instalar (`MY_PACKAGE_REPLACED`).
- **Aba de contatos redesenhada**: resumo, contadores, busca, estado por pessoa e bloqueio de chamada em um toque.
- **Aba de grupos redesenhada**: leitura na aba Conversas pelo 4º filtro "Grupos" e importação de todos os grupos como ignorados.
- **`latest.json`** no repositório público como fonte única da versão disponível.

### Corrigido

- Nomes de grupos lidos de `conversations_row_contact_name`, sem prévias de mensagem.
- Falha na leitura de grupos encerra com erro claro em vez de importar conversas individuais.
- Removido o aviso de atualização antigo, que duplicava a interface.

### Alterado

- O Nexo não navega mais para outras abas do WhatsApp.
- APK corrompido ou incompleto é apagado antes de um novo download completo.
- Versão 2.4.0 (`versionCode` 7).

---

## [2.3.0] — 2026-11-07

Versão de estabilidade e voz própria. Testada em **moto g84 5G (Android 15)**.

### Adicionado

- **Voz própria do Nexo** com Pocket TTS (sherpa-onnx 2.0.1), clonada a partir de uma amostra de referência.
- **Reserva neural Piper pt_BR-faber-medium**, ativada automaticamente se o Pocket falhar.
- **Status de voz** exposto ao app (`getVoiceStatus`), com diagnóstico de modelo carregado.
- **Espera de confirmação** ao selecionar o chip “Grupos” do WhatsApp (até 3 s, com novas tentativas).
- **Fluxo completo de lista de transmissão**: menu → listas → conversa → envio → confirmação.
- **Confirmação falada** após o envio e retorno automático ao Nexo.
- **Testes automatizados** do motor de voz (26 testes).
- Documentação técnica de build e das correções.

### Corrigido

- Fechamento inesperado (SIGABRT) causado pelo carregamento antecipado do Pocket TTS.
- Toque no chip errado do WhatsApp (usava o 3º chip em vez do 4º).
- Toque no `TextView` não clicável da lista de transmissão; agora usa o container da linha.
- Envio por Enter ou toque no container do botão; agora toca diretamente no botão `send`.
- Mascote travado: corrida entre o bridge JS e o toque; agora há fallback por broadcast.
- Morte do processo por `ForegroundServiceDidNotStartInTimeException` (serviço inicia no `onCreate`).
- Mascote aparecendo sobre a tela do próprio Nexo.
- Regras de ProGuard para WorkManager, Room e sherpa-onnx.
- Avisos de `__dirname` no plugin durante o lint.

### Alterado

- Voz neural passa a carregar **sob demanda**, na primeira fala.
- Ordem de fallback: **Piper → Pocket → Android TTS → expo-speech** na inicialização segura, preservando acentos no motor neural.
- `version.json` como fonte única de versão e `versionCode`.
- Assets `.onnx`, `.wav` e `.json` sem compressão no APK, para leitura direta.

### Qualidade

- `npm test`: 26/26.
- `npm run typecheck`: sem erros.
- `npm run lint`: sem erros.
- `npm run piper:check`: todos os assets presentes.
- `assembleRelease` assinado e instalado no dispositivo de teste.

---

## [1.1.0] — versão anterior

### Adicionado

- Palavra de ativação (“Nexo”).
- Microfone compartilhado entre os serviços.
- Frases e respostas via mecanismos do sistema.
- Envio para listas de transmissão do WhatsApp.
- Gravação de áudio.

### Corrigido

- Erros de compilação no Kotlin (`currentActivity`, `jobFinished`, `getOrPut`).
- Fluxo da lista de transmissão e regex mais flexível.
- Atualização nativa e leitura de notificações em segundo plano.

---

## [1.0.0]

- Primeira versão completa: assistente por voz e texto, lembretes, alarmes, chamadas, notificações, mascote flutuante e automação por acessibilidade.
