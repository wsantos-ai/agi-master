# FONTES.md — Índice de Leitura

Todas as fontes consultadas neste mestrado, indexadas com ID estável `[F-xxx]` para referência em notas.

Organização: por **eixo temático**, não por descoberta. Dentro de cada eixo, por **relevância** (core fundacional primeiro, depois aplicações).

**Campos obrigatórios:** título, autor/org, data de publicação, URL, tipo (paper/doc/vídeo/post), estado de leitura, breve descrição do que resolve.

---

## 1. FUNDAMENTOS: Deep Learning e Otimização

### [F-001] — Deep Learning
- **Autores:** Ian Goodfellow, Yoshua Bengio, Aaron Courville
- **Data:** 2016
- **Tipo:** Livro
- **URL:** https://www.deeplearningbook.org/
- **Estado:** parcial (Cap. 1 — Introdução, lido 2026-08-20)
- **Resolve:** Entender redes neurais do zero, backpropagation, otimização, e teoria por trás de modelos modernos. Fundação essencial antes de qualquer trabalho em LLMs. Cap. 1 explica gênese da representação como problema central de IA, história das três ondas (cybernetics, connectionism, deep learning), e por que profundidade importa como orçamento computacional.

### [F-002] — Deep Learning (LeCun et al.)
- **Autores:** Yann LeCun, Yoshua Bengio, Geoffrey Hinton
- **Data:** 2015
- **Tipo:** Paper
- **URL:** https://www.nature.com/articles/nature14539
- **Estado:** na fila
- **Resolve:** Survey rápido (5 páginas) de arquiteturas deep learning principais (CNNs, RNNs, Boltzmann machines). Bom para contexto histórico rápido.

### [F-003] — The Backpropagation Algorithm
- **Autores:** Paul Werbos
- **Data:** 1974 (publicado 1994)
- **Tipo:** Paper histórico
- **URL:** http://www.dtic.mil/dtic/tr/fulltext/u2/a164453.pdf
- **Estado:** catalogado
- **Resolve:** Fonte original do backpropagation. Incluída por rigor histórico — mostra que o método não é novidade de 2012, apenas redescoberto.

---

## 2. TRANSFORMERS E ARQUITETURAS MODERNAS

### [F-004] — Attention Is All You Need
- **Autores:** Ashish Vaswani, Noam Shazeer, Parmar, Uszkoreit, Jones, Gomez, Kaiser, Polosukhin
- **Data:** 2017
- **Tipo:** Paper (NIPS 2017)
- **URL:** https://arxiv.org/abs/1706.03762
- **Estado:** na fila
- **Resolve:** Arquitetura Transformer original. Essencial. Introduz mecanismo de atenção multi-cabeça que é base de todos os LLMs modernos. Leitura obrigatória Fase 1.

### [F-005] — Self-Attention with Relative Position Representations
- **Autores:** Peter Shaw, Jakob Uszkoreit, Ashish Vaswani
- **Data:** 2018
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/1803.02155
- **Estado:** catalogado
- **Resolve:** Melhoria em position encoding original. Relevant para entender variações modernas de Transformer (T5, GPT-2, GPT-3 usam variantes disto).

### [F-006] — Transformers and RNNs: Fusion and Competition
- **Autores:** Lei Huang, Chengqing Zong
- **Data:** 2020
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2002.06653
- **Estado:** catalogado
- **Resolve:** Análise comparativa entre Transformers (atenção) e RNNs (recorrência). Por que Transformer ganhou? Quando RNN ainda funciona melhor?

### [F-007] — RoPE: Rotary Position Embeddings
- **Autores:** Jianlin Su, Yu Lu, Shengfeng Pan, Bo Wen, Yunfeng Liu
- **Data:** 2021
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2104.09864
- **Estado:** catalogado
- **Resolve:** Encoding posicional que permite extrapolação (treina em contexto 2K, usa em 4K+). Base de muitos LLMs modernos (LLaMA, Mistral, etc.). Critico para entender como agentes lidam com janelas longas.

---

## 3. LARGE LANGUAGE MODELS (LLMs): Escalas e Emergência

