# PLS Patterns — Padrões por Componente

> Fonte: Product Language System v2.0 Sankhya — Domínio `/ui`  
> Leia este arquivo quando a tarefa envolver criação ou revisão de microcopy específico por componente.

---

## Mensagens de erro

**Estrutura obrigatória:**
1. O que aconteceu
2. Por que aconteceu (se útil e conhecido)
3. Como resolver ou qual próximo passo

**Exemplo correto:**
> "Não foi possível salvar as alterações. Revise os campos obrigatórios e tente novamente."

**Exemplos a evitar:**

| Errado | Problema |
|---|---|
| "Erro inesperado." | Não informa nada útil |
| "Falha na operação." | Vago, sem orientação |
| "Dados inválidos." | Não indica quais dados nem como corrigir |
| "Não foi possível concluir." | Sem causa nem próximo passo |
| "Entre em contato com o administrador." | Só aceitável como último recurso, nunca como única orientação |

**Regras adicionais:**
- Quando o erro for técnico, traduza o impacto para a linguagem do usuário
- Quando não houver solução imediata, explique o estado e oriente o próximo passo possível
- Nunca culpe o usuário
- Nunca use humor em mensagens de erro
- Nível de detalhe proporcional à gravidade: erro bloqueante > aviso > informativo

---

## Empty states

**Estrutura:**
1. O que ainda não existe
2. Por que aquele espaço está vazio (quando relevante)
3. O que o usuário pode fazer agora

**Exemplo correto:**
> "Nenhum pedido encontrado. Ajuste os filtros ou crie um novo pedido para começar."

**Exemplos a evitar:**

| Errado | Problema |
|---|---|
| "Sem dados." | Frio, sem orientação |
| "Nenhum resultado." | Genérico, não orienta ação |
| "Lista vazia." | Não explica nem orienta |

**Variações por contexto:**

| Contexto | Padrão recomendado |
|---|---|
| Filtro sem resultado | "[Entidade] não encontrada com esses filtros. Ajuste os critérios ou limpe os filtros." |
| Módulo novo/vazio | "Nenhum [entidade] cadastrado ainda. Crie o primeiro [entidade] para começar." |
| Permissão insuficiente | "Você não tem acesso para ver este conteúdo. Fale com o administrador do sistema." |
| Dados em processamento | "[Entidade] sendo carregada. Aguarde alguns instantes." |

---

## Tooltips

**Devem:**
- Explicar algo que não cabe no rótulo
- Esclarecer regra, restrição ou consequência
- Ser breves (preferencialmente 1–2 linhas)
- Não repetir o label

**Não devem:**
- Corrigir labels ruins (se o tooltip é necessário para entender o label, o label precisa ser revisado)
- Esconder informação essencial da jornada
- Conter instruções longas ou múltiplos parágrafos
- Substituir documentação de funcionalidade

**Exemplo correto:**
> Label: "Data de competência"  
> Tooltip: "Data em que a despesa ocorreu, independentemente do pagamento."

**Exemplo incorreto:**
> Label: "DC"  
> Tooltip: "DC significa Data de Competência, ou seja, a data em que a despesa ocorreu, que pode ser diferente da data de pagamento e é usada para fins contábeis."  
> → *Problema: o label precisa ser corrigido, não o tooltip expandido.*

---

## Labels

**Devem:**
- Usar substantivos ou termos reconhecíveis pelo usuário
- Evitar abreviações
- Manter consistência com termos já definidos no PLS
- Representar o dado ou a ação com precisão
- Seguir o domínio do usuário, não a nomenclatura do banco de dados

**Evitar:**

| Problema | Exemplo ruim | Exemplo correto |
|---|---|---|
| Sigla sem contexto | "NF-e" em contexto financeiro sem explicação | "Nota Fiscal Eletrônica" ou "NF-e" após apresentação |
| Label técnico de banco | `VLRLIQ` | "Valor líquido" |
| Variação sem padrão | "N", "Nt.", "Nota", "NOTA" para o mesmo campo | "Observações" (ou o termo canonizado no PLS) |
| Termo interno de dev | "Status_flag" | "Situação" |
| Label excessivamente longo | "Data de emissão do documento fiscal eletrônico" | "Data de emissão" |

