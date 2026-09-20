# Design System Sankhya (Acorde / EzUI) para protótipos

> Referência visual e de componentes usada na Etapa 4 do `SKILL.md`.
> O protótipo **imita** o Design System em CSS puro; ele não carrega os web components reais.
> O mapa da seção 5 é o que liga o protótipo à implementação de produção.

---

## 1. Status desta referência

| Item | Situação |
|---|---|
| Cor, tipografia, espaçamento e raio | **oficiais** — extraídos da doc do Design System Sankhya |
| Lista de componentes `ez-*` / `snk-*` | **oficial** — extraída do índice da doc |
| Estrutura de layout de tela (topbar, sidenav, page header) | derivada do uso real no ERP, não de página específica da doc |
| Sombras | tokens legados (`--shadow--*`); o DS ainda não publicou substituto |

Fonte de verdade:
https://gilded-nasturtium-6b64dd.netlify.app/docs/components/layout-doc/acorde/

Os valores estão em `references/design-tokens-sankhya-ds.md` e já aplicados em `assets/acorde-base.css`.
A página `/tokens/` da doc está **depreciada** — não use os nomes antigos (`--color--primary`,
`--text--medium`, `--space--sm`, `--border--radius-medium`).

O que ainda é decisão do protótipo, não do DS — declare ao entregar:

- raio de **8px em controles** (botão, input, tag). O DS padroniza 24px, que em controle de 32px
  vira pílula; 24 (superfície) + 8 (controle) são duas variações, dentro do limite que o DS recomenda;
- **info/processando em neutro petroleum** — a paleta nova não tem azul, e verde/amarelo/vermelho
  são reservados a feedback de sistema.

---

## 2. Anatomia de uma tela do ERP

```
+---------------------------------------------------------------+
| sk-topbar    marca - busca global - empresa/usuario - ajuda    |
+----------+----------------------------------------------------+
| sk-side   | sk-page-header   titulo - descricao - CTA primario |
| nav       +----------------------------------------------------+
|           | sk-toolbar       filtros - busca - acoes em lote    |
| modulos   +----------------------------------------------------+
| e telas   | sk-content       grade / formulario / cartoes       |
|           |                                                     |
|           +----------------------------------------------------+
|           | sk-page-footer   paginacao ou acoes do formulario   |
+----------+----------------------------------------------------+
```

Regras de layout:

- **Um** CTA primário por tela, sempre no `sk-page-header` (ou no rodapé fixo, em formulário longo).
- Título responde "onde estou / que trabalho é este" — "Pedidos em aberto", não "Gerenciamento de Pedidos".
- Descrição opcional, no máximo 2 linhas, complementa o título sem repeti-lo.
- Filtros ficam acima do conteúdo e **permanecem visíveis** quando o resultado é vazio.
- Conteúdo ocupa toda a largura útil; ERP não é landing page.

---

## 3. Componentes disponíveis no `acorde-base.css`

| Classe | Papel | Observações de uso |
|---|---|---|
| `sk-topbar` | barra superior do produto | fixa; identifica empresa e usuário |
| `sk-sidenav` / `sk-sidenav__item` | navegação de módulos | item ativo com `is-active` |
| `sk-page-header` | título, descrição e CTA primário | `sk-page-header__actions` alinha à direita |
| `sk-breadcrumb` | trilha de navegação | só quando há hierarquia real |
| `sk-toolbar` | filtros, busca, ações em lote | usar `sk-chip` para filtros aplicados |
| `sk-chip` | filtro aplicado, removível | texto do filtro + "×" |
| `sk-btn` | botão | `--primary`, `--secondary`, `--tertiary` (apelido legado: `--ghost`), `--danger`; `disabled`. Nomes espelham o `variant` do `ez-button` |
| `sk-field` | campo de formulário | label visível sempre, nunca só placeholder |
| `sk-field--required` | campo obrigatório | marca no label, não só na validação |
| `sk-field.is-invalid` + `sk-field__error` | erro de validação | mensagem no campo, não só no topo |
| `sk-form` / `sk-form__section` | formulário agrupado por afinidade de negócio | seção com título curto |
| `sk-grid` | grade de dados | cabeçalho fixo; numérico à direita |
| `sk-grid__row.is-selected` | seleção de linha | seleção múltipla habilita ações em lote |
| `sk-tag` | situação do registro | `--rascunho`, `--aguardando`, `--aprovado`, `--rejeitado`, `--cancelado`, `--concluido`, `--parcial`, `--bloqueado`, `--processando`; sempre com **texto** |
| `sk-tabs` / `sk-tabs__item` | abas dentro da tela | no máximo 2 níveis de navegação interna |
| `sk-card` | agrupador de conteúdo | usado em painéis e dashboards |
| `sk-kpi` | cartão de indicador | valor + rótulo + variação; nunca só o número |
| `sk-empty` | estado vazio | ícone neutro + texto orientador + ação |
| `sk-alert` | aviso, erro ou informação na tela | `--info`, `--warning`, `--danger`, `--success` |
| `sk-toast` | confirmação breve | nunca para informação crítica |
| `sk-modal` | confirmação e ações com consequência | título = o que vai acontecer |
| `sk-skeleton` | carregamento | reproduz a forma do conteúdo real |
| `sk-wizard` / `sk-wizard__step` | fluxo em etapas | etapa concluída, atual e futura distinguíveis |
| `sk-state-switcher` | seletor de estados do protótipo | **só existe no protótipo**; não vai para produção |

---

## 4. Tokens

O `acorde-base.css` tem duas camadas em `:root`:

