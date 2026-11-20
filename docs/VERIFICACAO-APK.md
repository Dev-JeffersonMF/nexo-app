# Verificação de autenticidade do APK

Este guia mostra como confirmar que o APK do Nexo é **oficial**, antes de instalar.

## Dados oficiais — versão 3.0.5

| Item | Valor |
| --- | --- |
| Arquivo | `app-release.apk` |
| Tamanho | 134.994.699 bytes (~129 MiB) |
| Pacote | `com.jefferson.nexo` |
| Versão | `3.0.5` (versionCode `35`) |
| SHA-256 do APK | `6b78a762e17dd36f0bd2680a8979f3510ae7021d6e538392c491446d16c77070` |
| SHA-256 do certificado | `3942b0409a933c87d86c8bdf437601f30ae38b6cc1efc2d8043e140e7db76aff` |
| SHA-1 do certificado | `fe77d8477eebe9c12434f55ed325a4da9d0c2505` |
| Emissor | `CN=Jefferson, OU=Nexo, O=Nexo, C=BR` |

O arquivo **`SHA256SUMS.txt`** da Release repete o hash do APK. Ele é a referência de conferência.

> Se o hash ou a assinatura não baterem, **pare**: não é o Nexo oficial.

---

## 1. Conferir o SHA-256 do arquivo

### Windows (PowerShell)

```powershell
Get-FileHash .\app-release.apk -Algorithm SHA256
```

ou

```cmd
certutil -hashfile app-release.apk SHA256
```

### Linux

```bash
sha256sum app-release.apk
```

### macOS

```bash
shasum -a 256 app-release.apk
```

O resultado deve ser exatamente:

```
6b78a762e17dd36f0bd2680a8979f3510ae7021d6e538392c491446d16c77070
```

Se você baixou o `SHA256SUMS.txt` junto, pode validar automaticamente:

```bash
# Linux
sha256sum -c SHA256SUMS.txt

# macOS
shasum -a 256 -c SHA256SUMS.txt
```

No Windows, compare o hash exibido com a linha do `SHA256SUMS.txt`.

---

## 2. Conferir a assinatura do APK

A assinatura prova quem compilou o app. O Nexo usa sempre o mesmo certificado.

### Opção A — Android SDK (`apksigner`)

```bash
apksigner verify --print-certs app-release.apk
```

Procure a linha:

```
Signer #1 certificate SHA-256 digest: 30405b638e6ffa9dfb9f05a72d59896957777a9ffd4903d1f02bd53cd42c95a9
```

### Opção B — `keytool` (Java)

```bash
keytool -printcert -jarfile app-release.apk
```

Compare o campo **SHA256** com o valor oficial.

### Opção C — aplicativos de verificação

Apps como *APK Signature Check* ou *AppChecker* mostram o hash do certificado. O valor deve ser o mesmo. Prefira ferramentas open source e confira o código-fonte delas.

---

## 3. Conferir pacote e versão

### Com o APK em mãos (`aapt2`)

```bash
aapt2 dump badging app-release.apk | findstr "package:"
```

Resultado esperado:

```
package: name='com.jefferson.nexo' versionCode='30' versionName='3.0.5'
```

### No aparelho, após instalar

```bash
adb shell dumpsys package com.jefferson.nexo | findstr versionName
```

ou em **Configurações → Apps → Nexo → Informações**.

---

## 4. Sinais de que o APK NÃO é oficial

- package diferente de `com.jefferson.nexo`;
- hash SHA-256 diferente do publicado;
- assinatura com outro certificado (mesmo mantendo o mesmo pacote);
- APK muito menor (por exemplo, 40 MB) — pode ter sido recompilado sem os modelos;
- nome como “Nexo Premium”, “Nexo Mod”, “Nexo Desbloqueado”, “Nexo VIP”;
- pedido de pagamento, login ou dados bancários;
- origem: grupos de WhatsApp/Telegram, sites de download, lojas alternativas.

Nesses casos, **não instale** e denuncie conforme [SECURITY.md](../SECURITY.md).

---

## 5. Por que isso importa

Um APK modificado pode:

- ler notificações e mensagens;
- capturar o microfone;
- acessar contatos e chamadas;
- instalar outros aplicativos;
- roubar contas e senhas.

Como o Nexo pede permissões poderosas (acessibilidade, sobreposição, notificações e microfone), **confiar na origem é essencial**. Só instale o arquivo cujo hash e assinatura conferem.