**Ao revisar labels do Dicionário de Dados, verifique:**
- Significado para o usuário final (não para o desenvolvedor)
- Módulo ou jornada em que o campo aparece
- Diferença entre dado técnico interno e dado refletido na interface
- Impacto em internacionalização
- Risco de ambiguidade
- Relação com campos semelhantes no mesmo formulário

---

## CTAs (Calls to Action)

**Padrão:** verbo no infinitivo + objeto específico

**Exemplos preferidos:**

| CTA | Contexto |
|---|---|
| "Salvar alterações" | Formulário com edição |
| "Criar pedido" | Início de fluxo de criação |
| "Adicionar produto" | Linha de item em pedido |
| "Revisar dados" | Validação antes de submissão |
| "Enviar para aprovação" | Submissão de fluxo |
| "Excluir [entidade]" | Ação destrutiva com contexto |
| "Cancelar pedido" | Ação irreversível específica |

**Evitar:**

| CTA ruim | Problema |
|---|---|
| "OK" | Não indica o que será feito |
| "Sim" / "Não" isolados | Sem contexto de decisão |
| "Prosseguir" | Vago; prefira a ação específica |
| "Confirmar" sem objeto | O usuário não sabe o que está confirmando |
| "Fechar" como CTA primário em modal de ação | Abandona o fluxo sem indicar |

**Em ações destrutivas ou irreversíveis:**
- Repita o nome da entidade no CTA: "Excluir pedido #1234"
- Use cor/ênfase diferenciada no Design System
- Exija confirmação explícita (modal, não apenas toast)

---

## Títulos e descrições

**Títulos devem responder:**
- Onde o usuário está
- Qual tarefa será feita
- Qual resultado será alcançado

**Prefira títulos orientados ao trabalho do usuário:**

| Evitar | Preferir |
|---|---|
| "Cadastros" | "Clientes cadastrados" |
| "Gerenciamento de Pedidos" | "Pedidos em aberto" |
| "Configurações do Sistema" | "Configurações de integração fiscal" |
| "Relatório" | "Relatório de vendas por período" |

**Descrições:**
- Complementam o título, não o repetem
- Explicam o propósito da tela ou o que o usuário pode fazer aqui
- Máximo de 2 linhas em contexto de interface
- Podem incluir restrições ou contexto relevante

---

## Notificações e toasts

**Estrutura por tipo:**

| Tipo | Propósito | Exemplo |
|---|---|---|
| Sucesso | Confirma que a ação foi concluída | "Pedido salvo com sucesso." |
| Aviso | Alerta sobre situação que exige atenção | "Estoque abaixo do mínimo para este produto." |
| Erro | Informa falha e orienta | "Não foi possível salvar. Verifique os campos obrigatórios." |
| Informativo | Comunica estado ou processo | "Sincronização em andamento. Os dados serão atualizados em instantes." |

**Regras:**
- Toasts de sucesso devem ser breves (até 10 palavras)
- Toasts de erro nunca devem ser a única orientação — inclua próximo passo
- Não use toasts para informações críticas que o usuário precisa ler com atenção
- Modais são mais adequados para erros bloqueantes ou ações com consequências

---

## Confirmações e modais de ação

**Estrutura de modal de confirmação:**
1. Título: o que está prestes a acontecer
2. Corpo: consequência da ação (não repita o título)
3. CTA primário: ação específica e irreversível
4. CTA secundário: cancelar, com contexto

**Exemplo:**
> **Título:** Excluir pedido #1234?  
> **Corpo:** Esta ação não pode ser desfeita. Os itens vinculados também serão removidos.  
> **CTA primário:** Excluir pedido  
> **CTA secundário:** Cancelar

**Evitar:**
- "Tem certeza?" como título — muito vago
- "Sim" e "Não" como CTAs — sem contexto de decisão
- Corpo longo com instruções — modal de confirmação não é manual

---

## Onboarding e orientações de primeiros passos

**Princípios:**
- Orientação, não apresentação institucional
- Foco na primeira ação, não na lista de funcionalidades
- Progressivo: não entregue tudo de uma vez
- Vinculado ao contexto: apareça onde a ação acontece

**Evitar:**
- Tours automáticos longos
- "Bem-vindo ao [produto]!" como única informação
- Instruções que assumem conhecimento prévio do ERP
