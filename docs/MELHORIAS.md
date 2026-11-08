# Melhorias e roadmap

O Nexo é um projeto em **evolução contínua**. Esta página registra o que já melhorou e o que vem a seguir.

---

## Já entregue

### 2.3.0 — estabilidade e voz própria

| Área | Melhoria |
| --- | --- |
| Voz | Pocket TTS clonado, offline, com Piper de reserva. |
| Estabilidade | Carregamento sob demanda elimina fechamentos na abertura. |
| WhatsApp | Chip “Grupos” corrigido e fluxo de lista de transmissão completo. |
| Mascote | Toque curto, longo, duplo e arraste, com posição salva. |
| Segundo plano | Serviço em primeiro plano seguro, com recuperação após morte do processo. |
| Build | Release assinado, ProGuard ajustado, assets sem compressão. |
| Qualidade | 26 testes, typecheck e lint sem erros. |

### 1.1.0 — recursos de assistente

| Área | Melhoria |
| --- | --- |
| Voz | Palavra de ativação e microfone compartilhado. |
| WhatsApp | Envio para listas de transmissão. |
| Áudio | Gravação de áudio. |
| Segundo plano | Atualização nativa e leitura de notificações. |

### 1.0.0 — base

Conversa por voz/texto, lembretes, alarmes, chamadas, notificações, mascote e acessibilidade.

---

## Em andamento

| Prioridade | Item | Status |
| --- | --- | --- |
| Alta | Reduzir o tamanho do APK com pacotes de voz sob demanda | Planejado |
| Alta | Recalibrar os fluxos do WhatsApp para novas versões | Contínuo |
| Alta | Testes em mais aparelhos e versões do Android | Contínuo |
| Média | Verificação de assinatura dentro do app | Planejado |
| Média | Estabilizar rádio e música | Planejado |
| Média | Backup/exportação de memória, notas e listas | Planejado |
| Baixa | Palavra de ativação com baixo consumo | Em avaliação |
| Baixa | Mais idiomas e sotaques | Em avaliação |

---

## Próximas versões (visão)

### 2.4 — leveza e confiança
- Núcleo leve + download opcional dos modelos de voz.
- Verificação de integridade/assinatura em tempo de execução.
- Mensagens de erro mais claras para falhas de voz e acessibilidade.
- Melhor diagnóstico em **Ajustes → Voz**.

### 2.5 — automação mais robusta
- Seletores do WhatsApp com múltiplos fallbacks e autorrecuperação.
- Suporte a novas telas e fluxos do WhatsApp.
- Confirmação visual das ações concluídas.

### 3.0 — assistente completo
- Palavra de ativação estável e econômica.
- Rotinas (“modo carro”, “boa noite”, “trabalho”).
- Backup criptografado e restauração.
- Relatório público de compatibilidade por aparelho.

---

## Como as melhorias são priorizadas

1. **Segurança e privacidade** — sempre primeiro.
2. **Estabilidade** — o app não pode travar nem ficar mudo.
3. **Correções que afetam o uso diário** — voz, lembretes, WhatsApp.
4. **Redução de tamanho e consumo**.
5. **Recursos novos**.

---

## Compromisso de evolução

- Toda versão publicada tem **changelog** e **hash oficial**.
- Erros conhecidos são documentados abertamente em [ERROS-CONHECIDOS.md](ERROS-CONHECIDOS.md).
- Relatos da comunidade entram na fila de correções.
- Nenhuma versão é publicada sem conferência de assinatura e testes básicos.

> **O Nexo está sempre melhorando.** Se algo não funciona como deveria, isso é um item de roadmap — e você pode ajudar a priorizá-lo abrindo uma issue.
