---
name: sankhya-prototipo
description: >
  Use esta skill SEMPRE que o pedido for criar, revisar ou evoluir um PROTÓTIPO de tela para o ERP Sankhya —
  "criar protótipo", "prototipar tela", "mockup de tela", "wireframe", "tela de exemplo", "simular a tela",
  "como ficaria a tela de X", "protótipo navegável", "tela para validar com o cliente", "POC de tela",
  "protótipo no padrão Sankhya", "tela no Design System", "tela Acorde", "protótipo para Figma Make".
  Também acione quando o usuário descrever uma tela de ERP (cadastro, consulta, listagem, CRUD, formulário,
  wizard, dashboard, portal, aprovação, painel operacional) e quiser vê-la antes de implementar.
  Unifica o Product Language System (PLS v2.0 Sankhya) — voz, tom, terminologia canônica, padrões de microcopy
  por componente — com o Design System Acorde/EzUI, gerando um HTML standalone navegável.
  NÃO use para implementar a tela de produção (aí é sankhya-frontend-dev / sankhya-frontend-design-system /
  sankhya-js) nem para escrever escopo ou orçamento (assistente-escopo-customizacao, sankhya-estimativa-planejador).
---

# Protótipo de Tela Sankhya — PLS + Acorde

## 1. O que esta skill entrega

Um **HTML standalone navegável** (arquivo único, sem Node, sem build, abre em qualquer navegador) que
representa uma tela do ERP Sankhya com:

- **Linguagem correta desde o rascunho** — todo texto segue o Product Language System (PLS v2.0 Sankhya).
  O protótipo não usa "lorem ipsum" nem placeholder genérico: usa o microcopy que vai para produção.
- **Aparência do Design System** — layout, espaçamento, tipografia e componentes no padrão Acorde/EzUI,
  reproduzidos em CSS puro (`assets/acorde-base.css`) com os **tokens oficiais** publicados em
  https://gilded-nasturtium-6b64dd.netlify.app/docs/components/layout-doc/acorde/ —
  Ocean Green `#008561` como única cor de ação, Roboto 14px de leitura, espaçamento base 16,
  raio 24 em superfície. Nada de cor inventada.
- **Todos os estados da tela**, não só o fluxo feliz: vazio, carregando, erro, bloqueado, parcial, sucesso.
- **Mapa de implementação**: qual componente real (`ez-*`, `snk-*` ou `sk-*` do sankhya-js) corresponde a
  cada bloco do protótipo, e o que ainda depende de backend.

O protótipo é artefato de **validação e alinhamento** — com cliente, produto e time. Não é código de produção.

## 2. Fluxo obrigatório (não pule etapas)

### Etapa 1 — Briefing mínimo

Antes de desenhar qualquer coisa, você precisa de 5 informações. Pergunte **apenas as que faltam**,
em uma única rodada, e assuma defaults declarados para o resto:

| # | Informação | Default se ausente |
|---|---|---|
| 1 | Módulo e entidade (ex.: Comercial / Pedido de venda) | perguntar — sem isso não há terminologia correta |
| 2 | Persona principal (Operador, Gestor, Controller, TI, Executivo) | Operador |
| 3 | Objetivo do usuário na tela (o que ele precisa concluir) | perguntar — define título, CTA e hierarquia |
| 4 | Arquétipo de tela (listagem, CRUD, formulário, wizard, dashboard, aprovação, detalhe) | inferir do objetivo e **declarar a suposição** |
| 5 | Origem dos dados (tabela/campos reais ou fictícios) | fictícios coerentes, marcados como tal |

Leia `references/prototipo-workflow.md` para o questionário completo e os arquétipos de tela.

### Etapa 2 — Ancorar nos dados reais

Se o usuário citou tabela, entidade ou campo Sankhya, **valide no MCP `sankhya-schema` antes de escrever
qualquer label** (`search_tables`, `describe_table`, `search_columns`). Nunca invente nome de campo.

Ao trazer campos do dicionário para a tela, aplique **PLS-DATA-001**: o label é o termo do domínio do
usuário, não o nome do banco. `VLRLIQ` vira "Valor líquido"; `DTNEG` vira "Data de negociação".
Mantenha o nome técnico apenas como comentário HTML, para o desenvolvedor.

### Etapa 3 — Escrever o microcopy ANTES do HTML

Esta é a inversão que diferencia esta skill: primeiro a linguagem, depois o layout.

Produza uma tabela de conteúdo da tela, e só então gere o HTML:

| Elemento | Estado | Texto | Rule ID / referência |
|---|---|---|---|
| Título da tela | padrão | ... | PLS-UI-001 |
| CTA primário | padrão | ... | PLS-UI-002 |
| Empty state | vazio | ... | PLS-UI-004 |
| Erro de validação | erro | ... | PLS-UI-003 |

Regras que valem para todo texto do protótipo:

- Verbo canônico do PLS em CTAs (`Salvar`, `Criar`, `Excluir`, `Enviar para aprovação`) — ver `references/pls-terminology.md`.
- Erro = o que aconteceu + por que + como resolver. Nunca "Erro inesperado".
- Empty state orienta a próxima ação. Nunca "Sem dados".
- Confirmação destrutiva repete a entidade no CTA: "Excluir pedido #4521".
- Tooltip não conserta label ruim — se precisou de tooltip para entender o label, corrija o label.
- Estado canônico: `Rascunho`, `Aguardando aprovação`, `Aprovado`, `Rejeitado`, `Cancelado`, `Concluído`, `Parcial`, `Bloqueado`, `Em processamento`.