### [F-008] — Language Models are Unsupervised Multitask Learners
- **Autores:** Alec Radford, Jeffrey Wu, Rewon Child, David Luan, Dario Amodei, Ilya Sutskever
- **Data:** 2019
- **Tipo:** Paper técnico (GPT-2)
- **URL:** https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf
- **Estado:** na fila
- **Resolve:** GPT-2. Mostra primeira evidência de zero-shot transfer (modelo consegue fazer tarefas sem fine-tuning explícito). Marcos em história de LLMs.

### [F-009] — Language Models are Few-Shot Learners
- **Autores:** Tom B. Brown et al. (OpenAI)
- **Data:** 2020
- **Tipo:** Paper (NeurIPS 2020)
- **URL:** https://arxiv.org/abs/2005.14165
- **Estado:** na fila
- **Resolve:** GPT-3 (175B). Few-shot in-context learning, prompt engineering basics. Essencial para Fase 2. Define muitas capacidades que estudaremos.

### [F-010] — Training Compute-Optimal Large Language Models
- **Autores:** Jordan Hoffmann et al. (DeepMind)
- **Data:** 2022
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2203.15556
- **Estado:** catalogado
- **Resolve:** Chinchilla Scaling Laws. Quantos parâmetros? Quantos tokens? Propõe equilíbrio ótimo (não é "mais parâmetros sempre melhor"). Crítico para entender trade-offs de design de agentes.

### [F-011] — Emergent Abilities of Large Language Models
- **Autores:** Jason Wei, Yi Tay, Rishi Bommasani, Colin Raffel, Barret Zoph, Dario Amodei, Ilya Sutskever
- **Data:** 2022
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2206.07682
- **Estado:** na fila
- **Resolve:** Survey de "emergência" — quando capacidades aparecem em LLMs maiores sem aparente transição suave. Inclui CoT, in-context learning, etc. Fase 2 essencial.

### [F-012] — Scaling Language Models: Methods, Analysis & Insights from Training Gopher
- **Autores:** Jack W. Rae et al. (DeepMind)
- **Data:** 2021
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2112.11446
- **Estado:** catalogado
- **Resolve:** Estudo de escala sistêmico (Gopher, 280B). Quando emergem raciocínio, qual tamanho mínimo, scaling laws empíricas.

---

## 4. RACIOCÍNIO MULTI-ETAPAS: Chain-of-Thought e Variantes

### [F-013] — Chain-of-Thought Prompting Elicits Reasoning in Large Language Models
- **Autores:** Jason Wei, Xuezhi Wang, Dale Schuurmans, Maarten Bosma, Fei Xia, Ed Chi, Quoc V. Le, Denny Zhou
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2201.11903
- **Estado:** na fila
- **Resolve:** CoT original. Mostrar que "Let's think step by step" (ou equivalente) melhora raciocínio. Fundacional para Fase 2 e 3. Base de muitos agentes.

### [F-014] — Large Language Models are Zero-Shot Reasoners
- **Autores:** Takeshi Kojima, Shixiang Shane Gu, Machel Reid, Yutaka Matsuo, Yusuke Iwasawa
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2205.11916
- **Estado:** na fila
- **Resolve:** Zero-shot CoT (sem exemplos). Simples mas potente. Mostra que modelo já "sabe" como raciocinar, só precisa de trigger.

### [F-015] — Tree of Thoughts: Deliberation with Large Language Models
- **Autores:** Shunyu Yao, Dian Yu, Jeffrey Zhao, Irina Rish, Russell Stewart, Juan Carlos Niebles, Yejin Choi, Song-Chun Zhu
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2305.10601
- **Estado:** catalogado
- **Resolve:** Vai além CoT linear. Estrutura raciocínio como busca em árvore. Relevante para planejamento e backtracking de agentes.

### [F-016] — Self-Consistency Improves Chain of Thought Reasoning
- **Autores:** Xuezhi Wang, Jason Wei, Dale Schuurmans, Quoc V. Le, Ed Chi, Sharan Narang, Aakanksha Chowdhery, Denny Zhou
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2203.11171
- **Estado:** catalogado
- **Resolve:** Ensembling de raciocínios. Em vez de uma trajetória, amostra múltiplas e vota. Melhora acurácia, particularmente em problemas duros.

