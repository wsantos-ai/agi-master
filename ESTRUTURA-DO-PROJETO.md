# ESTRUTURA DO PROJETO — Organização de Arquivos e Fluxo de Trabalho

## Visão Geral da Estrutura

```
c:\www\agi-master\
│
├── 📋 CLAUDE.md                    ← Instruções mestrado (leia primeiro!)
├── 📚 FONTES.md                    ← Índice de all fontes (papers, livros, docs)
├── 📖 BIBLIOGRAFIA.md              ← Livros (separado de FONTES)
├── 📅 LINHA-DO-TEMPO.md            ← Marcos históricos técnicos
├── ❓ MAPA-DA-IGNORANCIA.md        ← Perguntas abertas (mais importante!)
├── 📊 BENCHMARK-LOG.md             ← Resultados de experimentos
├── 📚 GLOSSARIO.md                 ← Definições precisas de termos
│
├── 📁 resumos-livros/              ← Resumos didáticos de livros/papers
│   ├── README.md
│   ├── _template-resumo.md
│   ├── [F-001]_deep-learning/
│   │   ├── cap-01-introducao.md
│   │   ├── cap-02-redes-neurais.md
│   │   └── ...
│   ├── [F-004]_attention-is-all-you-need/
│   │   └── resumo-completo.md
│   └── ...
│
├── 📁 notas/                       ← Notas de estudo (5 partes da aula)
│   ├── README.md
│   ├── _template-nota.md
│   ├── redes-neurais.md
│   ├── backpropagacao.md
│   ├── transformer.md
│   ├── atencao-multi-cabeca.md
│   ├── chain-of-thought.md
│   ├── react-agentes.md
│   ├── tool-calling.md
│   ├── retrieval-augmented-generation.md
│   └── ... (continue para ~30-40 notas)
│
├── 📁 projetos/                    ← Código e experimentos práticos
│   ├── projeto-01-agente-diagnostico/
│   ├── projeto-02-pesquisa-literaria/
│   ├── projeto-03-error-recovery/
│   └── projeto-04-experimento-pesquisa/
│
├── 📁 .claude/
│   ├── settings.json               ← Configurações Claude Code
│   └── agents/
│       └── book-summarizer.md      ← Subagente para resumos
│
├── 📄 RESUMOS-INDEX.md             ← Índice: Resumo → Status → Nota
├── 📄 NOTAS-INDEX.md               ← Índice: Nota → Fase → Pré-requisitos
├── 📄 ESTRUTURA-DO-PROJETO.md      ← Este arquivo!
└── 📄 README.md                    ← Bem-vindo ao projeto (opcional)
```

---

## Fluxo: Leitura → Resumo → Nota → Projeto

### Etapa 1️⃣: Preparação
1. Adicione livro/paper a **FONTES.md** com ID [F-xxx]
2. Marque em FONTES-INDEX qual fase estuda

### Etapa 2️⃣: Leitura + Resumo
1. Leia livro/capítulo
2. Chame agente: `@book-summarizer Resuma o Cap 3 de [Livro]`
3. Agente cria resumo em `resumos-livros/[F-xxx]_livro/`
4. Você revisa, testa Feynman
5. Atualiza status em **RESUMOS-INDEX.md** para "revisado"

### Etapa 3️⃣: Nota de Estudo
1. Cria arquivo em `notas/` usando `_template-nota.md`
2. Baseado no resumo, desenvolve as 5 partes:
   - Abertura engajadora
   - Explicação técnica
   - Exemplos + contraexemplos
   - Exercícios com gabarito
   - Resumo memorável
3. Testa Feynman (**PASSA ou FALHA**)
4. Se PASSA: marca como "revisado" em **NOTAS-INDEX.md**

### Etapa 4️⃣: Perguntas Abertas
1. Extrai 1-3 perguntas do resumo/nota
2. Adiciona a **MAPA-DA-IGNORANCIA.md** com nível (fundamento/aplicação/curiosidade)
3. Marca "nível: Fase X" para direcionar estudo

### Etapa 5️⃣: Aplicação Prática (Fase 3+)
1. Usa nota em **Projeto 1-4** do mestrado
2. Registra lições aprendidas em **BENCHMARK-LOG.md**
3. Volta para nota se descobrir lacuna (feedback loop)

---

## Arquivos Centrais e Seus Usos

