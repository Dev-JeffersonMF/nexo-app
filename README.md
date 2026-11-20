<div align="center">

# Nexo

**Assistente pessoal para Android, em português, com voz própria e automação do dia a dia.**

[![Versão](https://img.shields.io/badge/vers%C3%A3o-3.0.4-7C5CFF?style=flat-square)](#versão)
[![Android](https://img.shields.io/badge/Android-7.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white)](#requisitos)
[![Licença](https://img.shields.io/badge/licen%C3%A7a-propriet%C3%A1ria-FF4D6D?style=flat-square)](LICENSE.md)

[Download](https://github.com/Dev-JeffersonMF/nexo-app/releases/tag/v3.0.4) · [Notas da versão](CHANGELOG.md) · [Verificação do APK](docs/VERIFICACAO-APK.md) · [Licença](LICENSE.md)

</div>

---

## Versão

| Item | Valor |
| --- | --- |
| **Versão atual** | **3.0.4** (`versionCode` 30) |
| **Pacote** | `com.jefferson.nexo` |
| **Plataforma** | Android 7.0+ (ARM 64/32 bits) |
| **Idioma** | Português do Brasil |
| **APK** | `app-release.apk` na [Release v3.0.4](https://github.com/Dev-JeffersonMF/nexo-app/releases/tag/v3.0.4) |
| **Atualização automática** | Manifesto `latest.json` em `Dev-JeffersonMF/nexo-update` |

> **Nexo não é afiliado ao WhatsApp, Meta, Google ou fabricantes de celular.**
> Automação de apps de terceiros exige consentimento do usuário (serviço de
> acessibilidade do Android).

---

## O que é o Nexo

O Nexo é um assistente Android que conversa por **voz e texto em português** e
executa tarefas no aparelho: WhatsApp (mensagens e lista de transmissão),
chamadas, lembretes, clima, rádio, música no OiTube, notificações e respostas.

A memória e o banco de falas ficam no celular. A voz do Nexo (Sukuna) é gerada
pela Fish Audio com o ID da voz configurado; o áudio gerado fica salvo no
aparelho e toca offline da segunda vez em diante. O TTS do Android é a reserva.

---

## Novidades da 3.0.4

- **Voz sem MP3 no APK** — os 1.107 arquivos antigos ficam fora do bundle; o
  app fala pelo ID da voz Sukuna na Fish Audio e aprende cada frase gerada.
- **Fala sem atraso** — resposta frase a frase com pré-busca da próxima; limite
  de 2,5 s por frase e TTS do aparelho como reserva.
- **Auto-bot e rede neural corrigidos** — comandos de mensagem, rádio, música,
  transmissão, chamada, clima e volume são entendidos e executados sem cair na
  resposta de Ajustes.
- **WhatsApp confiável** — envio pela **seta** da interface (nunca Enter),
  extração correta do texto e nenhum comando perdido durante uma pergunta.
- **Música em segundo plano** — o OiTube toca sem ficar na tela; o Nexo volta
  automaticamente. Controles: `pula`, `voltar`, `pausar`, `continuar`, `parar`.
- **Rádio** — `toca radio` e `para radio` funcionam como pedidos distintos.

---

## Recursos

- Voz Sukuna (Fish Audio) + TTS do aparelho como reserva
- Entendimento de gíria, abreviações, acentos e números por extenso
- WhatsApp: mensagem para contato e lista de transmissão
- Chamadas de voz/vídeo, leitura e resposta de notificações
- Rádio de Minas e música no OiTube em segundo plano
- Lembretes, alarmes, anotações, clima, horóscopo, loterias e notícias
- Mascote flutuante (overlay) e sete temas de aparência
- Aprendizado local: frases e caminhos de tela aprendidos com o uso

---

## Requisitos

- Android 7.0 ou superior
- ~200 MB livres para o APK e o banco de falas
- Permissões concedidas pelo usuário: microfone, notificações e acessibilidade
  (Auto-Bot) para automatizar WhatsApp e mídia
- Internet para voz viva (Fish Audio), clima e pesquisa; o restante funciona offline

---

## Download e instalação

1. Abra a [Release v3.0.4](https://github.com/Dev-JeffersonMF/nexo-app/releases/tag/v3.0.4)
   e baixe `app-release.apk`.
2. Confira o hash em `SHA256SUMS.txt` (ou `docs/VERIFICACAO-APK.md`).
3. Instale no aparelho. Se vinha de uma versão com assinatura diferente,
   desinstale antes.
4. Abra o Nexo e conceda as permissões pedidas, incluindo **Acessibilidade**
   para o Auto-Bot.

> A atualização automática usa o manifesto público
> `https://raw.githubusercontent.com/Dev-JeffersonMF/nexo-update/main/latest.json`.

---

## Privacidade

Conversa, memória neural e banco de falas ficam no aparelho. A síntese de voz
usa a API Fish Audio apenas para gerar texto ainda não aprendido; a chave fica
no `.env` do código-fonte privado e nunca é publicada neste repositório.

---

## Código-fonte

O código-fonte é privado: **https://github.com/Dev-JeffersonMF/Nexo**.
Este repositório contém apenas distribuição, documentação e verificação.

## Licença

Uso pessoal, conforme [LICENSE.md](LICENSE.md).
