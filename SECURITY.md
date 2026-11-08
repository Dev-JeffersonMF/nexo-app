# Segurança e denúncias

## Reportar uma vulnerabilidade

Se você encontrou uma falha de segurança no Nexo, **não abra uma issue pública**. Entre em contato de forma privada pelo e-mail do mantenedor indicado no perfil do GitHub ([@Dev-JeffersonMF](https://github.com/Dev-JeffersonMF)) ou por mensagem direta.

Inclua, se possível:

- versão do Nexo e do Android;
- modelo do aparelho;
- passos para reproduzir;
- impacto estimado;
- evidências (logs, capturas) sem dados pessoais.

Você receberá um retorno em até **7 dias úteis**. Vulnerabilidades confirmadas serão corrigidas na próxima versão, com crédito ao reporter se desejado.

## Reportar pirataria ou cópia não oficial

O Nexo é distribuído **exclusivamente** em:

> https://github.com/Dev-JeffersonMF/nexo-app

Se você encontrar:

- APK do Nexo sendo vendido ou redistribuído;
- versões “mod”, “premium desbloqueado” ou com anúncios inseridos;
- uso indevido do nome, mascote ou identidade visual;
- sites, grupos ou lojas oferecendo o app fora do canal oficial;

envie o link e, se possível, uma captura de tela. Denúncias são tratadas com confidencialidade.

## Verificação rápida

Antes de instalar qualquer APK do Nexo, confira:

1. Pacote `com.jefferson.nexo`.
2. SHA-256 igual ao publicado em `SHA256SUMS.txt` na Release oficial.
3. Assinatura com o certificado:
   - SHA-256: `30405b638e6ffa9dfb9f05a72d59896957777a9ffd4903d1f02bd53cd42c95a9`
   - SHA-1: `6afb7a0f24fe23f9fd31ffbe1b5bae613a54fa1d`

Passo a passo em [VERIFICACAO-APK.md](docs/VERIFICACAO-APK.md).

> **APK não oficial é APK desconhecido.** Pode conter spyware, roubo de credenciais ou cobrança indevida. Não instale.
