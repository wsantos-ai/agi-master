# NOTAS-INDEX.md — Índice Central de Notas de Estudo

Tabela de todas as notas de estudo criadas, com fase, status, pré-requisitos e conexões com projetos práticos.

**Atualizar:** a cada nova nota criada ou revisada.

---

## Notas por Fase de Estudo

### Fase 1: Fundamentos (semanas 1-4)

| Conceito | Arquivo | Status | Fonte | Pré-requisitos | Avança Para | Projeto | Data |
|----------|---------|--------|-------|----------------|-------------|---------|------|
| Redes Neurais | [redes-neurais.md](notas/redes-neurais.md) | planejado | [F-001] | Cálculo básico | Backpropagation | — | — |
| Backpropagation | [backpropagacao.md](notas/backpropagacao.md) | planejado | [F-001] | Redes Neurais | Otimização | — | — |
| Descida de Gradiente | [descida-gradiente.md](notas/descida-gradiente.md) | planejado | [F-001] | Cálculo, Backprop | Otimização Avançada | — | — |
| Modelos de Linguagem Clássicos | [modelos-linguagem-classicos.md](notas/modelos-linguagem-classicos.md) | planejado | [F-002] | Probabilidade | n-gramas → LLMs | — | — |
| Transformer | [transformer.md](notas/transformer.md) | planejado | [F-004] | Redes Neurais | Atenção Multi-Cabeça | — | — |
| Atenção Multi-Cabeça | [atencao-multi-cabeca.md](notas/atencao-multi-cabeca.md) | planejado | [F-004] | Transformer | LLMs Modernos | — | — |
| Position Encoding | [position-encoding.md](notas/position-encoding.md) | planejado | [F-005], [F-007] | Transformer | RoPE → Contextos Longos | — | — |

---

### Fase 2: LLMs e Raciocínio em Linha (semanas 5-8)

| Conceito | Arquivo | Status | Fonte | Pré-requisitos | Avança Para | Projeto | Data |
|----------|---------|--------|-------|----------------|-------------|---------|------|
| Large Language Models (LLMs) | [llms-fundamentos.md](notas/llms-fundamentos.md) | planejado | [F-009] | Transformers | GPT-3 e Escalas | — | — |
| GPT-3: Few-Shot Learning | [gpt3-few-shot.md](notas/gpt3-few-shot.md) | planejado | [F-009] | LLMs Fundamentos | In-Context Learning | — | — |
| In-Context Learning | [in-context-learning.md](notas/in-context-learning.md) | planejado | [F-041], [F-042] | GPT-3 | Prompting Avançado | — | — |
| Emergent Abilities | [emergent-abilities.md](notas/emergent-abilities.md) | planejado | [F-011] | Escalas de LLM | Raciocínio Emergente | — | — |
| Chain-of-Thought (CoT) | [chain-of-thought.md](notas/chain-of-thought.md) | planejado | [F-013] | Emergent Abilities | Raciocínio Multi-Etapas | Proj 1 | — |
| Zero-Shot Reasoning | [zero-shot-reasoning.md](notas/zero-shot-reasoning.md) | planejado | [F-014] | CoT | Prompting Sem Exemplos | — | — |
| Self-Consistency | [self-consistency.md](notas/self-consistency.md) | planejado | [F-016] | CoT | Raciocínio Robusto | — | — |
| Tree of Thoughts | [tree-of-thoughts.md](notas/tree-of-thoughts.md) | planejado | [F-015] | CoT | Busca e Planejamento | Proj 2 | — |
| Least-to-Most Prompting | [least-to-most.md](notas/least-to-most.md) | planejado | [F-017] | CoT | Decomposição de Problemas | Proj 1 | — |
| Fine-Tuning e Adaptação | [fine-tuning.md](notas/fine-tuning.md) | planejado | [F-047], [F-048], [F-049] | LLMs Fundamentos | LoRA, DPO | — | — |
| LoRA: Low-Rank Adaptation | [lora.md](notas/lora.md) | planejado | [F-047] | Fine-Tuning | Adaptação Eficiente | — | — |

---

### Fase 3: Agentes e Tool Calling (semanas 9-13)

| Conceito | Arquivo | Status | Fonte | Pré-requisitos | Avança Para | Projeto | Data |
|----------|---------|--------|-------|----------------|-------------|---------|------|
| Agentes Autônomos | [agentes-autonomos.md](notas/agentes-autonomos.md) | planejado | CLAUDE.md | CoT, LLMs | ReAct, Tool Calling | Proj 2 | — |
| ReAct: Reasoning + Acting | [react-agentes.md](notas/react-agentes.md) | planejado | [F-018] | Agentes Autônomos | Tool Calling | Proj 2 | — |
| Tool Calling / Function Calling | [tool-calling.md](notas/tool-calling.md) | planejado | [F-022], [F-023], [F-024] | ReAct | Agentes com Ferramentas | Proj 1-3 | — |
| Toolformer: Self-Teaching Tools | [toolformer.md](notas/toolformer.md) | planejado | [F-022] | Tool Calling | Aprendizado Autônomo | — | — |
| Retrieval-Augmented Generation (RAG) | [retrieval-augmented-generation.md](notas/retrieval-augmented-generation.md) | planejado | [F-026] | Tool Calling, Embeddings | Vector Stores | Proj 1-2 | — |
| Dense Passage Retrieval (DPR) | [dense-passage-retrieval.md](notas/dense-passage-retrieval.md) | planejado | [F-027] | RAG | Recuperação Eficiente | — | — |
| Generative Agents (Memória + Planejamento) | [generative-agents.md](notas/generative-agents.md) | planejado | [F-019] | Agentes Autônomos | Sistemas de Memória | Proj 3 | — |
| Error Recovery em Agentes | [error-recovery-agentes.md](notas/error-recovery-agentes.md) | planejado | [F-035], pesquisa | ReAct, Backtracking | Robustez de Agentes | Proj 3 | — |
| 5 Princípios para Agentes Eficazes | [5-principios-agentes-eficazes.md](notas/5-principios-agentes-eficazes.md) | pronto | [B-018] | ReAct, Tool Calling | Arquitetura de Produção | Proj 1-4 | 2026-08-20 |

