# RESUMOS-INDEX.md — Índice Central de Resumos

Tabela de todos os resumos de livros e papers gerados pelo agente `@book-summarizer`, com rastreamento de status, nota de estudo gerada, e conexões com Mapa da Ignorância.

**Atualizar:** a cada novo resumo gerado.

---

## Resumos por Fase de Estudo

### Fase 1: Fundamentos (semanas 1-4)

| [F-xx] | Livro/Paper | Capítulo/Seção | Resumo | Nota Gerada | Status | Data | Perguntas Abertas |
|--------|------------|----------------|--------|------------|--------|------|-------------------|
| F-001 | Deep Learning (Goodfellow et al.) | Cap. 1: Introdução | [resumo](resumos-livros/[F-001]_deep-learning/cap-01-introducao.md) | — | planejado | — | — |
| F-001 | Deep Learning (Goodfellow et al.) | Cap. 2: Redes Neurais | [resumo](resumos-livros/[F-001]_deep-learning/cap-02-redes-neurais.md) | — | planejado | — | — |
| F-001 | Deep Learning (Goodfellow et al.) | Cap. 3: Backpropagation | [resumo](resumos-livros/[F-001]_deep-learning/cap-03-backpropagacao.md) | [nota](notas/backpropagacao.md) | planejado | — | — |
| F-004 | Attention Is All You Need | Seções 1-3 (Arquitetura) | [resumo](resumos-livros/[F-004]_attention-is-all-you-need/resumo-completo.md) | — | planejado | — | — |

---

### Fase 2: LLMs e Raciocínio em Linha (semanas 5-8)

| [F-xx] | Livro/Paper | Capítulo/Seção | Resumo | Nota Gerada | Status | Data | Perguntas Abertas |
|--------|------------|----------------|--------|------------|--------|------|-------------------|
| F-009 | Language Models are Few-Shot Learners | Completo (GPT-3) | [resumo](resumos-livros/[F-009]_gpt3/resumo-completo.md) | — | planejado | — | — |
| F-011 | Emergent Abilities of LLMs | Seções 1-2 | [resumo](resumos-livros/[F-011]_emergent-abilities/resumo-completo.md) | — | planejado | — | — |
| F-013 | Chain-of-Thought Prompting | Completo | [resumo](resumos-livros/[F-013]_cot-prompting/resumo-completo.md) | [nota](notas/chain-of-thought.md) | planejado | — | — |

---

### Fase 3: Agentes e Tool Calling (semanas 9-13)

| [F-xx] | Livro/Paper | Capítulo/Seção | Resumo | Nota Gerada | Status | Data | Perguntas Abertas |
|--------|------------|----------------|--------|------------|--------|------|-------------------|
| F-018 | ReAct: Synergizing Reasoning and Acting | Completo | [resumo](resumos-livros/[F-018]_react/resumo-completo.md) | [nota](notas/react-agentes.md) | planejado | — | — |
| F-022 | Toolformer | Completo | [resumo](resumos-livros/[F-022]_toolformer/resumo-completo.md) | — | planejado | — | — |
| F-026 | Retrieval-Augmented Generation | Seções 1-3 | [resumo](resumos-livros/[F-026]_rag/resumo-completo.md) | [nota](notas/retrieval-augmented-generation.md) | planejado | — | — |

---

### Fase 4: Fronteiras de Pesquisa (semanas 14-20)

| [F-xx] | Livro/Paper | Capítulo/Seção | Resumo | Nota Gerada | Status | Data | Perguntas Abertas |
|--------|------------|----------------|--------|------------|--------|------|-------------------|
| F-015 | Tree of Thoughts | Completo | [resumo](resumos-livros/[F-015]_tree-of-thoughts/resumo-completo.md) | — | planejado | — | — |
| F-029 | Language Models as Zero-Shot Planners | Completo | [resumo](resumos-livros/[F-029]_llm-planners/resumo-completo.md) | — | planejado | — | — |

---

## Legenda de Status

- **planejado** — ainda não foi resumido
- **resumo bruto** — agente criou resumo, ainda precisa revisar
- **revisado** — resumo revisado e validado
- **nota pronta** — nota de estudo criada em `/notas/`
- **completo** — resumo + nota + Mapa atualizado

---

## Como Usar Este Índice

1. **Encontrar resumo:** busque por [F-xx] (índice FONTES.md) ou título do livro
2. **Rastrear progresso:** coluna "Status" mostra o que falta fazer
3. **Conectar com notas:** coluna "Nota Gerada" aponta para a nota de estudo final
4. **Ver perguntas abertas:** coluna "Perguntas Abertas" linka para MAPA-DA-IGNORANCIA.md

---

## Fluxo: Resumo → Nota de Estudo

```
1. Agente @book-summarizer cria resumo bruto
   ↓
2. Você revisa, testa Feynman
   ↓
3. Se passou: move para "revisado"
   ↓
4. Cria nota de estudo (usando resumo como base)
   ↓
5. Nota vai para /notas/ e é listada em NOTAS-INDEX.md
   ↓
6. Perguntas abertas vão para MAPA-DA-IGNORANCIA.md
   ↓
7. Marca como "completo" aqui
```

---

## Estatísticas

- **Total de livros/papers:** [planejado: múltiplos / resumido: 0 / completo: 0]
- **Notas de estudo geradas:** 0
- **Perguntas abertas criadas:** 0

*(Atualizar conforme avança no mestrado)*

---

## Template para Novo Resumo

Quando adicionar novo resumo:

```markdown
| [F-xxx] | [Título] | [Capítulo/Seção] | [link-resumo] | [link-nota ou —] | planejado | — | — |
```

Depois:
1. Crie pasta em `resumos-livros/[F-xxx]_[kebab-case-livro]/`
2. Gere resumo usando template em `resumos-livros/_template-resumo.md`
3. Atualize esta tabela

---

**Última atualização:** 2026-08-20  
**Responsável:** mestrado-agi-agentes