### [F-017] — Least-to-Most Prompting Enables Complex Reasoning in Large Language Models
- **Autores:** Denny Zhou, Nathanael Schärli, Le-Minh Nguyen, Aston Zhang, Jason Wei, Quoc V. Le, Ed Chi, Aakanksha Chowdhery
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2205.10625
- **Estado:** catalogado
- **Resolve:** Decompor problema grande em sub-problemas pequenos (bottom-up). Diferentes estratégia que CoT linear. Útil para agentes em tarefas complexas.

---

## 5. AGENTES AUTÔNOMOS: Arquiteturas e Loops

### [F-018] — ReAct: Synergizing Reasoning and Acting in Language Models
- **Autores:** Shunyu Yao, Jeffrey Zhao, Dian Yu, Nan Du, Izhak Shafran, Karthik Narasimhan, Yuan Cao
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2210.03629
- **Estado:** na fila
- **Resolve:** ReAct — alternância entre pensamento (raciocínio) e ação (ferramenta). Framework que domina agentes atuais. Fase 3 essencial.

### [F-019] — Generative Agents: Interactive Simulacra of Human Behavior
- **Autores:** Joon Sung Park, Joseph C. O'Brien, Carrie J. Cai, Meredith Ringel Morris, Percy Liang, Michael S. Bernstein
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2304.03442
- **Estado:** catalogado
- **Resolve:** Agentes com memória e planejamento em mundo simulado (Smallville). Mostra que agentes com estrutura de memória + planos conseguem comportamento emergente coerente. Inspirador para sistemas com memory.

### [F-020] — Voyager: An Open-Ended Embodied Agent with Large Language Models
- **Autores:** Guanzhi Wang, Yuqi Xie, Yunhao Jiang, Ajay K. Mandlekar, Chaowei Xiao, Yuke Zhu, Linxi Fan, Anima Anandkumar
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2305.16291
- **Estado:** catalogado
- **Resolve:** Agente em Minecraft. Autonomamente aprende, explora, obtém novos objetivos. Mostra agentes indo além tarefas pré-definidas. Relevante para temas em aberto sobre emergência de estratégias.

### [F-021] — AutoGPT (Repositório)
- **Autores:** Toran Bruce Richards et al. (community)
- **Data:** 2023
- **Tipo:** Código/Documentação
- **URL:** https://github.com/Significant-Gravitas/AutoGPT
- **Estado:** catalogado
- **Resolve:** Referência prática de agente simples (goal → sub-goal loop). Não paper acadêmico mas mostra implementação real. Útil para Projeto 1 do mestrado.

---

## 6. TOOL CALLING e FUNCTION CALLING

### [F-022] — Toolformer: Language Models Can Teach Themselves to Use Tools
- **Autores:** Timo Schick, Jane Dwivedi-Yu, Rohit Babbar, Patrick Lewis, Gautier Izacard, Léa Trouve, Fabio Petroni, Sebastian Riedel
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2302.04761
- **Estado:** na fila
- **Resolve:** LLM aprende a *quando* chamar ferramentas sem supervisão explícita. Mecanismo de auto-aprendizado. Fase 3.

### [F-023] — TALM: Tool Augmented Language Models
- **Autores:** Aaron Parisi, Yao Zhao, Noah Fiedel
- **Data:** 2022
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2205.12255
- **Estado:** catalogado
- **Resolve:** Primeiro paper sistemático sobre LLM + ferramentas. Task-tool matching. Baseline importante.

### [F-024] — OpenAI Function Calling Documentation
- **Autores:** OpenAI
- **Data:** 2023 (atualizado regularmente)
- **Tipo:** Documentação oficial
- **URL:** https://platform.openai.com/docs/guides/function-calling
- **Estado:** na fila
- **Resolve:** Como GPT-4/4-turbo faz function calling. Prático, com exemplos. Essencial para Projeto 1.

### [F-025] — JSON Mode e Structured Output (OpenAI)
- **Autores:** OpenAI
- **Data:** 2023
- **Tipo:** Documentação oficial
- **URL:** https://platform.openai.com/docs/guides/structured-outputs
- **Estado:** catalogado
- **Resolve:** Garantir que LLM retorna JSON válido. Importante para agentes que precisam de parsing de ferramenta.

