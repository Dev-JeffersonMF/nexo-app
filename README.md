<div align="center">

# Nexo

**Assistente pessoal para Android, em português, com voz própria e automação do dia a dia.**

[![Versão](https://img.shields.io/badge/vers%C3%A3o-2.3.0-7C5CFF?style=flat-square)](#versão)
[![Android](https://img.shields.io/badge/Android-7.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white)](#requisitos)
[![Licença](https://img.shields.io/badge/licen%C3%A7a-propriet%C3%A1ria-FF4D6D?style=flat-square)](LICENSE.md)
[![Status](https://img.shields.io/badge/status-em%20evolu%C3%A7%C3%A3o%20cont%C3%ADnua-00C2A8?style=flat-square)](#sempre-melhorando)

[Download](#download-e-instalação) · [Verificar autenticidade](docs/VERIFICACAO-APK.md) · [Erros conhecidos](docs/ERROS-CONHECIDOS.md) · [Melhorias](docs/MELHORIAS.md) · [Licença](LICENSE.md)

</div>

![Tela inicial do Nexo](assets/nexo-home.png)

---

## Índice

- [O que é o Nexo](#o-que-é-o-nexo)
- [Destaques](#destaques)
- [Como funciona](#como-funciona)
- [Recursos](#recursos)
- [Requisitos](#requisitos)
- [Download e instalação](#download-e-instalação)
- [Verificação de autenticidade](#verificação-de-autenticidade)
- [Aviso antipirataria](#aviso-antipirataria)
- [Erros conhecidos](#erros-conhecidos)
- [Sempre melhorando](#sempre-melhorando)
- [Privacidade](#privacidade)
- [Perguntas frequentes](#perguntas-frequentes)
- [Código-fonte e componentes open source](#código-fonte-e-componentes-open-source)
- [Licença](#licença)

---

## O que é o Nexo

O **Nexo** é um assistente pessoal nativo para Android que conversa por **voz e texto em português**, executa tarefas no aparelho e automatiza ações do dia a dia — lembretes, alarmes, chamadas, notificações e o uso do WhatsApp.

Ele foi pensado para funcionar **no seu aparelho**: a voz neural roda offline, a memória e os dados ficam armazenados localmente e não existe conta, login ou painel na nuvem.

| | |
| --- | --- |
| **Versão atual** | 2.3.0 (versionCode 6) |
| **Pacote** | `com.jefferson.nexo` |
| **Plataforma** | Android 7.0+ (ARM 64/32 bits) |
| **Idioma** | Português do Brasil |
| **Tamanho do APK** | ~458 MB (inclui os modelos de voz) |
| **Distribuição** | Somente por este repositório, nas [Releases](../../releases) |

> **Nexo não é afiliado ao WhatsApp, Meta, Google ou a qualquer fabricante de celular.** O uso de automação em aplicativos de terceiros é responsabilidade do usuário.

---

## Destaques

- 🎙️ **Voz própria e offline** — modelo neural clonado a partir de uma amostra de voz, com três níveis de fallback para o assistente nunca ficar mudo.
- 🇧🇷 **Português de verdade** — interpretação de comandos com acentos, gírias, números por extenso e correções de fala.
- 💬 **WhatsApp assistido** — descoberta de grupos, envio para listas de transmissão e respostas, com listas de contatos e grupos ignorados.
- 🫧 **Mascote flutuante** — atalho sempre disponível: toque curto abre o microfone; toque longo ou duplo abre o app; arrastar reposiciona.
- 📞 **Chamadas e notificações** — atender, recusar e anunciar chamadas; leitura e resposta de notificações em segundo plano.
- 🧠 **Memória local** — aprende padrões de comando e mantém o contexto da conversa no próprio aparelho.
- 🔒 **Sem conta e sem nuvem** — voz, contatos e histórico processados localmente.
- ♿ **Acessibilidade com consentimento** — a automação usa o serviço de acessibilidade do Android, ativado manualmente por você.

---

## Como funciona

```
┌──────────────────────────────────────────────────────────────┐
│  Você fala ou digita                                          │
└───────────────────────────┬──────────────────────────────────┘
                            ▼
┌──────────────────────────────────────────────────────────────┐
│  Cérebro do Nexo (JS/TS)                                     │
│  intenção → comando → resposta → memória local               │
└───────────────┬──────────────────────────────┬───────────────┘
                ▼                              ▼
┌──────────────────────────────┐  ┌────────────────────────────┐
│  Núcleo nativo (Kotlin)      │  │  Voz neural (offline)      │
│  acessibilidade, overlay,    │  │  Pocket TTS → Piper →      │
│  chamadas, notificações,     │  │  TTS do Android →          │
│  lembretes e mídia           │  │  sintetizador do sistema    │
└──────────────────────────────┘  └────────────────────────────┘
```

**Fila de voz (fallback automático):**

1. **Pocket TTS** — voz clonada, mais natural, roda offline no aparelho.
2. **Piper pt_BR** — voz neural de reserva, mais leve.
3. **TTS do Android** — voz do sistema, instantânea.
4. **expo-speech** — último recurso, garante que o Nexo responda.

Se um modelo não carregar (memória baixa, arquivo corrompido ou aparelho incompatível), o próximo assume automaticamente. O Nexo **nunca fica mudo**.

---

## Recursos

| Área | O que o Nexo faz |
| --- | --- |
| **Conversa** | Responde perguntas, cálculos, hora, data, curiosidades e conversa informal em português. |
| **Voz** | Fala com voz própria clonada, preserva acentos e permite escolher o motor nos Ajustes. |
| **Mascote** | Overlay flutuante com toque curto (microfone), toque longo/duplo (abrir app) e arrastar com posição salva. |
| **Lembretes** | Cria, lista e cancela lembretes com data/hora e alarme com tela cheia. |
| **Alarmes** | Despertador, alarme e aviso por voz, com repetição e rótulos. |
| **Chamadas** | Atende, recusa, anuncia o contato e aplica regras de guarda de chamadas. |
| **Notificações** | Lê notificações em voz alta e permite responder sem abrir o app. |
| **WhatsApp** | Descobre grupos, envia para listas de transmissão, responde mensagens e respeita contatos/grupos ignorados. |
| **Notas** | Anota, consulta e apaga notas por comando de voz. |
| **Memória** | Aprende padrões de intenção e mantém contexto local entre conversas. |
| **Clima e notícias** | Consulta previsão e manchetes (recursos online opcionais). |
| **Horóscopo e loterias** | Consulta signos e resultados de loteria (recursos online opcionais). |
| **Mídia** | Controla música, volume e rádio; pausa o áudio quando o microfone abre. |
| **Atualizações** | Verifica e instala novas versões assinadas pelo próprio Nexo. |
| **Acessibilidade** | Executa automações no aparelho somente com o serviço ativado por você. |

> Recursos que dependem de internet (clima, notícias, horóscopo, loterias e busca) ficam indisponíveis offline; o restante continua funcionando.

---

## Requisitos

- **Android 7.0 (API 24) ou superior.**
- **ARM**: `arm64-v8a` ou `armeabi-v7a`. Emuladores x86 não são suportados.
- **Espaço livre**: ~700 MB (458 MB do APK + ~190 MB dos modelos copiados no primeiro uso).
- **Memória**: 3 GB de RAM ou mais para a voz Pocket TTS; com menos, o Nexo cai automaticamente para Piper ou TTS do sistema.
- Permissões concedidas manualmente: microfone, contatos, telefone, notificações, acessibilidade, sobreposição de tela e bateria sem restrições.

---

## Download e instalação

1. Abra a página de **[Releases](../../releases)** e baixe o `app-release.apk` da versão mais recente.
2. Confira o arquivo com o `SHA256SUMS.txt` da mesma Release — veja [como verificar](docs/VERIFICACAO-APK.md).
3. No celular, permita **“Instalar apps desconhecidos”** para o navegador ou gerenciador de arquivos usado.
4. Instale e abra o Nexo.
5. Siga o guia de permissões do app. A **Acessibilidade** e a **sobreposição de tela** são essenciais para o mascote e para o WhatsApp.
6. Em fabricantes agressivos (Xiaomi, Samsung, Motorola, Oppo), libere o Nexo de otimização de bateria para o mascote continuar ativo em segundo plano.

> O APK é grande porque carrega os modelos de voz. A primeira fala pode demorar alguns segundos enquanto o modelo é copiado para o armazenamento interno.

**Requisitos de instalação:** o pacote é `com.jefferson.nexo`. Versões antigas com outro pacote instalam como um app separado.

---

## Verificação de autenticidade

Toda versão oficial é assinada com o certificado do Nexo. Antes de instalar, confira:

| Item | Valor oficial |
| --- | --- |
| Pacote | `com.jefferson.nexo` |
| Versão | `2.3.0` (versionCode `6`) |
| SHA-256 do APK | `4a14663707dbd4d9dfff404bbc26cca85fbf962f72ea4416a06184628b03ed66` |
| SHA-256 do certificado de assinatura | `30405b638e6ffa9dfb9f05a72d59896957777a9ffd4903d1f02bd53cd42c95a9` |
| SHA-1 do certificado | `6afb7a0f24fe23f9fd31ffbe1b5bae613a54fa1d` |
| Emissor do certificado | `CN=NEXO, OU=Android, O=NEXO, L=Matozinhos, ST=MG, C=BR` |

**Regra simples:** se o hash ou a assinatura não baterem, **não é o Nexo oficial**. Não instale.

O passo a passo completo (Windows, Linux, macOS e Android) está em **[docs/VERIFICACAO-APK.md](docs/VERIFICACAO-APK.md)**.

---

## Aviso antipirataria

O Nexo é um **software proprietário**. Este repositório é o **único canal oficial de distribuição**.

❌ **Não é permitido**, sem autorização escrita do autor:

- redistribuir, espelhar, vender, alugar ou sublicenciar o APK;
- publicar versões modificadas, repackaged, “premium desbloqueado”, “mod” ou com anúncios inseridos;
- remover ou alterar avisos de copyright, assinatura, nome ou identificação do app;
- usar o nome, a marca, o mascote ou a identidade visual do Nexo em produtos derivados;
- contornar mecanismos de verificação de integridade ou de atualização.

⚠️ **Cópias não oficiais não são suportadas** e podem conter malware, roubo de dados ou cobranças indevidas. O autor **não se responsabiliza** por APKs obtidos fora deste repositório.

Se você encontrar o Nexo sendo vendido ou distribuído irregularmente, abra uma issue ou entre em contato de forma privada (veja [SECURITY.md](SECURITY.md)).

A íntegra das regras está em **[LICENSE.md](LICENSE.md)**.

---

## Erros conhecidos

Transparência total: estes são os problemas conhecidos da versão **2.3.0**, com causa e contorno. A lista detalhada fica em **[docs/ERROS-CONHECIDOS.md](docs/ERROS-CONHECIDOS.md)**.

| # | Sintoma | Causa | Contorno |
| --- | --- | --- | --- |
| 1 | APK de ~458 MB e instalação demorada | Modelos de voz embutidos | É intencional; a voz precisa ser offline. A redução está no roadmap. |
| 2 | Primeira fala demora | Cópia de ~190 MB para `filesDir` no primeiro uso | Aguarde a primeira resposta; as seguintes são rápidas. |
| 3 | Voz sai “robótica” | Pocket TTS não carregou (RAM/ABI) e caiu para o TTS do Android | Feche apps em segundo plano e tente de novo; verifique `npm run piper:check` no build. |
| 4 | Mascote não aparece | Sobreposição de tela negada ou serviço morto pelo fabricante | Conceda “Exibir sobre outros apps” e retire o Nexo da otimização de bateria. |
| 5 | Acessibilidade desliga sozinha | Alguns fabricantes encerram o serviço após reinício | Reative em Configurações → Acessibilidade → Nexo. |
| 6 | Grupos/lista de transmissão param de funcionar | O WhatsApp mudou IDs ou layout | Aguarde atualização do Nexo; os fluxos são recalibrados por versão do WhatsApp. |
| 7 | Play Protect bloqueia a instalação | APK fora da Play Store | Confirme o hash oficial e escolha “Instalar mesmo assim”. |
| 8 | Nexo para em segundo plano | Otimização de bateria do Android | Permita atividade em segundo plano e desative a otimização para o Nexo. |
| 9 | “Palavra de ativação” não responde | Recurso desligado por padrão | Ative nas configurações, se disponível na sua versão. |
| 10 | Rádio/música instável | Recurso pouco testado nesta versão | Prefira os controles nativos de mídia; melhorias previstas. |
| 11 | Não instala em emulador | APK só tem bibliotecas ARM | Use um aparelho físico ARM. |
| 12 | Comandos de WhatsApp não executam | Acessibilidade desligada ou WhatsApp não aberto | Ative o serviço e mantenha o WhatsApp atualizado. |

---

## Sempre melhorando

O Nexo é um projeto **vivo**. Cada versão corrige problemas reais encontrados em uso e prepara a próxima melhoria. O histórico completo está em **[CHANGELOG.md](CHANGELOG.md)** e o plano em **[docs/MELHORIAS.md](docs/MELHORIAS.md)**.

### O que melhorou na 2.3.0

- Voz própria clonada (Pocket TTS) com fallback Piper → Android TTS → expo-speech.
- Carregamento preguiçoso da voz neural: fim dos fechamentos inesperados na inicialização.
- Correção do chip **Grupos** do WhatsApp (4º chip, com espera de confirmação).
- Fluxo completo de **lista de transmissão** (menu → listas → conversa → envio → confirmação).
- Mascote estável: toque curto, toque longo, duplo toque e arraste com posição salva.
- Serviço em primeiro plano seguro, com recuperação após morte do processo.
- Build release assinado, com regras de ProGuard para WorkManager, Room e sherpa-onnx.
- 26 testes automatizados, `typecheck` e `lint` sem erros.

### Próximos passos

- 📦 **APK menor**: baixar pacotes de voz sob demanda, mantendo o núcleo leve.
- 🔐 **Verificação de assinatura dentro do app**, bloqueando builds repackaged.
- 🎧 **Rádio e música** mais estáveis e testados.
- 🗣️ **Palavra de ativação** (“Nexo”) opcional e com baixo consumo.
- ☁️ **Backup/exportação** de memória, notas e listas de ignorados.
- 🧪 **Testes em mais aparelhos e versões do Android**, com relatório público de compatibilidade.
- 🌎 **Mais idiomas** e sotaques.
- 📊 **Telemetria opcional e anônima** de latência de voz (desligada por padrão).

> Encontrou um erro? Abra uma issue com modelo do aparelho, versão do Android e o passo a passo. É assim que o Nexo melhora.

---

## Privacidade

- **Sem conta, sem login, sem anúncios.**
- **Voz offline**: o áudio da síntese não sai do aparelho.
- **Dados locais**: contatos, notas, memória, histórico e listas de ignorados ficam no armazenamento do app.
- **Sem venda de dados.**
- **Internet apenas quando necessário**: clima, notícias, horóscopo, loterias, busca e atualização.
- **Acessibilidade**: usada para executar as automações que você solicita; o conteúdo das telas é processado no aparelho.

Detalhes em **[docs/PRIVACIDADE.md](docs/PRIVACIDADE.md)**.

---

## Perguntas frequentes

**O Nexo é gratuito?**
A distribuição oficial é feita por este repositório. Consulte a [licença](LICENSE.md) para as condições de uso.

**Por que o APK é tão grande?**
Porque leva os modelos de voz neurais (Pocket TTS + Piper). Isso permite voz offline e privada. A redução está no roadmap.

**Funciona sem internet?**
A conversa, os comandos, os lembretes e a voz funcionam offline. Clima, notícias, horóscopo, loterias e busca precisam de conexão.

**Preciso de root?**
Não. O Nexo usa recursos oficiais do Android (acessibilidade, sobreposição e serviços em primeiro plano).

**O Nexo pode ser banido no WhatsApp?**
Automação não oficial pode contrariar os termos do WhatsApp. O Nexo atua como uma camada de acessibilidade, mas o risco e a responsabilidade são do usuário. Use com moderação.

**Por que o código-fonte não está aqui?**
O código é privado para proteger a propriedade intelectual e evitar cópias alteradas. Este repositório público concentra documentação, licença, verificação e o APK oficial. Componentes de terceiros são open source e estão creditados abaixo.

**Como sei que o APK é oficial?**
Confira o SHA-256 e a assinatura em [docs/VERIFICACAO-APK.md](docs/VERIFICACAO-APK.md). Se não bater, não instale.

---

## Código-fonte e componentes open source

Este repositório **não distribui o código-fonte do Nexo**. Ele publica a documentação e o APK oficial.

O Nexo é construído sobre projetos open source, respeitando suas licenças:

- [React Native](https://reactnative.dev/) e [Expo](https://expo.dev/) — MIT
- [Kotlin](https://kotlinlang.org/) e [AndroidX](https://developer.android.com/jetpack/androidx) — Apache-2.0
- [sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) — Apache-2.0
- [Piper](https://github.com/rhasspy/piper) — MIT
- [lucide-react-native](https://lucide.dev/) — ISC
- [react-native-svg](https://github.com/software-mansion/react-native-svg) — MIT

Marcas e nomes citados pertencem aos seus respectivos donos.

---

## Licença

**Proprietário — todos os direitos reservados.** O uso é concedido em caráter pessoal e não exclusivo, nos termos de **[LICENSE.md](LICENSE.md)**. Redistribuição, revenda e versões modificadas são proibidas.

© 2026 Jefferson M. F. — Nexo. Todos os direitos reservados.

---

<div align="center">

**Nexo — feito para entender você, no seu aparelho.**

[⬆ Voltar ao topo](#nexo)

</div>
