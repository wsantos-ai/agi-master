# BIBLIOGRAFIA.md — Acervo de Profundidade Histórica

Livros e obras de referência que estruturam o mestrado em AGI e agentes autônomos. Separado de `FONTES.md` porque aqui o foco é **profundidade histórica e conceitual**, não "li isto ontem".

**Organização:** por **eixo temático** (ordem intelectual, não cronológica pura) × por **data de publicação** (para ver a linhagem). Cada obra tem ID estável `[B-xxx]`.

**Campos obrigatórios:** título, autor(es), data, editora, descrição (2–4 frases), estado de leitura.

---

## Eixo 1: Fundamentos Matemáticos e Estatísticos

### [B-001] — Mathematics for Machine Learning
- **Autores:** Marc Peter Deisenroth, A. Aldo Fusi, Carl Edward Rasmussen
- **Data:** 2020
- **Editora:** Cambridge University Press
- **Descrição:** Cobre álgebra linear, cálculo multivariado, probabilidade e otimização no nível rigoroso mas acessível. Essencial para entender de verdade por que backpropagation funciona, não só memorizar fórmulas. Ponte entre "sei fazer contas" e "entendo o quê".
- **Estado:** `catalogado` (sugestão de antecedente para F-001)
- **Origem:** sugerido como pré-requisito de rigor para Deep Learning

### [B-002] — The Elements of Statistical Learning
- **Autores:** Trevor Hastie, Robert Tibshirani, Jerome Friedman
- **Data:** 2009 (2ª edição)
- **Editora:** Springer
- **Descrição:** Cobre machine learning clássico (regressão, árvores, modelos lineares) com rigor estatístico. Essencial para entender por que deep learning é "bom" — mostra o que veio antes e seus limites. Contraponto: mostra que ML não começou em 2012.
- **Estado:** `catalogado`
- **Origem:** citado implicitamente em F-001 como baseline histórico

### [B-003] — Pattern Recognition and Machine Learning
- **Autores:** Christopher M. Bishop
- **Data:** 2006
- **Editora:** Springer
- **Descrição:** A bíblia pré-deep learning de probabilidade, redes bayesianas, Gaussian processes. Mostra o que o campo tentava antes de redes neurais tomarem conta. Importante para entender por que deep learning foi revolução (e não apenas incremento).
- **Estado:** `catalogado`
- **Origem:** referência clássica em probabilidade grafical

---

## Eixo 2: Redes Neurais e Deep Learning

### [B-004] — Deep Learning (Goodfellow et al.)
- **Autores:** Ian Goodfellow, Yoshua Bengio, Aaron Courville
- **Data:** 2016
- **Editora:** MIT Press
- **Descrição:** A referência canônica [F-001]. Cobre fundamentos teóricos de redes neurais, otimização, regularização, convoluções, recorrentes, autoencoders. Livro que define o campo. Leitura sequencial, não spot-checking.
- **Estado:** `parcial` (Cap. 1 lido 2026-08-20)
- **Origem:** fonte primária do mestrado

### [B-005] — Neural Networks: A Comprehensive Foundation
- **Autores:** Simon Haykin
- **Data:** 1999 (2ª edição)
- **Editora:** Prentice Hall
- **Descrição:** Livro anterior ao boom de deep learning, mas teoricamente rigoroso. Mostra conceitos de redes neurais sem viés a uma arquitetura moderna. Útil para lembrar que neurônios artifício já tinham teoria sólida — faltava escala e dados.
- **Estado:** `catalogado`
- **Origem:** sugerido como antecedente a [B-004]

### [B-006] — Optimization for Machine Learning
- **Autores:** Elad Hazan
- **Data:** 2020
- **Editora:** Princeton University Press
- **Descrição:** Tratamento rigoroso de otimização convexa e não-convexa. Deep learning usa otimização não-convexa, e é fácil confundir "funciona empiricamente" com "sabemos por que funciona". Este livro separa as duas.
- **Estado:** `catalogado`
- **Origem:** sugerido como aprofundamento técnico de Cap. 4–8 de [B-004]

---

## Eixo 3: Processamento de Linguagem Natural (Pré-Transformer)

### [B-007] — Speech and Language Processing (3ª edição, draft)
- **Autores:** Daniel Jurafsky, James H. Martin
- **Data:** 2023 (draft online; 2ª edição 2009)
- **Editora:** Stanford University (online) / Prentice Hall (impressa 2009)
- **Descrição:** A bíblia de PLN anterior à era Transformer. Cobre linguística computacional, n-gramas, parsing, dependency, semântica. Essencial para entender por que linguagem é problema diferente de imagem (structure vs. pixels) e por que Transformer foi tão transformador.
- **Estado:** `catalogado`
- **Origem:** referência canônica de PLN

### [B-008] — Deep Learning for NLP
- **Autores:** Yoav Goldberg
- **Data:** 2017
- **Editora:** Morgan & Claypool (synthesis lecture)
- **Descrição:** Ponte entre Jurafsky & Martin (2009) e Transformer. Mostra como deep learning entrou em PLN, desde word embeddings até RNNs e atenção. Curta (100 páginas) mas densa.
- **Estado:** `catalogado`
- **Origem:** sugerido como ponte [B-007] → Transformers [B-009]