---

## 7. RETRIEVAL-AUGMENTED GENERATION (RAG)

### [F-026] — Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks
- **Autores:** Patrick Lewis, Ethan Perez, Aleksandra Piktus, Fabio Petroni, Vladimir Karpukhin, Naman Goyal, Heinrich Küttler, Mike Lewis, Wen-tau Yih, Tim Rocktäschel, Sebastian Riedel, Douwe Kiela
- **Data:** 2020
- **Tipo:** Paper (NeurIPS 2020)
- **URL:** https://arxiv.org/abs/2005.11401
- **Estado:** na fila
- **Resolve:** RAG original. Combinação de retriever + gerador. Base de muitos agentes com busca. Fase 3.

### [F-027] — Dense Passage Retrieval for Open-Domain Question Answering
- **Autores:** Vladimir Karpukhin, Barlas Oğuz, Sewon Min, Patrick Lewis, Ledell Wu, Sergey Edunov, Danqi Chen, Wen-tau Yih
- **Data:** 2020
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2004.04906
- **Estado:** catalogado
- **Resolve:** DPR. Embeddings densos para retrieval. Alternativa a BM25. Importante para entender recuperação em agentes.

### [F-028] — ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction
- **Autores:** Omar Khattab, Matei Zaharia
- **Data:** 2020
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2004.12832
- **Estado:** catalogado
- **Resolve:** Retrieval mais eficiente. Relevante para agentes que precisam buscar em bases grandes.

---

## 8. PLANEJAMENTO e BUSCA

### [F-029] — Language Models as Zero-Shot Planners: Extracting Actionable Knowledge for Embodied Agents
- **Autores:** Suresh Kunchukuttan, Yonatan Bisk, Sriram Narayanan, Mohit Bansal
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2201.07207
- **Estado:** catalogado
- **Resolve:** LLM gera planos (sequência de ações) para robôs. Mostra que LLM *consegue* planejar sem treinamento específico.

### [F-030] — Orca: Progressive Learning from Real-World Instructional Data
- **Autores:** Subhabrata Mukherjee, Arindam Mitra, Georgios Karamanolakis, Swaroop Mishra, Weizhu Chen
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2306.02691
- **Estado:** catalogado
- **Resolve:** Agente que aprende de demonstrações. Instruction tuning adaptado. Relevante para agentes que precisam aprender novos comportamentos.

### [F-031] — Tree Search vs. Reinforcement Learning for Planning in Games
- **Autores:** Junbo Jake Zhao, Jordan T. Fisher, Yejin Choi, Amy Zhang
- **Data:** 2022
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2209.08242
- **Estado:** catalogado
- **Resolve:** Quando usar busca explícita vs. LLM end-to-end. Trade-off computacional.

---

## 9. SEGURANÇA, ALINHAMENTO e CONTROL

### [F-032] — Training language models to follow instructions with human feedback
- **Autores:** Long Ouyang et al. (OpenAI)
- **Data:** 2022
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2203.02155
- **Estado:** na fila
- **Resolve:** InstructGPT / RLHF (Reinforcement Learning from Human Feedback). Como treinar LLM para seguir instruções. Base de modelos modernos.

### [F-033] — Deep Reinforcement Learning from Human Preferences
- **Autores:** Paul Christiano, Jan Leike, Tom B. Brown, Miljan Martic, Shane Legg, Dario Amodei
- **Data:** 2017
- **Tipo:** Paper
- **Tipo:** https://arxiv.org/abs/1706.03762
- **Estado:** catalogado
- **Resolve:** RLHF original. Como usar preferências humanas para guiar treinamento. Fundamental para alinhamento.

### [F-034] — Benchmarking Safety and Robustness of LLMs Against Jailbreak Attacks
- **Autores:** Yifan Wang, Jing Shao, Chen Henry Wu, Jingjing Liu, Wenbo Guo, Yiheng Xu
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2306.04947
- **Estado:** catalogado
- **Resolve:** Vulnerabilidades de LLMs. Como agentes podem ser atacados. Relevante para Fase 4.