Consulte, conforme o componente: `references/pls-patterns.md`, `references/pls-voice-tone.md`,
`references/pls-terminology.md`, `references/decision-tree.md`.

### Etapa 4 — Montar o HTML

1. Parta de `assets/template-tela.html` e **embuta `assets/acorde-base.css` inline** no `<style>` —
   o arquivo final tem que ser único e autossuficiente. O `:root` do base.css já traz os tokens
   oficiais do Design System; não sobrescreva valor de token sem declarar o motivo.
2. Use as classes do base.css (`sk-topbar`, `sk-sidenav`, `sk-toolbar`, `sk-grid`, `sk-form`, `sk-modal`,
   `sk-empty`, `sk-toast`, `sk-tag`…). Não invente CSS solto quando já existe classe.
3. Nomes de arquivo e de bloco em português; comentários explicando **o porquê** de cada decisão de UI.
4. Marque toda pendência com `<!-- TODO: ... -->`: serviço inexistente, regra não confirmada, campo a validar.

### Etapa 5 — Cobrir os estados alternativos

O protótipo é entregue **incompleto** se só mostra o fluxo feliz. Inclua um seletor de estado
(o template já traz `sk-state-switcher`) permitindo alternar entre:

`padrão · vazio · carregando · erro · bloqueado (sem permissão) · parcial · sucesso`

Cada estado com seu microcopy próprio, escrito na Etapa 3.

### Etapa 6 — Fechar a entrega

1. Rode o checklist de `assets/checklist-entrega.md`. Não declare pronto sem passar por ele.
2. Abra o arquivo no navegador para conferir que renderiza (use a skill `webapp-testing` ou Playwright
   quando disponível) — **não afirme que está pronto sem ter visto renderizar**.
3. Entregue, ao final da resposta:
   - caminho do arquivo gerado;
   - tabela de microcopy da Etapa 3;
   - **mapa de implementação** (protótipo → componente real), conforme `references/design-system-acorde.md`;
   - suposições declaradas e TODOs em aberto.
4. Ofereça publicar como Artifact (link privado, compartilhável com o cliente) — só publique se o usuário aceitar.

## 3. Guardrails

Nunca invente: regra de negócio, comportamento do sistema, nome de campo ou tabela, nome de funcionalidade,
serviço de backend, métrica, integração existente ou promessa de IA.

Quando faltar contexto, escreva a suposição de forma explícita:
> "Estou assumindo que o pedido só pode ser enviado para aprovação com pelo menos um item."

Não diga que algo é "padrão Sankhya" se não estiver no PLS ou no Design System. Diga que é
**recomendação para o PLS**.

Não trate escolha estética como verdade. Justifique com clareza, consistência, ação, acessibilidade,
escalabilidade ou impacto.

## 4. Hierarquia de decisão (herdada do PLS)

1. Regra de negócio e comportamento real do sistema
2. Objetivo do usuário na jornada
3. Clareza da informação
4. Próxima ação esperada
5. Consistência com o PLS
6. Consistência com o Design System (Acorde)
7. Acessibilidade e escaneabilidade
8. Voz e tom Sankhya
9. Concisão

Conflitos: concisão vs. clareza → clareza. Criatividade vs. consistência → consistência.
Falta de contexto → declare a suposição antes de recomendar.

## 5. Mapa de arquivos da skill

| Preciso de… | Arquivo |
|---|---|
| Questionário de briefing, arquétipos de tela, matriz de estados | `references/prototipo-workflow.md` |
| Anatomia da tela, classes `sk-*`, mapa protótipo → `ez-*`/`snk-*` | `references/design-system-acorde.md` |
| Valores exatos de token e regras de uso de cor do DS | `references/design-tokens-sankhya-ds.md` |
| Estrutura de erro, empty state, tooltip, CTA, modal, toast | `references/pls-patterns.md` |
| Voz, matriz de tom por contexto, anglicismos, acessibilidade, i18n | `references/pls-voice-tone.md` |
| Glossário canônico, verbos, estados, módulos, personas | `references/pls-terminology.md` |
| Rule IDs, guardrails de agente, ICU MessageFormat, princípios | `references/pls-core.md` |
| Decisão rápida de qual padrão aplicar | `references/decision-tree.md` |
| Templates de resposta (revisão de microcopy, erro, empty, modal) | `references/response-templates.md` |
| Esqueleto HTML da tela | `assets/template-tela.html` |
| CSS base com os tokens Acorde | `assets/acorde-base.css` |
| Tokens oficiais do DS (cor, tipografia, espaço, raio) e lista real de componentes | `references/design-tokens-sankhya-ds.md` |
| Checklist final antes de entregar | `assets/checklist-entrega.md` |

## 6. Fronteiras

- **Implementação de produção** → `sankhya-frontend-design-system` (Vite + `ez-*`/`snk-*`), `sankhya-js`
  (AngularJS legado) ou `sankhya-frontend-dev` (roteador). O protótipo alimenta esses agentes; não os substitui.
- **Escopo funcional / requisitos** → `assistente-escopo-customizacao`.
- **Estimativa e backlog** → `sankhya-estimativa-planejador`.
- **Dashboard de BI de verdade** → `sankhya-bi`. Aqui só se prototipa a aparência do painel.
- **Revisão de microcopy sem tela** → use direto as referências PLS desta skill, sem gerar HTML.