### 📋 CLAUDE.md
**O quê:** Instruções mestrado, persona, princípios, estrutura  
**Quem lê:** Você (todas as vezes que tiver dúvida)  
**Como usar:** Consulte antes de criar qualquer arquivo novo  
**Atualizações:** Raro (apenas se mudarem as regras do mestrado)

### 📚 FONTES.md
**O quê:** Índice de papers, livros, documentação, vídeos  
**Formato:** [F-001] → Título, autor, data, URL, estado, descrição  
**Quem usa:** Toda referência deve ter [F-xx]  
**Como atualizar:** Adicione nova fonte ANTES de ler (força catalogação)  
**Statuses:** lida / parcial / na fila / catalogado / não verificado

### ❓ MAPA-DA-IGNORANCIA.md
**O quê:** Perguntas abertas que dirigem o estudo (é o mais importante!)  
**Formato:** Pergunta específica, por que importa, o que já tentou, nível  
**Quem usa:** Você decide se vale responder agora ou depois  
**Como atualizar:** Adicione perguntas ao ler resumos/notas  
**Transição:** Pergunta aberta → Resposta → Nota de estudo → Marca "respondida"

### 📅 LINHA-DO-TEMPO.md
**O quê:** Marcos históricos (Transformer 2017, GPT-3 2020, etc.)  
**Formato:** AAAA-MM-DD — Marco — por que importa — [F-xx]  
**Quem cria:** Você, ao identificar marco relevante  
**Critério:** Só entra se teve impacto técnico/mercado rastreável

### 📊 BENCHMARK-LOG.md
**O quê:** Resultados de experimentos práticos (Projetos 1-4)  
**Formato:** Data, experimento, setup, resultado, insight  
**Quem atualiza:** Você após testar agente ou arquitetura  
**Uso:** Rastrear progresso prático vs. teórico

### 📁 resumos-livros/
**O quê:** Resumos didáticos (output agente @book-summarizer)  
**Formato:** Um arquivo por capítulo/paper (ou um único se paper curto)  
**Template:** resumos-livros/_template-resumo.md  
**Statuses:** resumo bruto → revisado → (torna-se nota)  
**Índice:** RESUMOS-INDEX.md

### 📁 notas/
**O quê:** Notas de estudo (5 partes da aula + exercícios)  
**Formato:** Um arquivo por conceito, kebab-case  
**Template:** notas/_template-nota.md  
**Statuses:** planejado → rascunho → revisado → pronto  
**Índice:** NOTAS-INDEX.md  
**Teste:** Técnica Feynman OBRIGATÓRIA antes de marcar "revisado"

### 📁 projetos/
**O quê:** Código + análise de Projetos 1-4 (prática do mestrado)  
**Estrutura:** Um diretório por projeto, com README, código, resultados  
**Conexão:** Cada projeto usa notas de 2-3 fases

### 📁 .claude/agents/
**O quê:** Subagentes especializados  
**Contem:** book-summarizer.md (seu agente de resumos)  
**Como usar:** `@book-summarizer [comando]`

---

## Índices Principais

### RESUMOS-INDEX.md
**Tabela:**  
[F-xx] | Livro | Capítulo | Resumo (link) | Nota Gerada | Status | Data

**Statuses:** planejado → resumo bruto → revisado → completo  
**Uso:** Rastrear qual livro já foi resumido, qual vira nota  
**Atualizar:** Quando termina resumo, quando cria nota

### NOTAS-INDEX.md
**Tabela:**  
Conceito | Arquivo (link) | Status | Fonte [F-xx] | Pré-requisitos | Avança Para | Projeto

**Statuses:** planejado → rascunho → revisado → pronto  
**Uso:** Ver o que já tem nota, o que ainda precisa, sequência de estudo  
**Atualizar:** Quando cria ou muda status de nota

---

## Teste Feynman: Validação de Qualidade

Aplicado em três momentos:

### 1. Ao fazer resumo (antes de marcar "revisado")
- [ ] Consigo explicar cada conceito SEM ler o texto original?
- [ ] Um novato entende?
- [ ] Consegui inventar novo exemplo?
- [ ] As 3-4 frases resumem 80% do conteúdo?

### 2. Ao fazer nota (antes de marcar "revisado")
- [ ] Consigo explicar SEM ler a nota?
- [ ] Alguém novo no tema consegue entender?
- [ ] Consegui inventar novo exercício?
- [ ] Cubra e resuma em 3 frases?
- [ ] Consigo guardar só a "frase de efeito"?