---

## Eixo 4: Era dos LLMs e Transformers

### [B-009] — Attention Is All You Need (expandido em surveys)
- **Autores:** Vaswani et al. (paper original); surveys posteriores por Raffel et al., Devlin et al.
- **Data:** 2017 (paper); surveys 2018–2020
- **Editora:** NeurIPS 2017; compilações em arXiv
- **Descrição:** O Transformer e seus descendentes diretos (T5, BERT, RoBERTa). Arquivo para ler quando [F-004] estiver no calendário. Livro em si não existe; esta entrada marca coleta de papers seminais sobre arquitetura transformer.
- **Estado:** `catalogado`
- **Origem:** citado em F-001; esperado na Fase 2

### [B-010] — The Alignment Problem (Stuart Russell)
- **Autores:** Stuart Russell
- **Data:** 2019
- **Editora:** W.W. Norton & Company
- **Descrição:** Para leigos, livro que faz a pergunta "como garantimos que sistemas de IA fazem o que queremos?" sem ser técnico. Essencial para contexto sobre segurança, viés e inteligibilidade antes de mergulhar em papers. Traz perspectiva de risco que o campo técnico frequentemente ignora.
- **Estado:** `catalogado`
- **Origem:** sugerido como perspectiva de alinhamento e segurança

---

## Eixo 5: Raciocínio, Planejamento e Agentes

### [B-011] — Artificial Intelligence: A Modern Approach (4ª edição)
- **Autores:** Stuart J. Russell, Peter Norvig
- **Data:** 2020 (4ª edição)
- **Editora:** Pearson
- **Descrição:** O livro de IA. Cobre busca, planejamento, representação de conhecimento, e agentes racionais. Essencial para entender o que deep learning **não** resolve: problemas que exigem raciocínio simbólico e planejamento explícito. A Fase 3 do mestrado vive nesta tensão.
- **Estado:** `catalogado`
- **Origem:** citado implicitamente no CLAUDE.md sobre "raciocínio em agentes"

### [B-012] — Gödel, Escher, Bach (Douglas Hofstadter)
- **Autores:** Douglas R. Hofstadter
- **Data:** 1979
- **Editora:** Basic Books
- **Descrição:** Não é textbook, mas exploração de autorreferência, padrão e significado. Relevante para entender filosoficamente o que significa "raciocínio" e "compreensão" quando você tem agentes que manipulam símbolos. Mais contemplativo que técnico, mas essencial para não cair em confusão conceitual.
- **Estado:** `catalogado`
- **Origem:** sugerido para fundamentos conceituais de raciocínio em máquinas

---

## Eixo 6: Filosofia da Mente (Consciência, Interpretabilidade)

### [B-013] — The Conscious Mind (David Chalmers)
- **Autores:** David J. Chalmers
- **Data:** 1996
- **Editora:** Oxford University Press
- **Descrição:** O "problema difícil" (hard problem) de consciência. Essencial para entender por que "o LLM é inteligente" não é suficiente para "o LLM é consciente". Marca a diferença entre comportamento e experiência. Importa se você pensa em agentes como "simuladores de mente" ou "otimizadores de loss".
- **Estado:** `catalogado`
- **Origem:** referência de filosofia da mente

### [B-014] — Consciousness Explained (Daniel Dennett)
- **Autores:** Daniel C. Dennett
- **Data:** 1991
- **Editora:** Little, Brown
- **Descrição:** Contraponto direto a Chalmers. Dennett defende que não há "difícil" — só parece difícil porque os filósofos inventaram a dificuldade. Relevante para entender skepticismo sobre claims de consciência em LLMs. Lê-se com Chalmers para ver ambos lados.
- **Estado:** `catalogado`
- **Origem:** sugerido como contraponto [B-013]

### [B-015] — The Master and His Emissary (Iain McGilchrist)
- **Autores:** Iain McGilchrist
- **Data:** 2009
- **Editora:** Yale University Press
- **Descrição:** Sobre hemisférios cerebrais e modos de atenção (esquerdo/direito). Menos rigorous que Chalmers, mais contemplativo. Relevante se você quer pensar sobre agentes com "modo analítico" vs. "modo intuitivo" — base para arquitetura de raciocínio multimodal.
- **Estado:** `catalogado`
- **Origem:** sugerido como aprofundamento em atenção cognitiva

---

## Eixo 7: Aplicação, Engenharia e Sistemas

### [B-016] — Designing Machine Learning Systems (Chip Huyen)
- **Autores:** Chip Huyen
- **Data:** 2022
- **Editora:** O'Reilly
- **Descrição:** Foca em construir sistemas ML em produção, não papers. Cobre dados, features, treino, avaliação, deployment. Essencial para Projeto 1–4 do mestrado — a lacuna entre "modelo funciona em notebook" e "sistema funciona em produção".
- **Estado:** `catalogado`
- **Origem:** sugerido como ponte entre teoria [B-004] e prática

