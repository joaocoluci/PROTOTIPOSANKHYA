# PLS Terminologia — Glossário Canônico

> Fonte: Product Language System v2.0 Sankhya — Domínios `/core`, `/data`, `/ui`  
> Leia este arquivo quando a tarefa envolver escolha de termos, revisão de labels ou padronização terminológica.

---

## Regras gerais de terminologia

1. Escolha sempre uma forma preferencial por conceito
2. Documente termos relacionados e variações proibidas
3. Considere o uso em: UI, documentação, agente de IA, comunicação interna
4. Avalie impacto em tradução antes de consolidar
5. Não troque termos consolidados sem avaliar impacto operacional

**Se houver dúvida entre termo técnico e termo simples:**
- Prefira o termo reconhecido pelo usuário da jornada
- Explique o termo técnico em texto de apoio se necessário
- Nunca troque termos consolidados sem avaliar o impacto nos fluxos existentes

---

## Glossário de entidades principais

| Termo canônico | Variações aceitas | Variações proibidas | Contexto |
|---|---|---|---|
| Pedido de venda | Pedido | Ordem de venda, PV, Ordem | Módulo Comercial |
| Nota fiscal eletrônica | NF-e | NFe, nota, NF | Módulo Fiscal |
| Ordem de compra | OC | Pedido de compra (evitar confusão) | Módulo Compras |
| Conta a pagar | — | Contas a pagar (plural em lista) | Módulo Financeiro |
| Conta a receber | — | Contas a receber (plural em lista) | Módulo Financeiro |
| Centro de custo | — | CC (somente em contexto técnico) | Módulo Contábil |
| Estoque | — | Inventário (evitar anglicismo) | Módulo Estoque |
| Parceiro de negócio | Cliente / Fornecedor / Transportadora | PN (somente técnico) | Cadastros |
| Situação | Status (aceito em contexto técnico) | State, Condição | Labels de campo |
| Competência | — | Período (ambíguo) | Contabilidade |

---

## Verbos canônicos — Resumo rápido

| Ação | Verbo preferido | Evitar |
|---|---|---|
| Persistir dados | Salvar | Gravar, Registrar |
| Criar entidade | Criar | Incluir, Novo |
| Remover entidade | Excluir | Deletar, Apagar, Remover |
| Enviar ao fluxo | Enviar para [destino] | Submeter, Mandar |
| Desfazer | Desfazer | Reverter (técnico) |
| Publicar | Publicar | Ativar, Implantar |
| Consultar | Consultar, Buscar | Pesquisar (prefira "Buscar" em UI) |
| Aprovar | Aprovar | Validar (ambíguo em contexto de aprovação) |
| Rejeitar | Rejeitar | Recusar, Negar |
| Vincular | Vincular | Associar, Ligar |

---

## Estados canônicos

| Estado | Label preferido | Evitar |
|---|---|---|
| Em criação / não enviado | Rascunho | Em edição, Pendente |
| Enviado para aprovação | Aguardando aprovação | Em análise (ambíguo) |
| Aprovado | Aprovado | OK, Válido |
| Rejeitado | Rejeitado | Reprovado, Negado |
| Cancelado | Cancelado | Inativado (outro conceito) |
| Concluído | Concluído | Finalizado, Fechado |
| Parcialmente concluído | Parcial | Incompleto |
| Bloqueado | Bloqueado | Travado, Com restrição |
| Em processamento | Em processamento | Carregando (para dados), Processando |

---

## Termos de IA e automação — Política do PLS

| Conceito | Termo preferido | Evitar |
|---|---|---|
| O agente de IA da Sankhya | BIA | Chatbot, Bot, Assistente virtual |
| Geração de texto com IA | BIA Escreve | IA de escrita, Redator IA |
| Sugestão feita pela IA | "BIA sugeriu…" | "A IA decidiu…", "O sistema escolheu…" |
| Limite de capacidade | "BIA não consegue fazer isso ainda" | "Funcionalidade não disponível" (impessoal demais) |
| Confirmação de ação da IA | "Posso [ação]?" | "Vou [ação] agora" (sem confirmação) |
| Resultado não verificado | "Revisar antes de usar" | "Pronto" |

**Proibido para IA:**
- "Tenho certeza" quando inferindo
- "Resolvi" quando depende de validação externa
- Qualquer linguagem que oculte limitações
- "Inteligente", "revolucionário", "poderoso" sem evidência concreta

---

## Termos de interface — Referência rápida

| Componente | Termo preferido | Evitar |
|---|---|---|
| Caixa de texto | Campo de texto | Input, Textbox |
| Lista suspensa | Lista suspensa | Dropdown, Combo |
| Caixa de seleção | Caixa de seleção | Checkbox |
| Botão de alternância | Alternância | Toggle, Switch |
| Janela flutuante | Modal | Popup, Overlay |
| Mensagem de sistema | Notificação | Toast (interno) |
| Barra de progresso | Indicador de progresso | Loading bar |
| Aba | Aba | Tab |
| Painel lateral | Painel | Drawer, Sidebar |
| Rodapé da tabela | Resumo | Footer |

---

## Módulos e domínios do produto — Nomenclatura oficial

| Módulo | Nome oficial | Abreviação aceita |
|---|---|---|
| Gestão comercial | Comercial | — |
| Gestão de compras | Compras | — |
| Gestão financeira | Financeiro | — |
| Gestão contábil | Contabilidade | — |
| Gestão de estoque | Estoque | — |
| Gestão fiscal | Fiscal | — |
| Gestão de produção | Produção | MRP (contexto técnico) |
| Gestão de pessoas | RH | — |
| Gestão de projetos | Projetos | — |
| Central de atendimento | Atendimento | SAC (contexto externo) |

---

## Personas de referência

| Persona | Perfil | Linguagem adequada |
|---|---|---|
| Operador | Usuário operacional, trabalha com fluxos do dia a dia | Direta, orientada à tarefa, sem jargão técnico |
| Gestor | Líder de área, foco em resultados e visão geral | Estratégica, resumida, com dados e impacto |
| Controller / Contador | Especialista financeiro/contábil, conhece jargão fiscal | Técnica mas precisa, sem ambiguidade |
| TI / Implantador | Configura e implanta o sistema | Técnica, estruturada, com exemplos práticos |
| Executivo | Toma decisões estratégicas, alto nível | Objetiva, orientada a negócio, sem detalhes técnicos |
