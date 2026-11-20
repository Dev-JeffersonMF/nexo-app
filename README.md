# Nexo

Assistente pessoal para Android, em português, com voz própria e automação do dia a dia.

Versão atual: **3.0.14** (versionCode 44) · pacote `com.jefferson.nexo` · Android 7.0+.

## Download

O APK assinado está na Release **v3.0.14** deste repositório:

https://github.com/Dev-JeffersonMF/nexo-app/releases/tag/v3.0.14

Instalação via adb:

```bash
adb install -r app-release.apk
```

## Recursos

- Voz Sukuna gerada pela Fish Audio, com banco aprendido no aparelho e TTS do Android como reserva.
- Entendimento de comandos em português, com gíria, abreviações e números por extenso.
- WhatsApp: mensagem para contato, lista de transmissão, chamadas de voz e vídeo.
- Música no OiTube em segundo plano, com comandos de pular, voltar, pausar, continuar e parar.
- Rádio, lembretes, alarmes, notificações, clima, horóscopo, loterias e notícias.
- Mascote flutuante para dar comandos sem abrir o app; sete aparências.
- Aprendizado local: frases e caminhos de tela aprendidos com o uso.

## Privacidade

Conversa, memória neural e banco de falas ficam no aparelho. Não existe conta, login ou painel na nuvem.
A síntese de voz usa a API Fish Audio apenas para gerar texto ainda não aprendido; a chave fica fora deste repositório.

## Permissões

O app pede microfone, notificações e acessibilidade. A acessibilidade é o Auto-Bot: ela permite ao Nexo operar WhatsApp e controles de mídia na tela, sempre sob consentimento do usuário.

## Licença

Uso pessoal.

## Comandos de voz

### Rádio
- `toca radio` — pergunta qual emissora; `toca a radio Itatiaia` — toca direto.
- `para radio` / `para a radio` — desliga a rádio.

### Música (OiTube)
- `toca musica` — o Nexo pergunta qual música ou cantor; com o nome, abre o OiTube, pesquisa e dá play em segundo plano.
- Com a música tocando: `pausar`, `continuar`, `pular`, `voltar`, `parar musica`.
- `parar musica` encerra o player e volta para a tela do Nexo.

### Clima e horas
- `clima em <cidade>` / `qual o tempo em <cidade>` — previsão da cidade.
- `que horas sao` / `me informa as horas` — diz a hora exata.

### Chamadas
- `ligar para <contato>` — chamada de **voz pelo WhatsApp** (padrão).
- `chamar no whatsapp para <contato>` — chamada de voz; `videochamada para <contato>` — chamada de vídeo.
- `discar para <contato ou numero>` / `ligacao telefonica para <contato>` — chamada pelo **telefone** (operadora).
- Se o tipo não for dito, o Nexo pergunta voz ou vídeo; se o contato faltar, pergunta para quem.

### WhatsApp — mensagens
- `manda mensagem para <contato>` — pergunta o texto e envia; `manda mensagem para <contato> dizendo <texto>` — envia direto.
- O envio é feito pelo **botão de seta** da conversa, nunca pela tecla Enter.
- `manda mensagem para lista de transmissao dizendo <texto>` — envia a mensagem falada para a lista de transmissão do WhatsApp.
- Comando novo dito durante uma pergunta pendente não é perdido.

### Horóscopo
- `horoscopo de <signo>` / `qual o meu signo` — horóscopo do signo informado.

### Lembretes e alarmes
- `cria lembrete` / `me lembra de ...` — o Nexo pergunta a descrição, o dia e o horário; também aceita `cria lembrete de <texto> amanha as 8h`.
- **PARAR**: cala o alarme/lembrete, fecha a tela e **apaga o registro**.
- **SONECA**: silencia, fecha a tela e volta a falar **5 minutos depois**, repetindo o mesmo alarme até que você toque em **PARAR** ou **SONECA** novamente.

### Vozes
- `Voz do Nexo (Sukuna)` — voz clonada pela Fish Audio; tem um pequeno atraso na primeira frase.
- `Fallback do aparelho (TTS)` — mais rápida, porém mais robótica.
- A troca é feita na aba Voz; uma voz nunca fala por cima da outra.

### Bloqueios
- Bloqueio de número cadastrado e bloqueio por **DDD** (fora da região).
- O Nexo **não anuncia em voz** nada sobre números bloqueados nem DDDs fora da região.
- Notificações de **grupos do WhatsApp** são bloqueadas automaticamente; para reativar um grupo, toque nele na lista de bloqueados.

### Outros modos
- `pesquisar na internet` — o Nexo busca e responde dentro do app, sem abrir navegador.
- **Modo professor** com matérias básicas (explicações de estudo).
