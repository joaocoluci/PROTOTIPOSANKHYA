# Checklist de entrega do protótipo

Rode antes de declarar o protótipo pronto. Item reprovado = protótipo não entregue.

## Conteúdo (PLS)

- [ ] Título responde onde o usuário está e qual trabalho ele faz na tela
- [ ] Descrição complementa o título, sem repeti-lo, em no máximo 2 linhas
- [ ] CTA primário usa verbo canônico do PLS + objeto específico ("Criar pedido", não "OK")
- [ ] Existe **um só** CTA primário na tela
- [ ] Labels usam o termo do domínio do usuário, não o nome do campo no banco (PLS-DATA-001)
- [ ] Nenhuma sigla sem apresentação prévia
- [ ] Terminologia consistente com o glossário (`references/pls-terminology.md`) — sem variação para o mesmo conceito
- [ ] Situações usam os estados canônicos (Rascunho, Aguardando aprovação, Aprovado, Rejeitado, Cancelado, Concluído, Parcial, Bloqueado, Em processamento)
- [ ] Mensagem de erro traz o que aconteceu + por que + como resolver
- [ ] Nenhum texto culpa o usuário
- [ ] Empty state orienta a próxima ação
- [ ] Tooltip (se houver) não está consertando um label ruim
- [ ] Confirmação destrutiva repete a entidade no CTA e explica a consequência
- [ ] Nenhuma promessa que o sistema não garante (prazo, automação, IA)
- [ ] Texto funciona sem o contexto visual (sem cor, sem ícone, sem posição)
- [ ] Nenhum "lorem ipsum" ou placeholder genérico sobrou

## Estrutura e estados

- [ ] Todos os estados aplicáveis existem: padrão, vazio, filtro sem resultado, carregando, erro, bloqueado, parcial, sucesso
- [ ] Estado não aplicável foi **justificado**, não apenas omitido
- [ ] Filtros continuam visíveis no estado de filtro sem resultado
- [ ] Erro de validação aparece no campo, não só no topo do formulário
- [ ] Carregamento usa esqueleto com a forma do conteúdo real
- [ ] Formulário longo tem rodapé de ação fixo

## Design System

- [ ] Só classes do `acorde-base.css`; nenhum valor mágico de cor, espaçamento ou raio no HTML
- [ ] Tipografia Roboto carregada; texto de leitura em 14px e título em 24px
- [ ] Ocean Green (`#008561`) é a única cor de ação, e ocupa no máximo ~20% da tela
- [ ] Verde/amarelo/vermelho só em feedback de sistema — nunca em botão de ação
- [ ] No máximo duas variações de raio (24 em superfície, 8 em controle)
- [ ] Situação comunicada por **texto**, não apenas por cor
- [ ] Campo com label visível (placeholder não substitui label)
- [ ] Máximo de 2 níveis de navegação interna
- [ ] Valores numéricos alinhados à direita

## Técnico

- [ ] Arquivo único: CSS embutido inline, sem dependência externa além da fonte
- [ ] Abre no navegador e renderiza — **verificado**, não presumido
- [ ] Seletor de estados funciona e alterna todos os blocos
- [ ] Sem emoji ou glifo Unicode cru (a plataforma pode servir como ISO-8859-1)
- [ ] Comentários explicam o porquê das decisões de UI
- [ ] Todo ponto pendente marcado com `<!-- TODO: ... -->`

## Fechamento da resposta

- [ ] Caminho do arquivo informado
- [ ] Tabela de microcopy (elemento · estado · texto · Rule ID) entregue
- [ ] Mapa protótipo → implementação real entregue, com serviços marcados como existentes ou `TODO`
- [ ] Suposições declaradas de forma explícita
- [ ] Dados fictícios identificados como fictícios
- [ ] Riscos de implementação citados quando o alvo for Design System em addon