### 3. Ao revisar para "pronto"
- [ ] Nota completa (5 partes + exercícios)?
- [ ] Exemplos + contraexemplos cobrem casos importantes?
- [ ] Conexões com mestrado explícitas?
- [ ] Gabarito comentado (explica por quê)?

**Resultado:** ✅ PASSA ou ❌ FALHA (se falha, reescreva)

---

## Dicas Práticas

### 1️⃣ Começar o Mestrado
```
1. Leia CLAUDE.md completo
2. Estude Fase 1: Fundamentos
   - Leia papers [F-001] a [F-007]
   - Crie resumos para cada
   - Crie notas (redes neurais, backprop, transformer, atenção)
3. Quando tiver 5-10 notas, comece Fase 2
```

### 2️⃣ Adicionar Novo Livro
```
1. Adicione em FONTES.md com [F-xxx]
2. Crie pasta em resumos-livros/[F-xxx]_livro/
3. Chame @book-summarizer
4. Agente gera resumo
5. Você revisa e cria nota
6. Adiciona a RESUMOS-INDEX e NOTAS-INDEX
```

### 3️⃣ Quando Travar numa Pergunta
```
1. Não fingia saber
2. Abra no MAPA-DA-IGNORANCIA com:
   - Pergunta específica
   - Por que importa
   - O que já tentou
   - Nível: fundamento/aplicação/curiosidade
3. Continue estudando outros tópicos
4. Volte depois com mais contexto
```

### 4️⃣ Teste Feynman Falha?
```
NÃO reescreva o resumo/nota porque é "fácil demais"
EM VEZ DISSO: identifique a lacuna específica
Abra pergunta no MAPA-DA-IGNORANCIA
Use como feedback para próxima vez
Lembre-se: é um método de aprendizado, não um jogo
```

---

## Cronograma Sugerido

| Semana | Fase | Atividade |
|--------|------|-----------|
| 1-4 | Fundamentos | Leia 3-4 papers [F-001-007], crie 7-10 notas |
| 5-8 | LLMs | Leia 5-6 papers [F-009-017], crie 10-15 notas |
| 9-13 | Agentes | Leia 4-5 papers [F-018-026], crie 8-12 notas, Projeto 1 |
| 14-20 | Fronteiras | Leia 4-5 papers [F-015, F-029-034], Projetos 2-4 |

---

## Estatísticas de Progresso

Acompanhe em:
- **RESUMOS-INDEX.md:** resumos criados / total
- **NOTAS-INDEX.md:** notas revisadas / total
- **MAPA-DA-IGNORANCIA.md:** perguntas abertas vs. respondidas
- **BENCHMARK-LOG.md:** experimentos completados

---

## Perguntas Frequentes

### P: Por que separar Resumos de Notas?
**R:** Resumo é processamento direto da fonte (bruto). Nota é versão didática refinada. Manter separado permite feedback loop: resumo → crítica → nota melhorada.

### P: Preciso preencher Teste Feynman toda vez?
**R:** Sim. É o detector de lacunas. Se passa, avança. Se falha, é sinal de que ainda não entendeu — volte e relê.

### P: Posso pular notas e ir direto para Projeto?
**R:** Não recomendado. Notas estruturam o conhecimento. Projetos testam aplicação. Sem notas, projeto vira achismo.

### P: O que fazer com Perguntas Abertas não respondidas?
**R:** Deixe abertas! Elas dirigem futuro estudo. Não force respostas. Ignorância explícita > confiança mal fundada.

### P: Como conectar Nota com Projeto?
**R:** Em NOTAS-INDEX.md, coluna "Projeto" identifica qual projeto prático usa cada nota. Ao fazer projeto, você consolida 3-4 notas.

---

## Próximo Passo

1. ✅ Você leu esta estrutura
2. 📖 Leia CLAUDE.md (instruções mestrado)
3. 📚 Comece Fase 1 lendo FONTES.md
4. 🤖 Use `@book-summarizer` para primeiro resumo
5. ✍️ Crie primeira nota usando `notas/_template-nota.md`
6. ✅ Teste Feynman
7. 📝 Atualizar RESUMOS-INDEX e NOTAS-INDEX

**Bora lá! 🚀**

---

**Criado:** 2026-08-20  
**Atualizado:** 2026-08-20  
**Responsável:** mestrado-agi-agentes
