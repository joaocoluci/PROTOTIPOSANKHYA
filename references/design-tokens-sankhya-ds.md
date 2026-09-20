/** @author João Coluci **/
# Tokens oficiais do Design System Sankhya (Acorde)

> **Fonte de verdade:** https://gilded-nasturtium-6b64dd.netlify.app/docs/components/layout-doc/acorde/
> Páginas: `/cores/`, `/tipografia/`, `/espacamentos/`, `/bordas/`.
> A página `/tokens/` está **depreciada** — não use os nomes antigos (`--color--primary`,
> `--text--medium`, `--space--sm`, `--border--radius-medium`). Eles ainda existem em telas legadas,
> mas o padrão novo é o desta página.

Estes são os valores reais publicados pelo time de Design System. Não são aproximação.
Use-os em: protótipo (`assets/acorde-base.css`), tela de extensão no frontend novo (`ez-*`/`snk-*`)
e dashboard/gadget HTML5 do BI.

---

## 1. Cores

### Ocean Green — cor de ação (marca)

Base: **Ocean Green 600 `#008561`**. É a única cor primária permitida.

| Token | Valor |
|---|---|
| `--color--ocean-green-1000` | `#00281D` |
| `--color--ocean-green-900` | `#003D2D` |
| `--color--ocean-green-800` | `#00523C` |
| `--color--ocean-green-700` | `#00684C` |
| `--color--ocean-green-600` | `#008561` |
| `--color--ocean-green-500` | `#1A9171` |
| `--color--ocean-green-400` | `#42A58A` |
| `--color--ocean-green-300` | `#6BB8A3` |
| `--color--ocean-green-200` | `#94CCBD` |
| `--color--ocean-green-100` | `#BDDFD6` |
| `--color--ocean-green-90` | `#E6F3EF` |

Uso: 700 para hover/pressed, 90 para fundo suave (chip, linha selecionada, botão terciário em hover).
As demais tonalidades servem para composição visual — **não** como cor de ação.

### Petroleum — neutro estrutural (texto, título, chrome)

| Token | Valor |
|---|---|
| `--color--petroleum-1000` | `#0D1119` |
| `--color--petroleum-900` | `#141B27` |
| `--color--petroleum-800` | `#1B2434` |
| `--color--petroleum-700` | `#222D42` |
| `--color--petroleum-600` | `#2B3A54` |
| `--color--petroleum-500` | `#404E65` |
| `--color--petroleum-400` | `#626D80` |
| `--color--petroleum-300` | `#848D9C` |
| `--color--petroleum-200` | `#A6ACB7` |
| `--color--petroleum-100` | `#C8CCD3` |
| `--color--petroleum-90` | `#EAEBEE` |
| `--color--petroleum-80` | `#F4F6F9` |
| `--color--petroleum-70` | `#F4F6F9` |

Uso: 600 = título e topbar/sidenav; 400 = texto secundário; 100/90 = bordas; 80 = fundo de página
e superfície alternada.

### Gray — neutro genérico

`--color--gray-1000 #060607` · `-900 #0B0C0E` · `-800 #111114` · `-700 #16171B` · `-600 #1C1D22` ·
`-500 #494A4E` · `-400 #77777A` · `-300 #A4A5A7` · `-200 #D2D2D3` · `-100 #DEDEDE` ·
`-90 #EAEAEA` · `-80 #F9F9F9` · `-70 #FFFFFF`

### Feedback de sistema

| Papel | Base | Escala |
|---|---|---|
| Sucesso | `--color--green-600 #157A00` | 1000 `#041800` · 900 `#083100` · 800 `#0D4900` · 700 `#116200` · 500 `#449533` · 400 `#73AF66` · 300 `#A1CA99` · 200 `#D0E4CC` · 100 `#EEF9EC` |
| Alerta | `--color--yellow-600 #EFB103` | 1000 `#302301` · 900 `#604701` · 800 `#8F6A02` · 700 `#BF8E02` · 500 `#F2C135` · 400 `#F5D068` · 300 `#F9E09A` · 200 `#FCEFCD` · 100 `#FAF7EE` |
| Erro | `--color--red-600 #BD0025` | 1000 `#260007` · 900 `#4C000F` · 800 `#710016` · 700 `#97001E` · 500 `#CA3351` · 400 `#D7667C` · 300 `#E599A8` · 200 `#F2CCD3` · 100 `#F9EBEE` |

Regras que a doc afirma explicitamente:

- Verde/amarelo/vermelho são **feedback de sistema**. Nunca use como cor de ação nem como cor de marca.
- Amarelo sobre fundo branco perde contraste — use o 700/800 para o texto e o 100/200 só como fundo.
- Sucesso não é verde da marca: `#157A00` (green) ≠ `#008561` (ocean green).

### Composição

- **20% cor de ação / 80% neutro.** 20% é o **teto**, não a meta.
- Fundos escuros: 10% a 20% da tela, no máximo.
- Só um verde protagonista: o da marca. Verde de feedback não compete com ele.

---

## 2. Tipografia

Fonte: **Roboto** (`--font--pattern`).

