# Árvore de Decisão — UX Writing Sankhya

> Use este guia rápido para decidir qual padrão aplicar sem precisar consultar o PLS completo.

---

## 1. Qual é o tipo de texto?

```
Texto de interface
├── Ação do usuário → CTA
├── Nome de campo ou dado → Label
├── Explicação complementar → Tooltip
├── Tela sem conteúdo → Empty state
├── Resultado de operação → Notificação / Toast
├── Problema ocorrido → Mensagem de erro
├── Decisão com consequência → Modal de confirmação
└── Orientação de contexto → Título / Descrição

Texto de agente (BIA / BIA Escreve)
├── Resposta a intenção → Turn canônico
├── Não entendeu → Repair (ver pls-core.md)
├── Ação irreversível → Confirmação obrigatória
├── Inferência → Indicar confiança, não afirmar
└── Limite de capacidade → Fallback + escalação

Texto de documentação
├── Instrução passo a passo → Procedimento
├── Explicação de conceito → Artigo de ajuda
├── O que mudou → Release notes
└── Referência técnica → Documentação de API / campo
```

---

## 2. Qual é o estado da interface?

| Estado | O que considerar |
|---|---|
| Fluxo feliz | Texto padrão, orientado à ação |
| Erro | Estrutura: o que foi + por que + como resolver |
| Vazio | Estrutura: o que não existe + o que fazer |
| Carregando | Texto informativo, sem criar ansiedade |
| Bloqueado | Explicar a restrição + próximo passo possível |
| Sucesso | Confirmação breve + próximo passo (quando relevante) |
| Parcial | Indicar o que foi feito e o que falta |

---

## 3. Qual é o perfil do usuário?

| Perfil | Ajuste de linguagem |
|---|---|
| Operador | Direta, tarefa específica, sem jargão |
| Gestor | Resumida, orientada a resultado |
| Controller | Técnica, precisa, sem ambiguidade contábil/fiscal |
| TI / Implantador | Técnica, estruturada, com contexto de configuração |
| Executivo | Objetiva, orientada a negócio, sem detalhes técnicos |

---

## 4. Checklist rápido antes de aprovar o texto

- [ ] O texto informa o que aconteceu / acontece / vai acontecer?
- [ ] O texto orienta a próxima ação?
- [ ] O texto usa o termo canônico do PLS?
- [ ] O texto funciona sem o contexto visual (cor, ícone, posição)?
- [ ] O texto evita culpar o usuário?
- [ ] O texto não promete o que o sistema não garante?
- [ ] O texto pode ser traduzido sem perda de sentido?
- [ ] Se o texto é para IA: indica incerteza quando necessário?

---

## 5. Referências rápidas por arquivo

| Preciso de… | Arquivo |
|---|---|
| Estrutura de erros, empty states, tooltips, CTAs | `references/pls-patterns.md` |
| Tom, voz, matriz de contexto, acessibilidade | `references/pls-voice-tone.md` |
| Glossário, verbos canônicos, estados, módulos | `references/pls-terminology.md` |
| Rule IDs, guardrails, ICU MessageFormat, BIA | `references/pls-core.md` |
