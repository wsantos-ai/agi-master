# 🚀 Mestrado em AGI & Raciocínio em Agentes + Ferramentas

**Diário de Estudos Estruturado:** Entendimento verificável sobre como LLMs integrados com ferramentas conseguem raciocínio complexo e caminham em direção a AGI.

---

## 🎯 Comece Aqui

1. **[CLAUDE.md](CLAUDE.md)** — Instruções mestrado, persona, princípios (leia primeiro!)
2. **[ESTRUTURA-DO-PROJETO.md](ESTRUTURA-DO-PROJETO.md)** — Organização de arquivos e fluxo de trabalho
3. **[FONTES.md](FONTES.md)** — Índice de papers, livros, documentação (58 fontes catalogadas)
4. **[MAPA-DA-IGNORANCIA.md](MAPA-DA-IGNORANCIA.md)** — Perguntas abertas que dirigem o estudo

---

## 📚 Estrutura

```
Arquivos Centrais:
├── CLAUDE.md                    ← Instruções (leia primeiro!)
├── ESTRUTURA-DO-PROJETO.md      ← Organização e fluxo
├── FONTES.md                    ← 58 papers/livros catalogados
├── MAPA-DA-IGNORANCIA.md        ← Perguntas abertas (importante!)
├── LINHA-DO-TEMPO.md            ← Marcos históricos
├── BENCHMARK-LOG.md             ← Resultados de experimentos

Índices:
├── RESUMOS-INDEX.md             ← Resumos de livros (status + notas geradas)
├── NOTAS-INDEX.md               ← Notas de estudo (fase, pré-req, projetos)

Pasta resumos-livros/:
├── Resumos didáticos por livro [F-xx]
├── Template: _template-resumo.md

Pasta notas/:
├── Notas de estudo (5 partes da aula)
├── Template: _template-nota.md
├── ~40 notas planejadas (de redes neurais a AGI)

Pasta projetos/:
├── Projeto 1: Agente de Diagnóstico
├── Projeto 2: Pesquisa Literária
├── Projeto 3: Error Recovery
├── Projeto 4: Experimento de Pesquisa

Subagentes:
├── .claude/agents/book-summarizer.md ← Resumidor automático
```

---

## 📖 Sequência de Estudo

### **Fase 1: Fundamentos** (semanas 1-4)
Redes neurais, backpropagation, Transformers, atenção.  
**Critério:** Explicar por que atenção multi-cabeça supera alternativas.

### **Fase 2: LLMs e Raciocínio** (semanas 5-8)
GPT-3, emergência, Chain-of-Thought, in-context learning, fine-tuning.  
**Critério:** Prever se CoT ou one-shot resolve problema novo.

### **Fase 3: Agentes e Ferramentas** (semanas 9-13)
ReAct, tool calling, RAG, memória, erro e recuperação.  
**Critério:** Desenhar arquitetura de agente com justificativa.

### **Fase 4: Fronteiras** (semanas 14-20)
Planejamento, longo horizonte, segurança, AGI, questões em aberto.  
**Critério:** Identificar lacuna e propor experimento.

---

## 🤖 Agente Especializado

**@book-summarizer** — Resuma livros e capítulos seguindo Técnica Feynman.

```
Uso: @book-summarizer Resuma o Cap 3 de "Deep Learning" sobre backpropagation
```

Output: Resumo didático (metadados, conceitos, exemplos, perguntas abertas) pronto para gerar nota de estudo.

---

## ✨ Princípios

### Rigor
- Nenhuma afirmação sem fonte `[F-xx]`
- Marcadores obrigatórios: `[confirmado]`, `[hipótese]`, `[em debate]`
- Datas absolutas sempre
- Teste Feynman valida aprendizado

### Didática
- 5 partes de aula: abertura, explicação, exemplos, exercícios, resumo
- Analogias com limites declarados
- Humor quando liga ao mundo real (nunca esconde lacuna)
- Linguagem acessível (8ª série) mesmo em tópicos complexos

### Aplicação
- 4 projetos práticos (Projetos 1-4)
- Código executável, resultados rastreados
- Feedback loop: teoria → prática → volta para teoria

---

## 📊 Fluxo: Leitura → Resumo → Nota → Projeto

```
1. Adicione livro/paper em FONTES.md [F-xxx]
   ↓
2. Leia e chame @book-summarizer
   ↓
3. Agente cria resumo em resumos-livros/
   ↓
4. Revise, teste Feynman
   ↓
5. Crie nota em notas/ (5 partes + exercícios)
   ↓
6. Teste Feynman novamente ✅ ou ❌
   ↓
7. Perguntas abertas → MAPA-DA-IGNORANCIA
   ↓
8. Use em Projeto 1-4 (Fase 3+)
   ↓
9. Registre resultados em BENCHMARK-LOG
```

---

## 🎓 Método: Técnica Feynman

**Teste de qualidade aplicado em toda nota:**

- [ ] Consigo explicar SEM ler o original?
- [ ] Um novato consegue entender?
- [ ] Consegui inventar novo exemplo?
- [ ] As 3-4 frases resumem 80%?

**Se falha em qualquer:** Reescreva. Não é perfeccionismo — é detector de lacunas.

---

## 🔍 Ferramentas

