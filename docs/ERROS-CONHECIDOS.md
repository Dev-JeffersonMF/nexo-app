# Erros conhecidos — versão 2.3.0

Transparência é parte do projeto. Esta é a lista de problemas conhecidos, com causa, impacto e contorno.

**Legenda de status:** 🟢 contornável · 🟡 limitação da versão · 🔴 depende de terceiros

---

## 1. 🟡 APK muito grande (~458 MB)

**Sintoma:** download e instalação demoram; pouco espaço livre exigido.
**Causa:** os modelos de voz Pocket TTS (~190 MB) e Piper (~77 MB) vão embutidos, além das bibliotecas nativas ARM.
**Contorno:** é intencional para ter voz offline e privada. A versão com pacotes de voz sob demanda está no roadmap.

## 2. 🟢 Primeira fala demora

**Sintoma:** o assistente demora 10–30 s para falar pela primeira vez.
**Causa:** cópia dos modelos para `filesDir/nexo-voice/` no primeiro uso.
**Contorno:** aguarde. As falas seguintes são rápidas. Não feche o app durante a cópia.

## 3. 🟢 Voz sai robótica

**Sintoma:** a voz é a do sistema Android, não a clonada.
**Causa:** Pocket TTS não carregou (RAM insuficiente, ABI incompatível ou arquivo corrompido) e o fallback assumiu.
**Contorno:** feche apps em segundo plano, reinicie o aparelho e tente novamente. Confira o motor ativo em **Ajustes → Voz do Nexo**.

## 4. 🟢 Mascote não aparece

**Sintoma:** o mascote flutuante some ou não abre fora do app.
**Causa:** permissão “Exibir sobre outros apps” negada ou serviço encerrado pelo fabricante.
**Contorno:** conceda a sobreposição e retire o Nexo da otimização de bateria. Em MIUI/HyperOS, ative Autostart.

## 5. 🟢 Acessibilidade desliga sozinha

**Sintoma:** automações param após reiniciar o aparelho.
**Causa:** alguns fabricantes encerram serviços de acessibilidade após atualização ou reinício.
**Contorno:** reative em Configurações → Acessibilidade → Nexo. Verifique após cada atualização do Android.

## 6. 🔴 WhatsApp muda e o fluxo quebra

**Sintoma:** descoberta de grupos ou envio para lista de transmissão falham.
**Causa:** o WhatsApp altera `resource-id`, layout ou `content-desc` entre versões.
**Contorno:** mantenha o WhatsApp na versão validada ou aguarde atualização do Nexo. Cada nova versão do WhatsApp exige recalibração dos seletores.

## 7. 🟢 Play Protect bloqueia a instalação

**Sintoma:** aviso de app desconhecido ou “instalação bloqueada”.
**Causa:** APK distribuído fora da Play Store.
**Contorno:** confira o hash oficial e escolha “Instalar mesmo assim”.

## 8. 🟢 Nexo para em segundo plano

**Sintoma:** mascote e assistente param de responder com o app fechado.
**Causa:** otimização de bateria do Android.
**Contorno:** Bateria → Sem restrições; permita atividade em segundo plano; bloqueie a “suspensão” do app.

## 9. 🟡 Palavra de ativação não responde

**Sintoma:** dizer “Nexo” não acorda o assistente.
**Causa:** recurso desligado por padrão para economizar bateria.
**Contorno:** ative nas configurações, se disponível. O consumo aumenta com o recurso ligado.

## 10. 🟡 Rádio e música instáveis

**Sintoma:** streaming para, ou o controle de mídia falha em alguns aparelhos.
**Causa:** recurso pouco testado nesta versão e dependente de APIs de mídia do fabricante.
**Contorno:** use os controles nativos de mídia. Melhorias previstas.

## 11. 🟢 Não instala em emulador x86

**Sintoma:** “app não instalado” em emuladores.
**Causa:** o APK contém apenas bibliotecas ARM.
**Contorno:** teste em aparelho físico ARM. Suporte a x86 não está previsto.

## 12. 🟢 Comandos de WhatsApp não executam

**Sintoma:** pedir para enviar mensagem não faz nada.
**Causa:** acessibilidade desligada, WhatsApp não instalado/atualizado ou tela bloqueada.
**Contorno:** ative a acessibilidade, desbloqueie o aparelho e mantenha o WhatsApp atualizado.

## 13. 🟡 Avisos de bateria em primeiro plano

**Sintoma:** notificação persistente do Nexo.
**Causa:** serviços em primeiro plano são obrigatórios no Android moderno para manter microfone/mascote ativos.
**Contorno:** é esperado. A notificação pode ser minimizada, mas não removida enquanto o serviço estiver ativo.

## 14. 🟡 Instalação por cima de versão antiga

**Sintoma:** “app não instalado” ao atualizar.
**Causa:** assinatura ou pacote diferente de uma versão antiga.
**Contorno:** desinstale a versão antiga (exporte o que precisar) e instale a oficial. Dados de versões com outra assinatura não são migrados.

## 15. 🟡 Consumo de memória da voz neural

**Sintoma:** lentidão em aparelhos com 2–3 GB de RAM.
**Causa:** modelos neurais são pesados.
**Contorno:** o Nexo cai automaticamente para Piper ou TTS do sistema. Feche outros apps.

---

## Como reportar um novo erro

Abra uma issue com:

1. Versão do Nexo (Ajustes → Sobre).
2. Modelo do aparelho e versão do Android.
3. Versão do WhatsApp (se aplicável).
4. Passos para reproduzir.
5. O que era esperado e o que aconteceu.
6. Captura de tela ou log, **sem dados pessoais**.

Relatos detalhados entram na próxima rodada de correções.