1. **tokens oficiais do DS**, com o nome real — `--color--ocean-green-*`, `--color--petroleum-*`,
   `--color--gray-*`, `--color--green|yellow|red-*`, `--font--pattern`, `--font-size--*`,
   `--font-weight--*`, `--line-height--*`, `--space--*`, `--border--radius-*`, `--shadow--*`;
2. **aliases `--sk-*`** usados pelas classes deste arquivo, todos derivados da camada 1.

| Grupo | Alias | Deriva de |
|---|---|---|
| Marca | `--sk-color-primary` / `-hover` / `-soft` | ocean-green 600 / 700 / 90 |
| Superfície | `--sk-color-bg`, `-surface`, `-surface-alt`, `-border`, `-border-strong` | petroleum 80, branco, gray 80, petroleum 90, petroleum 100 |
| Texto | `--sk-color-text`, `-text-muted`, `-text-inverse` | petroleum 600, petroleum 400, branco |
| Navegação | `--sk-color-nav-bg`, `-nav-text`, `-nav-active` | petroleum 600, petroleum 100, branco |
| Semântica | `--sk-color-success/warning/danger/info/neutral` (+ `-soft`) | green 600, yellow 800, red 600, petroleum 500, petroleum 400 |
| Tipografia | `--sk-font`, `--sk-font-size-xs…2xl` | Roboto; 10 / 12 / **14** / 16 / **24** / 32 |
| Espaçamento | `--sk-space-1` a `-8` | 4 · 8 · 12 · **16** · 20 · **24** · 32 · 40 |
| Forma | `--sk-radius-sm` = 8, `-md` / `-lg` = **24**, `--sk-shadow-1/2` | — |
| Layout | `--sk-topbar-h` 48px, `--sk-sidenav-w` 232px | decisão do protótipo |

Regras que o DS impõe e que o protótipo tem que respeitar:

- **20% cor de ação, 80% neutro.** Ocean green só em ação; teto de 20% da tela.
- **Texto de leitura em 14px**, título em 24px. Sem variação de tamanho por capricho.
- **Verde/amarelo/vermelho = feedback de sistema.** Nunca em botão de ação nem como cor de marca.
  Sucesso é `#157A00`, não o verde da marca `#008561`.
- **Amarelo não vai em fundo claro** como cor de texto — use yellow-800 no texto, yellow-100 no fundo.
- **No máximo duas variações de raio** no mesmo layout.

Nunca escreva hex solto no HTML do protótipo — use o token. Se falta token para o que você quer,
o problema é a decisão de design.

A lista completa dos componentes que existem de verdade no DS (70 `ez-*` e 19 `snk-*`) está em
`references/design-tokens-sankhya-ds.md`, seção 6. Não prometa componente fora dessa lista.

---

## 5. Mapa protótipo → implementação real

Entregue esta tabela ao final de todo protótipo, preenchida com os blocos que a tela realmente usa.

| Bloco do protótipo | Design System (Node/React) | AngularJS legado (sankhya-js) | Depende de backend |
|---|---|---|---|
| `sk-topbar` + `sk-sidenav` | shell do ERP (`snk-application`) | shell do workspace | não |
| Grade de dados | `snk-grid` dentro de `snk-data-unit` | `sk-datagrid` + `sk-dataset` | consulta / dicionário |
| CRUD completo (grade + form) | `snk-crud` | `sk-dataset` + `sk-dynaform` | dicionário da entidade |
| Formulário | `snk-form` ou `ez-form` | `sk-dynaform` / `sk-form` | serviço de gravação |
| Filtros | `snk-filter-bar` | `sk-filter-panel` | config server-side |
| Busca de registro | `snk-pesquisa` | `sk-pesquisa` | consulta |
| Botão | `ez-button` | `sk-button` | não |
| Campos | `ez-text-input`, `ez-number-input`, `ez-date-input`, `ez-combo-box` | `sk-input`, `sk-date`, `sk-combo` | domínio/opções |
| Abas | `ez-tabselector` | `sk-tabs` | não |
| Modal / confirmação | `ez-modal`, `ez-dialog` | `SanPopup` | não |
| Toast / alerta | `ez-toast`, `ez-alert` | `sk-messages` | não |
| Wizard | composição `ez-*` por etapa | `sk-wizard` | serviço por etapa |
| Upload | `ez-upload` | `sk-upload` | serviço de anexo |
| Gráfico | `ez-chart` | componente de BI | consulta agregada |
| KPI | `ez-card-item` / composição | cartão custom | consulta agregada |
| Exportação | `snk-data-exporter` | ação de exportação | serviço |
| Anexos | `snk-attach` | anexo padrão | serviço de anexo |

Ao entregar o mapa, marque cada serviço de backend como **existe** ou **`TODO` — precisa ser criado**,
e diga qual agente assume: `sankhya-backend-dev`, `sankhya-data-dev`, `sankhya-frontend-design-system`,
`sankhya-frontend-angular` ou `sankhya-bi-report-dev`.

---

## 6. Avisos que o protótipo deve carregar quando o alvo for Design System real

Se o usuário indicar que a tela vai virar Design System em addon, registre no fechamento:

1. `ez-*`/`snk-*` só renderizam com pipeline Node e `defineCustomElements()` no entrypoint —
   sem isso a tela sai **em branco**, sem erro óbvio no console.
2. Em addon, `snk-application` ainda exige, no `index.html`: `window.APPLICATION_NAME`, bridge da função
   global `utxt` a partir de `window.parent`, e warm-up de sessão no BFF antes de montar a aplicação.
3. `snk-grid` só mostra a barra de filtros se houver configuração de filtro não-vazia vinda do servidor.

Esses pontos não afetam o protótipo HTML, mas mudam a estimativa da implementação — diga isso
antes que o time prometa prazo com base no protótipo.
