# Workflow de Prototipação — Telas Sankhya

> Detalhamento das Etapas 1, 3 e 5 do `SKILL.md`.

---

## 1. Questionário de briefing

Pergunte em **uma rodada só**, apenas o que não foi informado. Para tudo que não vier resposta,
assuma o default e **declare a suposição no início da entrega**.

### Obrigatórias (sem isso não há protótipo confiável)

1. **Módulo e entidade** — Comercial/Pedido de venda, Financeiro/Conta a pagar, Estoque/Movimentação…
   Define a terminologia canônica (ver `pls-terminology.md`) e as personas prováveis.
2. **Objetivo do usuário na tela** — "aprovar pedidos represados", "cadastrar um novo cliente com
   validação fiscal", "acompanhar saldo de estoque por lote". Define título, hierarquia e CTA primário.

### Importantes (com default declarado)

3. **Persona** — default `Operador`. Ajusta densidade de informação e nível de jargão.
4. **Arquétipo de tela** — default inferido do objetivo (ver seção 2 abaixo).
5. **Origem dos dados** — tabela/campos reais (validar via MCP `sankhya-schema`) ou fictícios.
   Default: fictícios coerentes com o domínio, marcados como fictícios na entrega.

### Opcionais (só pergunte se o pedido sugerir que importam)

6. Restrições de permissão (quem vê o quê) — gera o estado "bloqueado".
7. Integrações ou serviços já existentes — evita prometer o que não existe.
8. Volume esperado de registros — define paginação, filtros e se a grade precisa de virtualização.
9. Se a tela é filha/derivada de uma tela nativa do ERP — muda o padrão de navegação.
10. Multi-idioma no roadmap — se sim, todo texto dinâmico já sai em ICU MessageFormat (ver `pls-core.md`).

---

## 2. Arquétipos de tela do ERP

Escolha um. Combinações existem, mas o protótipo deve ter **um** propósito dominante.

| Arquétipo | Quando usar | Blocos obrigatórios | CTA primário típico |
|---|---|---|---|
| **Listagem / consulta** | usuário procura e analisa registros | filtros, grade, paginação, ações em lote | "Criar [entidade]" |
| **CRUD completo** | listagem + edição na mesma tela | grade + formulário lateral ou modal | "Salvar alterações" |
| **Formulário de cadastro** | criar/editar uma entidade | seções agrupadas, validação por campo, rodapé fixo | "Criar [entidade]" |
| **Wizard / assistente** | fluxo longo com etapas dependentes | indicador de etapas, navegação anterior/próximo, resumo final | "Concluir [processo]" |
| **Detalhe (visão 360º)** | consultar tudo de um registro | cabeçalho com identificação + situação, abas, timeline | "Editar [entidade]" |
| **Aprovação / alçada** | decisão sobre itens pendentes | fila, contexto da decisão, justificativa, ações em lote | "Aprovar" + "Rejeitar" |
| **Painel operacional** | acompanhar operação em tempo quase real | cartões de indicador, alertas, lista priorizada | ação sobre o item crítico |
| **Dashboard analítico** | analisar desempenho por período | filtros globais, gráficos, tabela de apoio, drill-down | "Exportar" ou drill-down |
| **Configuração / parâmetros** | ajustar comportamento do sistema | seções com descrição de impacto, alternâncias | "Salvar configurações" |
| **Importação / processamento** | subir arquivo e acompanhar processamento | upload, pré-visualização, log de erros por linha | "Importar [entidade]" |
| **Portal / autoatendimento** | usuário externo (cliente, fornecedor) | linguagem menos técnica, poucos campos, muito estado | varia |

**Regra de hierarquia:** uma tela = um CTA primário. Todo o resto é secundário ou terciário.
Se aparecerem dois CTAs primários concorrentes, a tela está fazendo duas coisas — questione o escopo.

---

## 3. Matriz de estados (Etapa 5 — obrigatória)

Todo protótipo entrega estes estados. Se algum não se aplica, **diga por quê** em vez de omitir.