---

### Fase 4: Fronteiras de Pesquisa (semanas 14-20)

| Conceito | Arquivo | Status | Fonte | Pré-requisitos | Avança Para | Projeto | Data |
|----------|---------|--------|-------|----------------|-------------|---------|------|
| Planejamento em LLMs | [planejamento-llms.md](notas/planejamento-llms.md) | planejado | [F-029] | ReAct, Tree of Thoughts | Busca + Raciocínio | Proj 4 | — |
| Raciocínio de Longo Horizonte | [raciocinio-longo-horizonte.md](notas/raciocinio-longo-horizonte.md) | planejado | [F-015], [F-029] | Planejamento | Composição de Tarefas | Proj 4 | — |
| Composição e Generalização | [composicao-generalizacao.md](notas/composicao-generalizacao.md) | planejado | pesquisa | Agentes Autônomos | Capacidades Emergentes | — | — |
| Conhecimento Estruturado vs. Implícito | [conhecimento-estruturado.md](notas/conhecimento-estruturado.md) | planejado | [F-026], pesquisa | RAG | Hybrid Reasoning | — | — |
| Segurança de Agentes | [seguranca-agentes.md](notas/seguranca-agentes.md) | planejado | [F-032], [F-033], [F-034] | Tool Calling | Control de Agentes | Proj 3-4 | — |
| Interpretabilidade em Agentes | [interpretabilidade-agentes.md](notas/interpretabilidade-agentes.md) | planejado | [F-050], [F-051] | Mecanismos de Agentes | Debugging de Agentes | — | — |
| Escala Bruta vs. Teoria Nova | [escala-bruta-vs-teoria-nova.md](notas/escala-bruta-vs-teoria-nova.md) | aberta | [F-001], [F-053] | Deep Learning, Scaling Laws | Arquitetura Futura | Proj 4 | 2026-08-20 |
| AGI: Perspectivas e Limites | [agi-perspectivas.md](notas/agi-perspectivas.md) | planejado | [F-052] | Todas as fases | Pesquisa Futura | Proj 4 | — |

---

## Legenda de Status

- **planejado** — ainda não foi criada
- **rascunho** — criada, mas precisa de revisão (Teste Feynman)
- **revisado** — revisada e pronta para uso
- **pronto** — completa com exercícios e exemplos validados

---

## Estatísticas

- **Total de notas planejadas:** 68 (adicionada 1 pergunta aberta)
- **Notas criadas:** 2 (5 Princípios para Agentes Eficazes + Escala Bruta vs. Teoria Nova)
- **Notas revisadas:** 1 (pronto, com errata e exercícios)
- **Perguntas abertas:** 1 (Escala Bruta vs. Teoria Nova)
- **Cobertura por fase:** Fase 1 (0%), Fase 2 (0%), Fase 3 (1/8 = 12,5%), Fase 4 (1/8 = 12,5%)

*(Última atualização: 2026-08-20)*

---

## Como Usar Este Índice

1. **Encontrar nota:** busque por conceito ou arquivo
2. **Entender pré-requisitos:** coluna "Pré-requisitos" mostra o que estudar antes
3. **Sequência de estudo:** seguir de cima para baixo em cada fase
4. **Projetos:** coluna "Projeto" mostra qual projeto prático usa a nota
5. **Progresso:** coluna "Status" monitora cobertura do mestrado

---

## Fluxo: Do Resumo à Nota

```
1. Agente @book-summarizer cria resumo em resumos-livros/
   ↓
2. Você revisa resumo, testa Feynman
   ↓
3. Cria nota de estudo usando _template-nota.md
   ↓
4. Preenche exercícios, exemplos, conexões
   ↓
5. Testa Feynman novamente (✅ ou ❌)
   ↓
6. Se ✅: move para status "revisado" aqui
   ↓
7. Adiciona perguntas abertas ao MAPA-DA-IGNORANCIA.md
   ↓
8. Quando refinada: marca como "pronto"
```

---

## Template para Nova Nota

Quando adicionar nota ao índice:

```markdown
| [Conceito] | [arquivo.md](notas/arquivo.md) | planejado | [F-xx] | [Pré] | [Avança] | [Proj] | — |
```

Depois:
1. Crie arquivo em `notas/[arquivo].md` usando `_template-nota.md`
2. Desenvolva as 5 partes
3. Teste Feynman
4. Atualize status aqui

---

**Última atualização:** 2026-08-20  
**Responsável:** mestrado-agi-agentes  
**Template:** [_template-nota.md](notas/_template-nota.md)
