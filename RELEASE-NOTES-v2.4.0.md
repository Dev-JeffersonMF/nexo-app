# Nexo 2.4.0 — atualização automática e contatos redesenhados

Esta versão fecha o ciclo de atualização do Nexo: ele procura a versão nova, baixa, confere a assinatura e instala. Depois de reiniciar, uma tela de novidades aparece **uma única vez**, até você tocar em **Confirmado**.

## Destaques

- **Atualização automática de verdade**: verificação silenciosa ao abrir e diariamente em segundo plano (JobScheduler), download pelo sistema e conferência completa antes de instalar.
- **Download sempre completo**: se o APK falhar ou for corrompido, o arquivo anterior é apagado e o download recomeça do zero.
- **Conferência de segurança**: SHA-256, tamanho, pacote, `versionCode` e assinatura digital precisam bater com o manifesto e com o Nexo instalado.
- **Tela "Confirmado"**: mostra o que mudou e aparece só uma vez por atualização; o app reabre sozinho depois de instalar.
- **Aba de contatos redesenhada**: cartão de resumo, contadores, busca, estado por pessoa e bloqueio de chamada em um toque.
- **Grupos do WhatsApp**: a leitura fica na aba Conversas, toca no **4º filtro "Grupos"** e marca todos os grupos como ignorados. Tocar em um grupo reativa as mensagens dele.
- **Nunca troca de aba no WhatsApp**: sem Atualizações, Comunidades ou Ligações.

## Correções

- Nomes de grupo passam a vir de `conversations_row_contact_name`, sem prévias de mensagem ou cabeçalhos de comunidade.
- Se o filtro "Grupos" não abrir, a leitura termina com erro claro em vez de importar conversas individuais.
- Removido o aviso antigo de atualização, que duplicava a interface.

## Arquivo

| Item | Valor |
| --- | --- |
| APK | `app-release.apk` |
| Tamanho | 480.123.084 bytes (~458 MiB) |
| Pacote | `com.jefferson.nexo` |
| Versão | 2.4.0 (7) |
| Android | 7.0+ (ARM) |
| SHA-256 | `57e021e9a294db9f294b8e95142f1e021fae2d0bce4a5049499015f566ecbf66` |
| Certificado SHA-256 | `30405b638e6ffa9dfb9f05a72d59896957777a9ffd4903d1f02bd53cd42c95a9` |

## Instalação

1. Baixe o `app-release.apk` e o `SHA256SUMS.txt`.
2. Confira o SHA-256 ([guia de verificação](https://github.com/Dev-JeffersonMF/nexo-app/blob/main/docs/VERIFICACAO-APK.md)).
3. Permita "Instalar apps desconhecidos" e instale.
4. Conceda acessibilidade, sobreposição e bateria sem restrições.

## Atualização automática

O app consulta `latest.json` neste repositório público:

```
https://raw.githubusercontent.com/Dev-JeffersonMF/nexo-app/main/latest.json
```

O manifesto aponta para o APK da release, com SHA-256 e tamanho. A instalação final sempre passa pela confirmação do Android — o sistema não permite instalar em silêncio.
