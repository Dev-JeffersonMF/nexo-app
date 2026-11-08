# Nexo 2.3.0 — voz própria, WhatsApp e estabilidade

Primeira versão pública do Nexo. Assistente pessoal Android em português, com voz neural offline e automação do dia a dia.

## Destaques

- 🎙️ **Voz própria clonada** (Pocket TTS, offline) com fallback Piper → TTS Android → expo-speech.
- 💬 **WhatsApp**: descoberta de grupos corrigida e fluxo completo de lista de transmissão.
- 🫧 **Mascote estável**: toque curto, toque longo/duplo, arraste com posição salva.
- 🔋 **Segundo plano confiável**: serviço em primeiro plano seguro e recuperação após morte do processo.
- ✅ **26 testes**, typecheck e lint sem erros.

## Arquivo

| Item | Valor |
| --- | --- |
| APK | `app-release.apk` |
| Tamanho | 480.085.944 bytes (~458 MiB) |
| Pacote | `com.jefferson.nexo` |
| Versão | 2.3.0 (6) |
| Android | 7.0+ (ARM) |
| SHA-256 | `4a14663707dbd4d9dfff404bbc26cca85fbf962f72ea4416a06184628b03ed66` |

## Instalação

1. Baixe o `app-release.apk` e o `SHA256SUMS.txt`.
2. Confira o SHA-256 ([guia](../docs/VERIFICACAO-APK.md)).
3. Permita “Instalar apps desconhecidos” e instale.
4. Conceda acessibilidade, sobreposição e bateria sem restrições.

## Aviso

Distribuição oficial **somente** neste repositório. É proibido redistribuir, vender ou modificar o APK. Cópias não oficiais não são suportadas e podem conter malware. Leia a [licença](../LICENSE.md).

## Erros conhecidos

APK grande, primeira fala lenta e dependência do layout do WhatsApp. Lista completa em [docs/ERROS-CONHECIDOS.md](../docs/ERROS-CONHECIDOS.md).

**O Nexo está sempre melhorando.** Encontrou um problema? Abra uma issue com aparelho, versão do Android e passos para reproduzir.