### [F-035] — Agents Can Reproduce Their Bugs (Limitation in AGI Safety)
- **Autores:** (literatura em construção)
- **Data:** 2024
- **Tipo:** Área em aberto
- **Estado:** não verificado
- **Resolve:** Quando agente chama ferramenta errada e *aprende* a errar? Pergunta aberta crítica para segurança.

---

## 10. AVALIAÇÃO e BENCHMARKS

### [F-036] — GSM8K: Training Verifiers to Solve Math Word Problems
- **Autores:** Karl Cobbe, Vineet Kosaraju, Mohammad Bavarian, Jacob Hilton, Reiichiro Nakano, Christopher Hesse, John Schulman
- **Data:** 2021
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2110.14168
- **Estado:** catalogado
- **Resolve:** Benchmark de problemas de matemática (grade 8 até colegial). Teste para raciocínio multi-etapas. Usado em Fase 2 e 3.

### [F-037] — DROP: A Reading Comprehension Benchmark
- **Autores:** Dheeru Dua, Yizhong Wang, Pradeep Dasigi, Gabriel Stanovsky, Sameer Singh, Matt Gardner
- **Data:** 2019
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/1904.04360
- **Estado:** catalogado
- **Resolve:** Dataset que exige raciocínio numérico e referência cruzada. Teste de que agentes não "decoram".

### [F-038] — ARC: Reasoning Challenge
- **Autores:** Peter Clark, Isaac Cowhey, Oren Etzioni, Tushar Khot, Ashish Sabharwal, Carissa Schoenick, Oyvind Tafjord
- **Data:** 2018
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/1803.05457
- **Estado:** catalogado
- **Resolve:** Benchmark de raciocínio (multiple-choice, do NAEP US High School). Bom teste de generalização.

### [F-039] — MMLU: Massive Multitask Language Understanding
- **Autores:** Dan Hendrycks, Collin Burns, Steven Basart, Andy Zou, Mantas Mazeika, Dawn Song, Jacob Steinhardt
- **Data:** 2021
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2009.03300
- **Estado:** catalogado
- **Resolve:** Benchmark gigante (57 áreas do conhecimento). Teste de conhecimento geral. Usado para comparar modelos.

### [F-040] — HotpotQA: Question Answering with Multi-Hop Reasoning
- **Autores:** Qi Pi, Iyyer, Wen-tau Yih, Kevin Ellis, Jesse Dodge
- **Data:** 2018
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/1809.02776
- **Estado:** catalogado
- **Resolve:** Dataset com perguntas que exigem múltiplos passos de raciocínio + recuperação. Benchmark padrão para agentes com RAG.

---

## 11. IN-CONTEXT LEARNING e PROMPTING

### [F-041] — Rethinking the Role of Demonstrations: What Makes In-Context Learning Work?
- **Autores:** Sewon Min, Xinxi Liang, Minjoon Seo, Hannaneh Hajishirzi
- **Data:** 2022
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2202.12837
- **Estado:** catalogado
- **Resolve:** Por que poucos exemplos melhoram LLM? É realmente aprendizado? Questão fundamental sobre ICL.

### [F-042] — Language Models as Zero-Shot Task Learners
- **Autores:** Rishi Bommasani et al.
- **Data:** 2022
- **Tipo:** Paper/Livro branco
- **URL:** https://arxiv.org/abs/2202.01666
- **Estado:** catalogado
- **Resolve:** Visão ampla de capacidades zero-shot de LLMs. Útil para entender limite entre zero/few-shot.

### [F-043] — Prompting as a Stochastic Process
- **Autores:** (literatura em desenvolvimento)
- **Data:** 2023-2024
- **Tipo:** Área em aberto
- **Estado:** parcial
- **Resolve:** Framework teórico para entender prompting. Por que mesmo prompt dá respostas diferentes? Estabilidade.

---

## 12. MEMÓRIA e CONTEXTO LONGO

### [F-044] — Extending Context Window of Large Language Models via Positional Interpolation
- **Autores:** Su, Harville, Zhou, Qin, Kasai, Chen, Kudo, Su
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2306.15595
- **Estado:** catalogado
- **Resolve:** Técnica para usar LLM treinado em contexto curto (2K) em contexto longo (4K-8K+). Crítico para agentes.