| Estado | O que mostrar | Padrão de texto | Erro comum |
|---|---|---|---|
| **Padrão** | tela com dados representativos (5–8 linhas, valores plausíveis) | microcopy final | dados irreais que escondem problema de layout |
| **Vazio — nunca houve dado** | ilustração/ícone neutro + orientação | "Nenhum [entidade] cadastrado ainda. Crie o primeiro [entidade] para começar." | "Sem dados." |
| **Vazio — filtro sem resultado** | manter os filtros visíveis | "[Entidade] não encontrada com esses filtros. Ajuste os critérios ou limpe os filtros." | limpar os filtros junto com a mensagem |
| **Carregando** | esqueleto (skeleton) com a forma do conteúdo real | "Carregando [entidade]." (só se demorar) | spinner genérico no meio da tela |
| **Erro de validação** | mensagem **no campo**, não só no topo | "[Campo] é obrigatório. Preencha antes de salvar." | resumo genérico no topo do formulário |
| **Erro de sistema** | bloco de erro com próximo passo | "Não foi possível [ação]. Verifique sua conexão e tente novamente." | "Erro inesperado." |
| **Bloqueado / sem permissão** | tela com contexto, ação desabilitada e motivo | "Você não tem acesso para ver este conteúdo. Fale com o administrador do sistema." | esconder a tela sem explicar |
| **Parcial** | o que foi feito e o que falta | "12 de 15 pedidos importados. 3 linhas com erro precisam de correção." | dizer só "concluído" |
| **Sucesso** | confirmação breve + próximo passo quando útil | "Pedido salvo com sucesso." | toast de sucesso com 3 linhas |
| **Processando (assíncrono)** | estado do processo + o que o usuário pode fazer enquanto isso | "Sincronização em andamento. Os dados serão atualizados em instantes." | travar a tela sem informar |

Consulte `pls-patterns.md` para a estrutura completa de cada componente e `pls-voice-tone.md`
para calibrar o tom por contexto.

---

## 4. Densidade e hierarquia da informação

ERP é software de trabalho repetitivo. Densidade alta é **desejável** — desde que hierarquizada.

- Coluna mais importante à esquerda; valores monetários alinhados à direita; datas em formato curto.
- Situação sempre visível como `sk-tag`, com **texto** (não apenas cor) — acessibilidade.
- Ações de linha: no máximo 2 visíveis + menu "mais ações". Ação destrutiva nunca fica visível na linha
  sem confirmação.
- Formulário: agrupe por afinidade de negócio, não pela ordem das colunas do banco.
- Campo obrigatório marcado no label, não só na validação.
- Rodapé de ação fixo em formulário longo — o usuário não deve rolar para achar "Salvar".
- Máximo de 2 níveis de navegação dentro da tela (abas + seções). Mais que isso, quebre a tela.

---

## 5. Perguntas que o protótipo precisa responder ao ser aberto

Antes de entregar, verifique se alguém que abre a tela pela primeira vez consegue responder:

1. Onde eu estou? (título + navegação)
2. O que essa tela faz por mim? (descrição, 1–2 linhas)
3. O que eu vejo? (dados, com labels no vocabulário do usuário)
4. O que eu posso fazer agora? (CTA primário evidente)
5. O que acontece se eu errar? (estados de erro e confirmação)
6. Por que estou impedido? (quando bloqueado)

Se alguma resposta depender de explicação verbal fora da tela, a tela ainda não está pronta.

---

## 6. Mapeamento para implementação

O protótipo termina com uma tabela **protótipo → implementação real** (detalhes em
`design-system-acorde.md`), indicando para cada bloco:

- o componente real correspondente (`ez-*`, `snk-*` ou `sk-*`);
- o serviço de backend necessário e se ele já existe (senão, `TODO`);
- a entidade/campos do dicionário envolvidos;
- riscos conhecidos (permissão, volume, integração, sessão).

Isso é o que transforma o protótipo em insumo direto para `sankhya-frontend-design-system`,
`sankhya-js` ou `sankhya-backend-dev`.