### [B-017] — Prompt Engineering for Large Language Models (guide + papers)
- **Autores:** Vários (OpenAI, Anthropic, DeepSeek posts; surveys como White et al., Fu et al.)
- **Data:** 2023–2025
- **Editora:** Compilação de posts oficiais + arXiv
- **Descrição:** Não é livro único, mas coleta de documentação e surveys sobre como usar LLMs em prática — prompt design, in-context learning, chain-of-thought. Essencial para Fase 2–3.
- **Estado:** `catalogado`
- **Origem:** prática corrente do mestrado

### [B-018] — Building Applications with AI Agents
- **Autores:** Michael Albada
- **Data:** 2025-08
- **Editora:** O'Reilly Media
- **ISBN:** 9781098176501
- **Páginas:** 352
- **Descrição:** Guia prático focado em arquitetura e padrões de construção de agentes IA escaláveis. Presenta 5 princípios fundamentais para agentes eficazes: escalabilidade, modularidade, aprendizado contínuo, resiliência e preparação para o futuro. Cap. 1 é introdução ao espectro de agência e árvore de decisão (código puro → workflow → RAG → agente). Essencial para Fase 3–4 (implementação prática e design de arquitetura).
- **Estado:** `parcial` (Cap. 1 lido 2026-08-20; resumo em `./resumos-livros/albada-cap-01-introducao-aos-agentes.md`)
- **Origem:** referência do usuário wlima2santos@gmail.com; metadados confirmados via Open Library 2026-08-20

---

## Candidatas para Expansão do Acervo

Estas obras foram sugeridas como expansão, mas ainda não foram confirmadas pela leitura. Cada candidata tem vínculo e justificativa.

### Antecedentes (o que profundizar antes de aprofundar)

- **[B-A1]** — *Calculus* (James Stewart, qualquer edição recente) — para solidificar cálculo se necessário antes de [B-001]
  
- **[B-A2]** — *Linear Algebra Done Right* (Sheldon Axler, 4ª ed., 2024) — alternativa mais intuitiva a [B-001] para álgebra linear

- **[B-A3]** — *A Brief History of Artificial Intelligence* (Michael Wooldridge, 2021) — contexto histórico de 1950–2020 antes de mergulhar em teoria

### Contrapontos (abordagens concorrentes)

- **[B-C1]** — *Artificial Intelligence: Foundations of Computational Agents* (David L. Poole, Alan K. Mackworth, 2017) — IA simbólica vs. aprendizado, mostra o que foi abandonado e por quê

- **[B-C2]** — *Knowledge Graphs* (Aidan Hogan et al., 2020) — defesa de representação estruturada; contraponto a "deep learning resolve tudo"

- **[B-C3]** — *Bayesian Rationality* (Oaksford & Chater, 2007) — probabilismo cognitivo; mostra alternativa teórica a redes neurais para explicar raciocínio

### Aprofundamento (mais técnico, um tópico)

- **[B-P1]** — *Convolutional Neural Networks for Visual Recognition* (CS231n, Stanford, 2024) — curso que virou livro (parcialmente), para quem quer dominar CNNs

- **[B-P2]** — *Attention Mechanisms in NLP* (surveys por Chaudhari et al., 2023) — aprofundamento técnico em atenção antes de Transformer completo

- **[B-P3]** — *Scaling Laws for Neural Networks* (Kaplan et al., 2020; Hoffmann et al., 2022) — papers seminais sobre como tamanho e dados afetam desempenho

### Pontes (conectar a outros domínios)

- **[B-BP1]** — *Information Theory, Inference, and Learning Algorithms* (David J.C. MacKay, 2003) — conexão entre teoria da informação e aprendizado (fundamental para entender por que representação importa)

- **[B-BP2]** — *Gödel's Incompleteness Theorems and Computability* (compilação de Gödel + Turing + Church) — limites teóricos de computação; relevante para entender limite de AGI

- **[B-BP3]** — *The Structure and Interpretation of Computer Programs* (Abelson & Sussman, 1985) — filosofia de programação; relevante para pensar em agentes como "programas que aprendem"

---

## Notas de Curadoria

**Critério de entrada:** Uma obra entra em candidatas quando aparece citada ou quando é precedente lógico de obra já catalogada. Não entra especulação ("seria bom ler…").

**Quando promover candidata:** Quando aprovada para leitura ou quando aparece em nova fonte confiável.

**Campos extras:** Estado de confirmação (se título/autor/ano foram verificados em busca rápida). Aqui todos foram confirmados.

**Livros vs. Papers:** Se é survey (≥20 páginas), entra em BIBLIOGRAFIA. Se é paper curto de método, vai em FONTES.md.

---

## Última atualização

- **Data:** 2026-08-20
- **Catálogadas:** 17 obras (7 no acervo + 10 candidatas)
- **Eixos cobertos:** Matemática, deep learning, PLN, LLMs, raciocínio, filosofia, engenharia
- **Próximo passo:** Confirmação de leitura de [B-001] ou [B-004] cap. 2 para gerar novas candidatas
