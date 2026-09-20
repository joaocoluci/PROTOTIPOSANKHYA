# PLS Voz e Tom — Referência Canônica

> Fonte: Product Language System v2.0 Sankhya — Domínio `/core`  
> Leia este arquivo quando a tarefa envolver calibragem de tom, revisão de voz ou criação de textos para novos contextos.

---

## Voz Sankhya

A voz Sankhya é **única** — não muda entre módulos, canais ou produtos.  
O **tom** varia conforme o contexto (ver tabela abaixo).

**A voz é:**
- Profissional, sem ser fria
- Clara, sem ser simplista
- Confiável, sem ser arrogante
- Objetiva, sem ser mecânica
- Técnica quando necessário, acessível sempre

**A voz não é:**
- Promocional
- Entusiasmada demais
- Informal ou coloquial
- Vaga ou evasiva
- Intimidadora ou autoritária

---

## Matriz de tom por contexto

| Contexto | Tom | Exemplo |
|---|---|---|
| Sucesso de ação | Confirmativo, breve, neutro | "Pedido salvo com sucesso." |
| Erro crítico/bloqueante | Direto, orientador, sem culpa | "Não foi possível processar o pagamento. Verifique os dados bancários e tente novamente." |
| Aviso / alerta | Informativo, preciso, sem alarme | "Este lote vence em 7 dias. Revise antes de confirmar o pedido." |
| Onboarding | Orientador, acolhedor, objetivo | "Comece cadastrando seus clientes para criar os primeiros pedidos." |
| Vazio / sem dados | Útil, não desanimador | "Nenhum pedido encontrado com esses filtros. Ajuste ou crie um novo." |
| Confirmação de ação irreversível | Sério, preciso, sem drama excessivo | "Esta ação não pode ser desfeita. Deseja continuar?" |
| Agente de IA (BIA) | Conversacional, profissional, transparente | "Encontrei 3 fornecedores com condições semelhantes. Quer que eu compare?" |
| Documentação técnica | Neutro, estruturado, passo a passo | "Para emitir uma NF-e, acesse Faturamento > Notas Fiscais > Nova NF-e." |
| Comunicação interna / Produto | Objetivo, direto, sem jargão desnecessário | "O fluxo de aprovação de pedidos foi atualizado. Veja o que mudou." |

---

## O que o texto deve fazer — e não fazer

### Deve:
- Ajudar o usuário a completar a tarefa
- Informar o suficiente para a próxima ação
- Usar o vocabulário do domínio do usuário (não do banco de dados)
- Ser consistente com o que já existe no produto
- Funcionar fora do contexto visual ideal (acessibilidade, leitor de tela)

### Não deve:
- Culpar o usuário por erros
- Usar humor em contextos críticos
- Prometer o que o sistema não garante
- Criar expectativas falsas sobre IA ou automação
- Usar termos internos que o usuário não reconhece
- Variar terminologia sem justificativa

---

## Anglicismos — Política do PLS

Use português quando houver equivalente claro e estabelecido.  
Use o termo em inglês quando ele for o termo canônico do domínio e a tradução gere estranhamento.

| Termo | Decisão | Justificativa |
|---|---|---|
| Dashboard | Aceito | Não há equivalente consolidado no contexto de produto |
| Workflow | Evitar → usar "fluxo" | Equivalente claro em PT-BR |
| Status | Aceito em contextos técnicos; prefira "situação" em UI | "Situação" é mais acessível para usuários não técnicos |
| Deploy | Evitar em UI → usar "publicar" ou "ativar" | Contexto técnico interno |
| Feedback | Aceito | Consolidado no vocabulário corporativo |
| Submit | Evitar → usar o verbo da ação específica | "Enviar", "Salvar", "Confirmar" conforme o contexto |
| Input | Evitar em UI → usar "campo" | Mais claro para o usuário final |
| Label | Aceito em contexto técnico/design | Em UI visível ao usuário, use "rótulo" ou o nome do campo |

---

## Acessibilidade de linguagem

Considere sempre:
- Clareza para leitura por leitores de tela (não dependa de contexto visual)
- Instruções sem dependência de cor ("o botão vermelho" não funciona sem visão)
- Contraste semântico entre estados: erro ≠ aviso ≠ sucesso ≠ bloqueio
- Textos alternativos descritivos para ícones funcionais
- Labels visíveis (não apenas placeholders) em campos de formulário
- Mensagens de erro vinculadas ao campo correto, não apenas ao topo do formulário

---

## Internacionalização

Escreva pensando em tradução desde o início:

**Evite:**
- Expressões idiomáticas ("mão na roda", "dar um puxão de orelha")
- Metáforas culturais
- Frases muito longas (>20 palavras em UI)
- Ambiguidades e duplo sentido
- Concatenação de strings: `"Olá, " + nome + "!"` — use ICU MessageFormat
- Dependência de gênero gramatical quando possível
- Abreviações sem padrão internacional

**Prefira:**
- Estruturas diretas e sem metáfora
- ICU MessageFormat para variáveis, plural e gênero
- Textos modulares que não dependam de ordem de palavras de uma língua específica

---

## Microcopy — Critérios de qualidade

Antes de aprovar qualquer microcopy, verifique:

- [ ] Informa o suficiente para o usuário agir
- [ ] Evita ambiguidade
- [ ] Usa termos consistentes com o PLS
- [ ] Não depende de conhecimento interno da Sankhya
- [ ] Não exige leitura longa no contexto do componente
- [ ] Funciona fora do contexto ideal (sem a tela, sem a cor, sem o ícone)
- [ ] Pode ser traduzido sem perda de sentido
- [ ] Evita expressões idiomáticas
- [ ] É compatível com acessibilidade textual
- [ ] Não cria expectativa falsa sobre automação, IA ou tempo de execução
