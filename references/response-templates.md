# Templates de Resposta — PLS Sankhya

> Use estes templates como base para respostas padronizadas. Adapte conforme o contexto real.

---

## Template: Revisão de microcopy (tabela completa)

| Contexto | Texto atual | Problema identificado | Versão recomendada | Alternativas | Racional de UX Writing | Observações / riscos |
|---|---|---|---|---|---|---|
| [módulo / componente / estado] | [texto exato atual] | [problema de clareza, consistência, tom, etc.] | [versão recomendada] | [opção B / opção C se houver] | [por que a versão recomendada é melhor] | [riscos de implementação, dependências, Rule IDs] |

---

## Template: Mensagem de erro

**Estrutura:**
> [O que aconteceu]. [Por que aconteceu, se útil.] [Como resolver.]

**Exemplos por tipo de erro:**

```
// Erro de validação de campo
"[Campo] é obrigatório. Preencha antes de salvar."

// Erro de conexão / sistema
"Não foi possível [ação]. Verifique sua conexão e tente novamente."

// Erro de permissão
"Você não tem permissão para [ação]. Fale com o administrador."

// Erro de regra de negócio
"Não é possível [ação] porque [condição]. [O que fazer]."

// Erro sem solução imediata
"Não foi possível [ação] agora. Nossa equipe foi notificada. Tente novamente em alguns minutos."
```

---

## Template: Empty state

**Estrutura:**
> Nenhum/a [entidade] [contexto]. [O que o usuário pode fazer agora.]

**Exemplos:**

```
// Filtro sem resultado
"Nenhum [entidade] encontrado com esses filtros. Ajuste os critérios ou limpe os filtros."

// Módulo novo
"Nenhum [entidade] cadastrado ainda. Crie o primeiro [entidade] para começar."

// Permissão insuficiente
"Você não tem acesso para ver este conteúdo. Fale com o administrador do sistema."

// Dados em processamento
"[Entidade] sendo carregada. Aguarde alguns instantes."
```

---

## Template: Modal de confirmação de ação destrutiva

**Título:** [Verbo] [entidade] [identificador]?  
**Corpo:** Esta ação [consequência específica]. [O que mais será afetado, se relevante.]  
**CTA primário:** [Verbo] [entidade]  
**CTA secundário:** Cancelar

**Exemplo:**
> **Excluir pedido #4521?**  
> Esta ação não pode ser desfeita. Os itens vinculados também serão removidos.  
> [Excluir pedido] [Cancelar]

---

## Template: Turn de agente BIA

**Resposta padrão a intenção identificada:**
> "Encontrei [resultado]. [Resumo do que foi feito ou do que está disponível]. Quer que eu [próxima ação sugerida]?"

**Resposta com incerteza:**
> "Com base nas informações disponíveis, [resultado provável]. Revise antes de confirmar."

**Repair leve:**
> "Entendi que você quer [interpretação]. É isso mesmo?"

**Repair médio:**
> "Não tenho certeza do que você precisa. Você quer: [opção A] ou [opção B]?"

**Repair pesado / fallback:**
> "Não consegui identificar o que você precisa neste caso. Você pode reformular? Se preferir, posso conectar você com o suporte."

---

## Template: CTA por contexto

| Contexto | CTA primário | CTA secundário |
|---|---|---|
| Salvar formulário novo | Criar [entidade] | Cancelar |
| Salvar formulário editado | Salvar alterações | Descartar |
| Confirmar ação crítica | [Verbo] [entidade] | Cancelar |
| Enviar para fluxo | Enviar para aprovação | Salvar rascunho |
| Excluir | Excluir [entidade] | Cancelar |
| Publicar | Publicar | Revisar |

---

## Template: Padrão para o PLS

```
## [Nome do padrão]

**Objetivo:** [Uma frase descrevendo o propósito]

**Quando usar:**
- [Contexto 1]
- [Contexto 2]

**Quando não usar:**
- [Exceção 1]
- [Exceção 2]

**Regra de escrita:**
[Estrutura ou fórmula de redação]

**Exemplos recomendados:**
- "[Exemplo 1]"
- "[Exemplo 2]"

**Exemplos a evitar:**
- "[Exemplo ruim 1]" → [por que é ruim]
- "[Exemplo ruim 2]" → [por que é ruim]

**Critérios de qualidade:**
- [ ] [Critério 1]
- [ ] [Critério 2]

**Relação com componentes:** [Lista de componentes afetados]

**Observações:**
- Produto: [impacto ou ação necessária]
- Design: [impacto ou ação necessária]
- Engenharia: [impacto ou ação necessária]
```