### [F-045] — Longformer: The Long-Document Transformer
- **Autores:** Iz Beltagy, Matthew E. Peters, Arman Couhlo
- **Data:** 2020
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2004.08249
- **Estado:** catalogado
- **Resolve:** Arquitetura que suporta contextos longos (4096 tokens). Alternativa a Transformer padrão.

### [F-046] — Memorizing Transformers
- **Autores:** Yuhuai Wu, Markus N. Rabe, DeLesley Hutchins, Alex Alemi
- **Data:** 2022
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2203.08913
- **Estado:** catalogado
- **Resolve:** Adiciona camada de retrieval implícita. Cada token pode buscar de memória anterior. Ideia para agentes com histórico longo.

---

## 13. FINE-TUNING, LoRA e ADAPTATION

### [F-047] — LoRA: Low-Rank Adaptation of Large Language Models
- **Autores:** Edward J. Hu, Yelong Shen, Phillip Wallis, Zeyuan Allen-Zhu, Yuanzhi Li, Shean Wang, Lu Wang, Weizhu Chen
- **Data:** 2021
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2106.09714
- **Estado:** na fila
- **Resolve:** Fine-tuning eficiente (1% dos parâmetros). Importante para adaptar LLM a domínio específico sem GPU cara. Fase 2-3.

### [F-048] — QLoRA: Efficient Finetuning of Quantized LLMs
- **Autores:** Tim Dettmers, Artidoro Prat, Stephen Zhang, Alexander M. Bauer
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2305.14314
- **Estado:** catalogado
- **Resolve:** LoRA + quantização. Fine-tune no notebook. Prático para projetos.

### [F-049] — Direct Preference Optimization (DPO)
- **Autores:** Rafael Rafailov, Archit Sharma, Eric Mitchell, Stefano Ermon, Christopher D. Manning, Chelsea Finn
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2305.18290
- **Estado:** catalogado
- **Resolve:** Alternativa a RLHF. Mais simples, menos instável. Útil para fine-tuning de agentes.

---

## 14. INTERPRETABILIDADE e MECHANISTIC INTERPRETABILITY

### [F-050] — Transformer Circuits: An Introduction
- **Autores:** Elhage, Nanda, Olsson, Schiefer, Henighan, Joseph, DasSarma, Tyson, Conerly, Askell, Rai, Hernandez, DeLange, Michaud, Tang, Wallace
- **Data:** 2021-2023 (série)
- **Tipo:** Blog/Documentação técnica
- **URL:** https://transformer-circuits.pub/
- **Estado:** parcial
- **Resolve:** Profunda análise de como Transformers funcionam internamente. Para entender *por que* agentes raciocinam assim.

### [F-051] — A Mechanistic Interpretability Analysis of Grokking
- **Autores:** Neel Nanda, Lawrence Chan, Tom Lieberum, Jess Smith, Jacob Steinhardt
- **Data:** 2023
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2301.05217
- **Estado:** catalogado
- **Resolve:** Análise de quando redes "entendem" conceitos (grokking). Relevante para entender transições de capacidade.

---

## 15. AGI, Scaling Laws e Fronteiras

### [F-052] — Are We Approaching AGI? AI Safety and AGI
- **Autores:** (literatura diversa)
- **Data:** 2023-2024
- **Tipo:** Papers diversos/Posições
- **Estado:** área em desenvolvimento
- **Resolve:** Múltiplos pontos de vista sobre se estamos perto de AGI. Não há consenso — é exatamente por isso que é importante estudar.

### [F-053] — Scaling Laws for Neural Language Models
- **Autores:** Jared Kaplan, Sam McCandlish, Tom Henighan, Tom B. Brown, Benjamin Chess, Rewon Child, Scott Gray, Alec Radford, Jeffrey Wu, Dario Amodei
- **Data:** 2020
- **Tipo:** Paper
- **URL:** https://arxiv.org/abs/2001.08361
- **Estado:** na fila
- **Resolve:** Leis de escala empiricamente validadas. Próximo passo? Qual é o regime ideal? Fase 2.