| Arquivo | Uso | Atualizar |
|---------|-----|-----------|
| **FONTES.md** | Índice de papers/livros | Antes de ler qualquer coisa nova |
| **RESUMOS-INDEX.md** | Status de resumos | Quando termina um resumo |
| **NOTAS-INDEX.md** | Status de notas | Quando cria/revisa nota |
| **MAPA-DA-IGNORANCIA.md** | Perguntas abertas | Ao encontrar lacuna no conhecimento |
| **BENCHMARK-LOG.md** | Resultados práticos | Ao testar agente/arquitetura |
| **LINHA-DO-TEMPO.md** | Marcos históricos | Quando identifica marco relevante |

---

## 🚀 Primeiro Passo

```bash
1. Leia CLAUDE.md
2. Leia ESTRUTURA-DO-PROJETO.md
3. Escolha primeiro paper de Fase 1 (ex: F-004 Attention Is All You Need)
4. Chame: @book-summarizer Resuma Vaswani et al. 2017 focando em mecanismo de atenção
5. Agente cria resumo
6. Crie nota em notas/atencao-multi-cabeca.md
7. Complete com exercícios (use _template-nota.md)
8. Teste Feynman
9. Atualize RESUMOS-INDEX e NOTAS-INDEX
```

---

## 📈 Estatísticas de Progresso

Acompanhe em tempo real:

- **RESUMOS-INDEX.md:** X resumos criados / Y planejados
- **NOTAS-INDEX.md:** Z notas revisadas / ~40 total
- **MAPA-DA-IGNORANCIA.md:** N perguntas abertas
- **BENCHMARK-LOG.md:** M experimentos completados

---

## ❓ Questões em Aberto (Dirigem o Estudo)

1. **Qual é o mecanismo de raciocínio multi-etapas em LLMs?** CoT funciona, mas por quê?
2. **Como agentes ultrapassam limites de contexto?** Qual estrutura de memória funciona?
3. **Quando tool calling falha?** Por que agentes chamam ferramentas erradas?
4. **Há limite fundamental em raciocínio sem busca?** Quando preferir árvore de busca?
5. **Como emergem novas estratégias?** Agentes inventam métodos não-treinados?
6. **Segurança de agentes com tool access.** Quais garantias são possíveis?
7. **Composição e generalização.** Agente generaliza para ferramentas novas?
8. **Quando AGI?** O que muda na transição de "tarefas específicas" para "qualquer tarefa"?

Estude para responder. Lacunas dirigem pesquisa.

---

## 🎯 Critérios de Sucesso

### Fim da Fase 1
- ✅ Explicar backpropagation sem papel
- ✅ Desenhar rede neural para problema novo
- ✅ Comparar Transformer com RNN e justificar

### Fim da Fase 2
- ✅ Prever se CoT resolve problema (antes de testar)
- ✅ Explicar por que emergência acontece
- ✅ Descrever 3 razões pelas quais fine-tuning muda comportamento

### Fim da Fase 3
- ✅ Desenhar arquitetura de agente com justificativa
- ✅ Identificar 3 pontos de falha possíveis
- ✅ Comparar 2 arquiteturas e prever vencedor

### Fim da Fase 4
- ✅ Identificar pergunta de pesquisa em aberto
- ✅ Ler paper novo e apontar lacuna
- ✅ Desenhar agente que fecharia a lacuna
- ✅ Estimar custo computacional realista

---

## 📝 Convenções

- **Arquivos:** kebab-case descritivo (`atencao-multi-cabeca.md`, não `nota-3.md`)
- **Fontes:** `[F-001]` em FONTES.md, referenciado em toda nota
- **Marcadores:** `[confirmado]`, `[hipótese]`, `[em debate]`, `[não verificado]`
- **Datas:** AAAA-MM-DD sempre (nunca "recentemente")
- **Commits:** Um assunto, mensagem no imperativo (`Explica backprop e abre pergunta sobre otimização`)
- **Nenhum emoji** em arquivos técnicos (só em README/comunicação)

---

## 🛠️ Tecnologia

- **Linguagem:** Português do Brasil (termos técnicos em inglês, *itálico*)
- **Formato:** Markdown
- **Versionamento:** Git
- **Subagentes:** Claude Code Agent SDK (`@book-summarizer`)
- **Modelos:** Claude Opus 5 (reasoning_effort: extended)

---

## 📚 Ressources Recomendados

**Papers Essenciais:** Vaswani 2017 (Transformer), Brown 2020 (GPT-3), Wei 2022 (Emergência), Wei 2023 (CoT), Yao 2023 (ReAct)

**Livros:** Deep Learning (Goodfellow), Speech & Language Processing (Jurafsky), AIMA (Russell & Norvig)

**Cursos:** CS224n (Stanford NLP), Fast.ai Part 2, DeepLearning.AI agents

---

## 🎓 Espírito do Mestrado

Não é "usar LLMs". É entender:
- **Como** eles raciocinam
- **Quando** falham
- **Por que** agentes com ferramentas abrem caminhos novos

Você sai sabendo:
- Ler paper novo, identificar contribuição real
- Reproduzir, criticar, sugerir próximo passo
- Pesquisador, não só estudante

**Estude rigoroso. Ria quando fizer sentido. Abra pergunta quando travar.**

A ignorância explícita é mais valiosa que confiança mal fundada.

---

**Bora lá! 🚀**

Comece em: [CLAUDE.md](CLAUDE.md)

---

*Repositório em construção (Fase 1: Fundamentos)*  
*Última atualização: 2026-08-20*  
*Responsável: mestrado-agi-agentes*
