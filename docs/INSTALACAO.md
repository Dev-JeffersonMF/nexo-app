# Instalação passo a passo

## Antes de começar

- **Android 7.0+** em aparelho **ARM** (`arm64-v8a` ou `armeabi-v7a`).
- **~700 MB livres** (458 MB do APK + ~190 MB de modelos copiados no primeiro uso).
- **3 GB de RAM** recomendados para a voz Pocket TTS.
- Bateria acima de 30% (a instalação e a primeira cópia dos modelos consomem energia).

---

## 1. Baixar o APK oficial

1. Acesse **[Releases](../../releases)**.
2. Baixe o `app-release.apk` da versão mais recente.
3. Baixe também o `SHA256SUMS.txt`.
4. Confira o hash em [VERIFICACAO-APK.md](VERIFICACAO-APK.md). **Não pule esta etapa.**

---

## 2. Permitir instalação de apps desconhecidos

O caminho varia por fabricante, mas em geral:

**Android 12+**

- Configurações → Apps → **Acesso especial a apps** → **Instalar apps desconhecidos**.
- Escolha o app que fará a instalação (Chrome, Drive, Gerenciador de arquivos) e permita.

**Android 8–11**

- Configurações → Segurança → **Instalar apps desconhecidos**.
- Selecione o app de origem e permita.

Se o Play Protect exibir alerta, escolha **“Instalar mesmo assim”** — desde que o hash confira.

---

## 3. Instalar

1. Abra o APK baixado.
2. Toque em **Instalar**.
3. Aguarde. Como o APK é grande, a instalação pode levar alguns minutos.
4. Toque em **Abrir**.

---

## 4. Primeira configuração

O Nexo guia você pelas permissões. Conceda com atenção:

| Permissão | Para quê |
| --- | --- |
| **Microfone** | Conversa por voz e palavra de ativação. |
| **Contatos** | Identificar quem está chamando ou enviando mensagens. |
| **Telefone** | Atender, recusar e anunciar chamadas. |
| **Notificações** | Avisos, lembretes e leitura de notificações. |
| **Acessibilidade** | Executar automações (WhatsApp, telas e respostas). |
| **Sobrepor outros apps** | Exibir o mascote flutuante. |
| **Bateria sem restrições** | Manter o mascote e o assistente ativos em segundo plano. |

### Ativar acessibilidade

Configurações → **Acessibilidade** → **Apps instalados** → **Nexo** → ativar.
Confirme o aviso do Android. Sem isso, os comandos de WhatsApp e automação não funcionam.

### Ativar sobreposição

Configurações → **Apps** → **Nexo** → **Exibir sobre outros apps** → permitir.
Sem isso, o mascote não aparece fora do app.

### Liberar a bateria

Configurações → **Apps** → **Nexo** → **Bateria** → **Sem restrições**.

Em Xiaomi/Redmi (MIUI/HyperOS), ative também **Autostart**.
Em Samsung, remova o Nexo da lista de “apps em suspensão”.
Em Oppo/Realme, permita **atividade em segundo plano**.

---

## 5. Primeira fala

Na primeira vez que o Nexo falar, ele copia os modelos de voz (~190 MB) para o armazenamento interno. Isso pode levar **10–30 segundos** dependendo do aparelho. É normal.

Se o aparelho tiver pouca memória, o Nexo pode usar a voz Piper ou a voz do Android automaticamente. Você pode conferir o motor em uso nos **Ajustes → Voz do Nexo**.

---

## 6. Atualizar

- O Nexo verifica atualizações assinadas e oferece a instalação.
- Também é possível baixar manualmente a Release mais recente e instalar por cima; os dados são preservados.
- **Nunca** instale uma atualização de origem desconhecida. Confira a assinatura.

---

## Solução de problemas de instalação

| Erro | Solução |
| --- | --- |
| “App não instalado” | Desinstale uma versão com assinatura diferente e instale a oficial. |
| “Pacote inválido” | Download corrompido; baixe novamente e confira o hash. |
| “Sem espaço” | Libere ~1 GB e tente de novo. |
| Play Protect bloqueia | Confirme o hash e escolha “Instalar mesmo assim”. |
| Instala mas não abre | Verifique se o aparelho é ARM e Android 7+. |
| Mascote não aparece | Ative “Exibir sobre outros apps” e libere a bateria. |
| Comandos de WhatsApp não funcionam | Ative a Acessibilidade e mantenha o WhatsApp atualizado. |
