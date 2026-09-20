# PLS Core — Referência Canônica

> Fonte: Product Language System v2.0 Sankhya  
> Este arquivo alimenta o contexto operacional da skill `product-language-system`.

---

## Estrutura do PLS v2.0

O PLS organiza-se em **10 domínios** e **2 anexos**:

| Domínio | Caminho | Conteúdo principal |
|---|---|---|
| Fundamentos | `/core` | Princípios, voz, tom, hierarquia de decisão |
| Interface | `/ui` | Microcopy, componentes, estados, acessibilidade |
| Agentes de IA | `/agent` | BIA, BIA Escreve, turn-taking, repair, fallback, confiança |
| Código | `/code` | Nomenclatura técnica, comentários, tokens |
| Dados | `/data` | Dicionário de Dados, labels de entidade, ICU MessageFormat |
| Design/PM | `/design_pm` | Briefing, roadmap, critérios de aceitação |
| Documentação | `/docs` | Tech Writing, artigos de ajuda, release notes |

---

## Princípios centrais (PLS /core)

1. Clareza antes de criatividade
2. Precisão antes de persuasão
3. Consistência antes de variação
4. Orientação à ação antes de explicação extensa
5. Linguagem simples, sem simplificar demais o problema
6. Tom profissional, direto, humano e acessível
7. Microcopy deve reduzir esforço cognitivo, não apenas "soar melhor"
8. Toda mensagem deve ajudar o usuário a entender: o que aconteceu / o que significa / o que fazer
9. Evite termos técnicos quando houver alternativa mais clara
10. Não invente regra de negócio, comportamento sistêmico, fluxo técnico ou promessa de produto

---

## Verbos canônicos do PLS

Verbos preferidos para CTAs e ações de interface:

| Ação | Verbo canônico | Evitar |
|---|---|---|
| Persistir dados | Salvar | Gravar, Registrar, Confirmar |
| Criar entidade | Criar, Adicionar | Novo, Incluir |
| Excluir entidade | Excluir | Deletar, Remover (salvo relações) |
| Editar | Editar, Alterar | Modificar, Atualizar |
| Enviar para fluxo | Enviar para aprovação | Submeter, Mandar |
| Cancelar ação | Cancelar | Sair, Fechar (depende do contexto) |
| Desfazer operação | Desfazer | Reverter (contexto técnico) |
| Publicar | Publicar | Ativar (depende do módulo) |
| Revisar | Revisar | Checar, Verificar |

---

## Guardrails por nível (PLS /agent)

### Guardrail Nível I — Proibição absoluta
O agente nunca deve:
- Excluir dados sem confirmação explícita do usuário
- Executar transações financeiras sem validação humana
- Apresentar inferências como certezas
- Omitir limitações conhecidas da IA
- Personalizar a voz de forma que confunda o usuário sobre quem está respondendo

### Guardrail Nível II — Restrição condicional
O agente deve:
- Solicitar confirmação antes de ações irreversíveis
- Indicar nível de confiança quando inferir dados
- Escalar para humano quando não houver resposta adequada
- Não apresentar resposta se a confiança for inferior ao threshold definido
- Separar resposta principal de detalhes complementares

---

## Modelo de confiança do agente (PLS /agent)

| Nível de confiança | Comportamento do agente |
|---|---|
| Alta (>90%) | Executa com transparência sobre o que foi feito |
| Média (60–90%) | Executa com aviso e pede validação |
| Baixa (<60%) | Pede esclarecimento antes de agir |
| Nenhuma | Ativa fallback e escala para humano |

---

## Escada de repair (PLS /agent)

Quando o agente não entender a intenção do usuário:

1. **Repair leve** — Parafraseia a intenção e pergunta se entendeu corretamente
2. **Repair médio** — Apresenta opções interpretadas e pede escolha
3. **Repair pesado** — Declara limitação, explica o que não conseguiu entender, sugere reformulação
4. **Escalação** — Encaminha para canal humano com contexto da conversa

---

## ICU MessageFormat — Regras básicas (PLS /data)

Use ICU MessageFormat para mensagens com variáveis dinâmicas, pluralização e gênero.

```
// Exemplo plural
{count, plural,
  one {# item selecionado}
  other {# itens selecionados}
}

// Exemplo com nome
{userName, select,
  other {Olá, {userName}. Sua solicitação foi enviada.}
}
```

Evite concatenação de strings em mensagens traduzíveis.  
Nunca assuma ordem fixa de variáveis em diferentes idiomas.

---

## Rule IDs do PLS

Rule IDs são identificadores canônicos de regras do PLS, usados para rastrear conformidade em auditorias e revisões.

| Rule ID | Descrição resumida |
|---|---|
| PLS-UI-001 | Labels devem usar substantivos reconhecíveis pelo usuário final |
| PLS-UI-002 | CTAs devem indicar a ação específica, não usar "OK" ou "Sim/Não" sem contexto |
| PLS-UI-003 | Mensagens de erro devem seguir: o que aconteceu + por que + como resolver |
| PLS-UI-004 | Empty states devem orientar a próxima ação, não apenas declarar ausência |
| PLS-UI-005 | Tooltips não devem corrigir labels ruins; se necessário, melhorar o label |
| PLS-AG-001 | Agente não executa ação irreversível sem confirmação explícita |
| PLS-AG-002 | Agente não apresenta inferência como certeza |
| PLS-AG-003 | Agente declara limitações antes de escalar |
| PLS-AG-004 | Agente usa turn-taking explícito em fluxos de múltiplas etapas |
| PLS-DATA-001 | Labels de entidade no Dicionário de Dados usam termo do domínio do usuário, não do banco |
| PLS-CORE-001 | Nenhum texto de interface deve ser criado sem referência ao componente e ao estado |
| PLS-CORE-002 | Variação terminológica para o mesmo conceito é proibida sem justificativa documentada |

---

## Fluxo feliz vs. estados alternativos (PLS /ui)

O PLS exige que toda jornada documente:

- **Fluxo feliz**: caminho principal sem erros ou desvios
- **Estados alternativos**: erro, vazio, carregamento, bloqueio, parcial, sucesso com ressalva

Toda decisão de microcopy deve considerar os estados alternativos, não apenas o fluxo feliz.

---

## Artefatos do PLS v2.0

| Artefato | Função |
|---|---|
| BIA Escreve | Agente de escrita assistida por IA para textos de produto |
| Figma Make Skill | Skill de geração de interfaces seguindo PLS + Acorde |
| MCP Sankhya | Integração do PLS com fluxos de desenvolvimento via Claude Code |
| CLAUDE.md | Referência operacional do PLS para repositórios Sankhya no Claude Code |
| Dicionário de Dados | Glossário de entidades, campos e termos técnicos mapeados para linguagem de usuário |