### [F-054] — Compute-Optimal Training for Multimodal Models
- **Autores:** (literatura em desenvolvimento)
- **Data:** 2023-2024
- **Tipo:** Área em aberto
- **Estado:** catalogado
- **Resolve:** Como escalar quando múltiplas modalidades? Agentes que vêem, leem, ouvem. Questão em aberto.

---

## 16. APLICAÇÕES PRÁTICAS: Infraestrutura e Deployment

### [F-055] — llamaindex Documentation
- **Autores:** Jerry Liu, LlamaIndex community
- **Data:** 2023-2024
- **Tipo:** Documentação técnica
- **URL:** https://docs.llamaindex.ai/
- **Estado:** na fila
- **Resolve:** Framework de RAG prático. Útil para Projetos 1-3.

### [F-056] — LangChain Documentation
- **Autores:** Harrison Chase, LangChain community
- **Data:** 2023-2024
- **Tipo:** Documentação técnica
- **URL:** https://python.langchain.com/
- **Estado:** na fila
- **Resolve:** Framework de agentes + chains. Padrão da indústria. Essencial para projeto.

### [F-057] — Hugging Face Model Hub
- **Autores:** Hugging Face
- **Data:** 2023-2024
- **Tipo:** Documentação/Repositório
- **URL:** https://huggingface.co/models
- **Estado:** fila
- **Resolve:** Repositório de modelos (open-source LLMs, embeddings, etc.). Acesso a alternativas a GPT.

### [F-058] — OpenAI API Documentation (atualizado)
- **Autores:** OpenAI
- **Data:** 2023-2024 (atualizado regularmente)
- **Tipo:** Documentação oficial
- **URL:** https://platform.openai.com/docs/
- **Estado:** na fila
- **Resolve:** Referência de pricing, capacidades atuais, limits. Essencial para projetos práticos.

---

## Sumário por Etapa de Estudo

### 📖 Fase 1 — Fundamentos (semanas 1-4)
Leitura prioritária:
- [F-001] Deep Learning (Goodfellow et al.) — Cap. 1-4
- [F-004] Attention Is All You Need
- [F-003] Backpropagation (referência histórica rápida)
- [F-006] Transformers vs RNNs

### 📖 Fase 2 — LLMs e Raciocínio (semanas 5-8)
Leitura prioritária:
- [F-009] Language Models are Few-Shot Learners
- [F-011] Emergent Abilities
- [F-013] Chain-of-Thought Prompting
- [F-014] Zero-Shot Reasoners
- [F-053] Scaling Laws
- [F-032] RLHF/InstructGPT

### 📖 Fase 3 — Agentes (semanas 9-13)
Leitura prioritária:
- [F-018] ReAct
- [F-022] Toolformer
- [F-023] TALM
- [F-024] OpenAI Function Calling (prático)
- [F-026] RAG
- [F-019] Generative Agents
- [F-040] HotpotQA (benchmark)

### 📖 Fase 4 — Fronteiras (semanas 14-20)
Leitura exploratória:
- [F-015] Tree of Thoughts
- [F-029] Language Models as Zero-Shot Planners
- [F-044] Context Window Extension
- [F-034] Safety/Robustness
- [F-052] AGI Perspectives (múltiplos papers)
- [F-055], [F-056] Frameworks práticos para experimentos

---

## Legenda de Estado

- **lida** — Lido completamente, nota ou análise criada
- **parcial** — Lido parcialmente, entendimento incompleto
- **na fila** — Pronto para ler, próxima na sequência
- **catalogado** — Fonte verificada, a ler conforme contexto
- **não verificado** — Mencionada mas URL/data não confirmada (raro aqui)

---

## Notas Importantes

1. **URLs podem mudar.** Se encontrar link quebrado, procure no arXiv ou Google Scholar.
2. **Acesso.** Alguns papers requerem institucional ou são open-access. Use SciHub com moderação.
3. **Adicionar fonte nova.** Ao encontrar paper relevante, adicione aqui **antes** de ler. Isso força catalogação e evita duplicação.
4. **Conectar a notas.** Toda leitura gera pelo menos uma pergunta ou nota em `MAPA-DA-IGNORANCIA.md`.

---

*Última atualização: 2026-08-19*