| Papel | Valor | Token |
|---|---|---|
| Texto de leitura | **14px** | `--font-size--default` |
| Título | **24px** | `--font-size--xxxlarge` |
| Escada de parágrafo | 8–20px | `--font-size--xxsmall` (8) … `--font-size--xlarge` (20) |
| Escada de título | 22–44px | `--font-size--xxlarge` (22) … `--font-size--13xlarge` (44) |

Outros tamanhos: 10 `xsmall`, 12 `small`, 16 `medium`, 18 `large`, 26 `4xlarge`, 28 `5xlarge`,
30 `6xlarge`, 32 `7xlarge`, 36 `9xlarge`, 40 `11xlarge`, 48 `15xlarge`. Vai até 120px.

Pesos: `--font-weight--regular 400` · `--medium 500` · `--semi-bold 600` · `--bold 700`.
Padrão de leitura = 400. Semi-bold é destaque pontual, nunca maioria do texto.

Altura de linha: tokens de `--line-height--16` a `--line-height--78` (passo de 2px até 60, depois
64/68/74/78). Não misture várias alturas na mesma tela.

Letter-spacing: `--letter-spacing--0/1/2` (0px, 1px, 2px).

O que a doc proíbe: texto de leitura fora de 14px; muitos tamanhos diferentes na mesma tela;
títulos coloridos variados.

---

## 3. Espaçamento

Tokens `--space--0` a `--space--52`, passo de 2px.

| Situação | Valor |
|---|---|
| Padrão geral (título↔parágrafo, ícone↔texto, entre botões) | **16** |
| Entre componentes | 16 a 24 (24 quando a tela parecer apertada) |
| Respiro lateral do conteúdo | 24 |
| Itens da mesma lista/navegação | 8 |
| Escada recomendada | 16 · 20 · 24 · 28 · 32 |

---

## 4. Border radius

Tokens `--border--radius-0` a `--border--radius-64`, mais `-100` e `-200`.

- **Padrão: 24px.** A doc diz literalmente para não mudar, salvo necessidade real.
- No máximo **duas** variações de raio no mesmo layout.
- Circular: `--border--radius-200`.

Para protótipo/tela densa de ERP, a combinação adotada é:
**24px em superfícies** (card, modal, painel, form) e **8px em controles** (botão, input, tag) —
duas variações, dentro da regra. Declare essa escolha ao entregar; não invente uma terceira.

---

## 5. Uso em CSS

```css
.elemento {
  background-color: var(--color--ocean-green-600);
  color: var(--color--petroleum-900);
  font-family: var(--font--pattern);
  font-size: var(--font-size--default);
  font-weight: var(--font-weight--regular);
  line-height: var(--line-height--24);
  padding: var(--space--8) var(--space--16);
  border-radius: var(--border--radius-24);
}
```

Em **tela de extensão** (frontend novo, `ez-*`/`snk-*`) os tokens já vêm do tema — só consuma
`var(--...)`. Em **protótipo** e **dashboard HTML5 do BI** não há tema carregado: declare os tokens
em `:root` você mesmo, com os valores desta página.

Nunca escreva hex solto no HTML/CSS. Se não existe token para o que você precisa, o problema é a
decisão de design, não o token faltando.

---

## 6. Componentes publicados

Para o mapa protótipo → implementação, estes são os componentes que existem de fato.

**EzUI (`ez-*`, genéricos):** actions-button, alert, alert-list, avatar, badge, breadcrumb, button,
calendar, card-item, chart, check, chip, classic-combo-box, classic-input, classic-text-area,
collapsible-box, combo-box, date-input, date-time-input, dialog, double-list, dropdown, empty-card,
file-item, filter-input, form, form-view, grid, grid-view, guide-navigator, icon, list, list-item,
modal, modal-container, multi-select-input, multi-selection-list, number-input, pagination, popover,
popover-plus, popup, progress-bar, radio-button, rich-text, scrim, scroller, search, search-plus,
sidebar-button, sidebar-navigator, skeleton, sortable-list, spinner, split-button, split-panel,
tabselector, tag, tag-input, text-area, text-edit, text-input, tile, tile-medium, time-input, toast,
tooltip, tree, underface, upload.

**Sankhya ERP (`snk-*`, acoplados à EIP/dicionário):** application, attach, crud, data-exporter,
data-unit, entity-list, filter-bar, filter-field-search, form, grid, layout-form-config,
message-builder, personalized-filter, pesquisa, print-selector, simple-bar, simple-crud,
simple-form-config, taskbar.

**Utilitários de layout:** box, content, flexbox-system, grid-system, icons, labels, margin, padding,
text, title.

`ez-button` — o que a API realmente aceita (não invente variante):

- `variant`: `primary` | `secondary` (default) | `tertiary`
- `size`: `x-small` | `small` | `medium` (default) | `large`
- `mode`: `regular` | `icon` | `label-icon` | `link`
- desabilitar: `isDisabled` (`true` acessível — recomendado; `"full"` bloqueia teclado).
  `enabled` está **depreciado**.
- ícone: `iconName` / `leftIconName` / `rightIconName`, da biblioteca `ez-icons`.
