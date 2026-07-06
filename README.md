# AI Skill for R Stats

Uma skill (system prompt) para agentes de IA especializados em R e estatística aplicada. O objetivo central é ser model agnostic: qualquer LLM, incluindo modelos locais pequenos sem treinamento prévio em R, deve conseguir seguir as instruções e produzir código correto.

## Arquivo principal

`r-stats-skill.md` é o único artefato do projeto. Ele pode ser usado como system prompt completo em qualquer LLM (Claude, GPT, Gemini, Llama, Mistral, etc.) ou carregado como skill/comando em ferramentas como o Claude Code.

## Para que serve

O agente definido nesse arquivo ajuda a:

- Escrever e depurar código R para análise estatística
- Aplicar métodos estatísticos corretamente (EDA, inferência, regressão, ANOVA)
- Usar pacotes como base R, tidyverse, ggplot2, MASS e car
- Interpretar a saída de funções estatísticas do R
- Explicar conceitos de estatística aplicada em nível introdutório/intermediário

## Foco prioritário

t test, teste qui quadrado, regressão linear, ANOVA e plotagem de gráficos (base R e ggplot2).

## Estrutura da skill

A skill tem 25 seções, organizadas em blocos:

1. Identidade e regras de estilo de código
2. Fundamentos da linguagem R (vetores, estruturas de dados, controle de fluxo, strings, apply)
3. Importação e exportação de dados
4. Análise exploratória e estatística descritiva
5. Distribuições de probabilidade
6. Testes de hipótese (t test, qui quadrado, normalidade, não paramétricos, tamanhos de efeito)
7. ANOVA (one way, two way, post hoc, eta squared e omega squared)
8. Regressão linear (simples, múltipla, diagnósticos, pontos de influência)
9. Visualização com ggplot2 e base R
10. Pacotes comuns, workflow padrão e árvore de decisão de suposições
11. Valores críticos de referência e erros comuns a evitar
12. Interpretação de output e dicas de RStudio
13. Séries temporais
14. Exemplos funcionais completos, usando datasets embutidos do R (mtcars, faithful, iris)
15. Regras de comportamento do agente

As seções de fundamentos de R foram incluídas especificamente para cobrir lacunas de modelos de linguagem pequenos, sem conhecimento prévio consolidado da linguagem (indexação baseada em 1, reciclagem de vetores, diferença entre `&` e `&&`, diferença entre `[` e `[[`, escopo léxico).

## Regras de estilo aplicadas ao código gerado

- Atribuição com `<-`, não `=`
- Nomes de variáveis e funções em snake_case
- Blocos de código sempre identificados com a linguagem `r`
- Comentários apenas quando o motivo não é óbvio
- Tratamento explícito de valores ausentes (`na.rm = TRUE`)
- Suporte ao formato brasileiro de dados (separador `;`, decimal `,`, encoding latin1)

## Como usar

Copie o conteúdo de `r-stats-skill.md` como system prompt do seu modelo de preferência, ou registre o arquivo como skill/comando em ferramentas que suportem esse formato.

## Como carregar direto do GitHub no seu agente de código

O padrão geral é sempre o mesmo: baixar o arquivo raw do GitHub e salvá-lo na pasta de prompts/comandos customizados da sua ferramenta.

Link raw do arquivo:
`https://raw.githubusercontent.com/diegoamrg4123/ai-skill-for-r-stats/main/r-stats-skill.md`

Baixar via terminal:
```bash
curl -o r-stats-skill.md https://raw.githubusercontent.com/diegoamrg4123/ai-skill-for-r-stats/main/r-stats-skill.md
```

Depois, em cada ferramenta:

**Claude Code**
Salve o arquivo em `~/.claude/commands/r-stats.md` (ou dentro de uma pasta de skill em `~/.claude/skills/`). Depois é só chamar com `/r-stats` em qualquer sessão.

**Codex CLI**
Cole o conteúdo do arquivo nas instruções customizadas do projeto (`AGENTS.md`) ou nas configurações de system prompt da sessão.

**Antigravity**
Adicione o conteúdo como instrução customizada/system prompt do agente, na área de configuração de contexto do projeto.

**OpenCode**
Salve o arquivo na pasta de agentes/prompts customizados do projeto (normalmente `.opencode/` ou equivalente) e referencie ao iniciar a sessão.

Cada ferramenta tem sua própria convenção de pasta e pode mudar com novas versões, então vale conferir a documentação oficial de custom prompts/commands da ferramenta escolhida. O importante é que o arquivo `r-stats-skill.md` é autocontido: basta colar o texto inteiro como instrução para o agente passar a segui-lo.

## Licença

MIT. Veja o arquivo `LICENSE` para o texto completo.
