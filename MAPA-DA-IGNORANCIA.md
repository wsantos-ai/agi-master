# Mapa da Ignorância — Perguntas que Dirigem o Estudo

Este documento registra as perguntas abertas que direcionam o mestrado em AGI e Agentes Autônomos. Toda lacuna deve estar **explícita** aqui, com contexto, tentativas anteriores e nível de impacto.

---

## Perguntas Abertas (Em Investigação)

### **Fundamento — Raciocínio e Profundidade**

#### 1. Profundidade de rede vs. comprimento de cadeia — compram a mesma coisa?

**Enunciado preciso:**  
Se profundidade é "número de instruções sequenciais executáveis" [F-001], então Chain-of-Thought compraria passos extra via comprimento de sequência em vez de via camadas de pesos. Se essa equivalência valer, deveria haver troca mensurável: modelo mais raso + CoT mais longo deveria igualar modelo mais profundo + CoT mais curto.

**Por que importa:**  
Define se agentes que aumentam comprimento de contexto (via memória, RAG, múltiplas chamadas) estão substituindo ou complementando profundidade de modelo. Afeta decisão de arquitetura.

**O que já se tentou:**  
- Leitura do cap. 1 de Deep Learning (F-001) — estabelece profundidade como orçamento de computação
- Não há medição sistemática dessa troca na literatura revisada até 2026-08-20

**Nível:** `fundamento` — bloqueia entendimento de arquitetura de agente

**Status:** Aberta desde 2026-08-20 / [F-001]

---

#### 2. Mecanismo de raciocínio em múltiplos passos — busca implícita ou composição?

**Enunciado preciso:**  
CoT funciona empiricamente [F-013, F-010], mas o mecanismo interno continua em debate: é o LLM fazendo **busca implícita** (testando caminhos mentalmente) ou **composição de padrões** (recombinando comportamentos vistos no treino)? A resposta muda se há limite fundamentalista em raciocínio puro (sem ferramentas).

**Por que importa:**  
Se é busca, há horizonte computacional atingível com mais tokens. Se é composição, há padrões que o treino nunca viu e nenhuma quantidade de contexto resolve — aí ferramentas viram necessárias.

**O que já se tentou:**  
- Wei et al. (F-013) mostram CoT melhora desempenho; não explicam mecanismo
- Neuroscience-inspired papers (não listados em FONTES.md ainda) especulam sobre pruning de possibilidades

**Nível:** `fundamento`

**Status:** Aberta desde 2026-08-20 / Pergunta fronteiriça do mestrado

---

### **Agentes e Ferramentas**

#### 3. Como agentes com ferramentas ultrapassam limites de contexto?

**Enunciado preciso:**  
Se um agente precisa fazer 100 chamadas a ferramentas (RAG, APIs, cálculos), como mantém coerência e memória de decisões anteriores quando janela de contexto é finita? Qual é a estrutura de memória que funciona — episódica, semântica, hierarchical?

**Por que importa:**  
Define limite prático de tamanho de tarefa. Agentes com horizonte longo são o teste de capacidades.

**O que já se tentou:**  
- Nenhuma ainda; esta é pergunta de pesquisa aberta

**Nível:** `fundamento` 

**Status:** Aberta desde 2026-08-20

---

#### 4. Quando agentes chamam ferramentas erradas — diagnóstico e recuperação

**Enunciado preciso:**  
Agentes falham ao selecionar ferramenta: chamam API errada, passam schema errado, interpretam erro de forma inadequada. Que mecanismo de *recovery* funciona sem retraining? Como o agente detém erro, replaneja, e tenta novamente — e como mede se a estratégia de *recovery* foi bem-sucedida?

**Por que importa:**  
Define confiabilidade em produção. Um agente que nunca erra é mais fraco que um que erra mas se recupera.

**O que já se tentou:**  
- Pesquisa inicial: feedback em loop, mas sem métrica clara de quando parar

**Nível:** `aplicação` → `fundamento`

**Status:** Aberta desde 2026-08-20 / [F-001] menciona NTM; conexão a recuperação ainda não explorada

---

#### 5. Há limite fundamentalista em raciocínio sem busca?

**Enunciado preciso:**  
LLMs fazem raciocínio "amortizado" em pesos — tudo precisa ter sido visto em forma similar durante treino. E se um problema exigir busca explícita no espaço de soluções (tipo problema de satisfação de restrições)? Quando é melhor uma árvore de busca tradicional + LLM que LLM puro com CoT?

**Por que importa:**  
Define o tipo de tarefa para o qual agentes com ferramentas são necessários. Alguns problemas talvez sejam resolvíveis só por LLM + raciocínio; outros não.

**O que já se tentou:**  
- Observação anedótica: problemas combinatórios parecem exigir busca explícita
- Nenhuma caracterização formal

**Nível:** `fundamento` 

**Status:** Aberta desde 2026-08-20

---

#### 6. Como emergem novas estratégias de raciocínio em agentes?

**Enunciado preciso:**  
Um agente consegue inventar um método de resolução que seus treinadores não usaram? Ou só recombina padrões já presentes em treino? Se só recombina, há limite nas estratégias emergentes. Se consegue inventar, qual é o mecanismo?

**Por que importa:**  
Teste crítico de "criatividade" em AGI. Define se agentes podem escalar além da experiência de treino.

**O que já se tentou:**  
- Nenhuma medição sistemática

**Nível:** `fundamento` → `curiosidade`

**Status:** Aberta desde 2026-08-20

---

### **Representação e Generalização**

#### 7. Representação distribuída funciona em ferramentas?

**Enunciado preciso:**  
Um agente treinado com 100 ferramentas conseguiu decompor "ferramenta" em fatores reutilizáveis (nome, schema de entrada/saída, semântica de erro) — e assim consegue usar ferramenta 101 nunca vista em treino? Ou memorizou 100 casos específicos e não consegue generalizar?

**Por que importa:**  
Teste direto da hipótese de Hinton et al. (1986) sobre representação distribuída. Se funciona em ferramentas, composição é viável em agentes. Se não funciona, cada ferramenta precisa de treino separado — escala quebra.

**O que já se tentou:**  
- Leitura de F-001 estabeleceu o conceito; aplicação em ferramentas não foi medida

**Nível:** `fundamento` 

**Status:** Aberta desde 2026-08-20 / [F-001]

---

#### 8. Generalização composicional em agentes — quando o nunca visto é resolvível?

**Enunciado preciso:**  
Um agente consegue resolver um problema novo, com ferramentas novas, em domínio novo — nunca visto em treino? Isso é generalização **composicional**. Quando ela funciona e quando quebra? Qual é o limite?

**Por que importa:**  
Critério central de AGI. AGI não é "resolver 1.000 benchmarks vistos em treino" — é resolver o nunca visto.

**O que já se tentou:**  
- Avaliação em benchmarks tipo ARC, GSM8K; mas não sob lente de composição explícita

**Nível:** `fundamento` 

**Status:** Aberta desde 2026-08-20

---

### **Conhecimento Estruturado**

#### 9. Quando RAG falha — características do problema que exigem knowledge graph estruturado

**Enunciado preciso:**  
RAG (Retrieval-Augmented Generation) recupera e passa contexto ao LLM. Funciona bem com fatos isolados. Funciona mal com problemas que exigem raciocínio sobre relações estruturadas. Qual é a característica do problema que determina: RAG suficiente vs. knowledge graph necessário?

**Por que importa:**  
Desenho de sistema — decidir entre simplicidade de RAG e complexidade de grafo.

**O que já se tentou:**  
- Observação: problemas com cadeias causais longas parecem exigir grafo; problemas de fatos isolados funcionam com RAG

**Nível:** `aplicação`

**Status:** Aberta desde 2026-08-20

---

#### 10. A crítica ao *knowledge base* (anos 80) se aplica a *knowledge graphs* modernos?

**Enunciado preciso:**  
Cyc fracassou [F-001] porque tentou curar conhecimento manualmente em domínio aberto — impossível. Mas e se curassem só domínio fechado, com ontologia estável? Ou e se automatizassem a curadoria? A crítica ao método se sustenta ou era específica à escala?

**Por que importa:**  
Define se RAG híbrido (LLM + grafo curado em domínio fechado) é viável ou herda o problema do Cyc.

**O que já se tentou:**  
- Leitura de F-001; nenhuma implementação de teste

**Nível:** `aplicação`

**Status:** Aberta desde 2026-08-20 / [F-001]

---

### **Treinamento e Adaptação**

#### 11. A regra dos 5.000 exemplos/categoria tem análogo no regime de in-context learning?

**Enunciado preciso:**  
F-001 (2016) diz: ~5.000 exemplos rotulados/categoria para desempenho aceitável em treino supervisionado. Em 2020+, GPT-3 faz few-shot in-context learning com ≤5 exemplos no contexto [F-009]. O que mudou? É só shift de custo pré-treino ou há razão mais profunda?

**Por que importa:**  
Muda decisão entre fine-tuning e prompting. Afeta orçamento de desenvolvimento.

**O que já se tentou:**  
- Observação empírica em F-009; nenhuma análise teórica

**Nível:** `aplicação`

**Status:** Aberta desde 2026-08-20 / [F-001], [F-009]

---

### **Segurança de Agentes**

#### 12. Segurança e alinhamento — garantias de comportamento em agentes com tool access

**Enunciado preciso:**  
Um agente chamando APIs reais tem riscos: custo descontrolado, side effects não-intencionais, injeção de prompt, alucinação sobre disponibilidade de ferramenta. Quais garantias são possíveis sem reescrever o agente a cada ferramenta nova?

**Por que importa:**  
Define limite prático de deployment em produção.

**O que já se tentou:**  
- Segurança: nenhuma exploração formal ainda

**Nível:** `fundamento` → `aplicação`

**Status:** Aberta desde 2026-08-20 / CLAUDE.md pergunta 6

---

### **O Problema Grande — AGI e Convergência**

#### 13. Quando AGI? — Transição suave ou qualitativa?

**Enunciado preciso:**  
Hoje (2026) temos "agentes que resolvem tarefas específicas com ferramentas". AGI seria "sistema que resolve qualquer tarefa nova". Há transição suave (mais escala, mais ferramentas) ou são qualidades diferentes que exigem mudança arquitetural?

**Por que importa:**  
Define roadmap de pesquisa. Se é suave, é otimização; se é qualitativa, há descoberta esperando.

**O que já se tentou:**  
- Especulação; nenhuma caracterização formal

**Nível:** `curiosidade` → `fundamento`

**Status:** Aberta desde 2026-08-20 / CLAUDE.md pergunta 8

---

## Perguntas Respondidas (Arquivo)

*(Esta seção será preenchida conforme perguntas forem respondidas. Formato: pergunta # | resposta resumida | [F-xx] | data)*

### **Arquitetura e Decisão de Agência**

#### 16. Como operacionalizar "decisão significativa"?

**Enunciado preciso:**  
Albada propõe que o teste de agência é "tomada de decisão significativa e comportamento adaptativo" em contraste com "execução de trilho". Mas não oferece teste executável: como você mede, numa trajetória de execução dada, se houve decisão genuína ou execução predeterminada? Existe métrica?

**Por que importa:**  
Sem operacionalização, o "espectro de agência" é retórico. Cada arquitetura diz que faz "decisão" — o termo virou vazio.

**O que já se tentou:**  
- Albada não oferece teste; verificar se Caps. 6-7 (avaliação) definem métrica

**Nível:** `fundamento` 

**Status:** Aberta desde 2026-08-20 / [B-018] Cap. 1

---

#### 17. Sistemas multiagentes superam um agente único bem construído?

**Enunciado preciso:**  
O livro de Albada é "Construindo Aplicações com Agentes de IA: Projeto e Implementação de **Sistemas Multiagentes**". Mas Cap. 1 não justifica por que múltiplos agentes superariam um agente único. Em qual classe de tarefa, sob qual critério de avaliação?

**Por que importa:**  
É a premissa central do livro — se não estiver defendida, toda arquitetura multiagente fica em questão.

**O que já se tentou:**  
- Leitura do Cap. 1; promessa está em Caps. 8 (A2A protocol). Conecta a [F-019] Generative Agents.

**Nível:** `fundamento` 

**Status:** Aberta desde 2026-08-20 / [B-018]

---

#### 18. Qual é o benchmark por trás dos scores de modelo 0,819 / 0,812 / 0,811 / 0,807?

**Enunciado preciso:**  
[B-018] Cap. 1 cita: "GPT-5 mini (0,819), o4-mini (0,812), o3 (0,811), GPT-5 (0,807)". Sem nomear o benchmark, o *dataset* ou o protocolo de avaliação. Score médio de quê, em quais tarefas?

**Por que importa:**  
Por critério do repo (CLAUDE.md): número sem fonte primária é inutilizável. Não pode ser citado em trabalho sem benchmark identificado.

**O que já se tentou:**  
- Texto do Cap. 1 não especifica; pode ser erro de tradução ou omissão do original

**Nível:** `aplicação`

**Status:** Aberta desde 2026-08-20 / [B-018] Cap. 1, página 6

---

#### 19. Onde exatamente fica a fronteira entre RAG e agente autônomo?

**Enunciado preciso:**  
[B-018] propõe árvore de 4 degraus: código puro → workflow determinístico → RAG/chatbot → agente. Mas o degrau de RAG desaparece na execução — há parágrafo que descreve RAG dentro da seção de workflow. Qual é a característica que diferencia um RAG sofisticado de um agente? O "planejamento multietapas" é o critério, mas quando RAG já faz 2–3 hops (multi-hop RAG)?

**Por que importa:**  
É a decisão de arquitetura mais frequente na prática. Developers ficam presos na fronteira sem critério claro.

**O que já se tentou:**  
- Leitura do Cap. 1; teste empírico seria rodar Projeto 2 (Agente de Pesquisa Literária) e comparar ROI de RAG vs. agente

**Nível:** `aplicação` 

**Status:** Aberta desde 2026-08-20 / [B-018] Cap. 1 (lacuna editorial)

---

#### 20. *Model routing* funciona sem degradar qualidade?

**Enunciado preciso:**  
[B-018] menciona seleção automática de modelo (*model routing*): enviar consulta simples para modelo pequeno, complexa para modelo grande. O custo do erro de roteamento — quando o roteador manda tarefa difícil para modelo pequeno que falha — nunca é quantificado.

**Por que importa:**  
Determina viabilidade prática de *model routing* em produção. Trade-off: economia vs. risco de degradação.

**O que já se tentou:**  
- Albada menciona como "tendência crescente" sem dados; conecta a [F-010] Chinchilla (scaling laws)

**Nível:** `aplicação`

**Status:** Aberta desde 2026-08-20 / [B-018] Cap. 1

---

#### 21. Observabilidade deveria ser o sexto princípio?

**Enunciado preciso:**  
[B-018] lista 5 princípios (escalabilidade, modularidade, aprendizado contínuo, resiliência, preparação para futuro). Mas observabilidade — capacidade de medir e ver o que o agente está fazendo — é pré-requisito para fechar ciclo de aprendizado contínuo (como saber que o agente não está aprendendo sem medir?) e para detectar falhas em resiliência (como saber que recuperação funcionou sem instrumentação?). Deveria ser princípio 0 ou 6?

**Por que importa:**  
Observabilidade é o critério que separa "agente que funciona" de "agente que funciona *e você sabe por quê*".

**O que já se tentou:**  
- Albada dedica um parágrafo a observabilidade em contexto de aprendizado; não a elevar a princípio

**Nível:** `fundamento` 

**Status:** Aberta desde 2026-08-20 / [B-018] Cap. 1

---

## Meta-observação: Perguntas sobre o Próprio Método

- **Como sei que uma pergunta está bem formulada?** Ela deveria ser testável experimentalmente ou respondível via leitura + análise. "O que é consciência?" é pergunta filosófica eterna. "Segundo qual teoria de consciência um LLM teria o comportamento X?" é pergunta que fecha.

- **Quando uma pergunta passa de aberta para respondida?** Quando há fonte primária que a responde com evidência ou argumento rigoroso. Resposta conjecturista não fecha.

- **Como evito pergunta-ninhoca (que abre 5 novas perguntas)?** Ótimo — pergunta-ninhoca é sinal de que está aprofundando. Abra as 5 novas.

---

**Última atualização:** 2026-08-20  
**Fonte:** CLAUDE.md (perguntas fronteiriças do mestrado) + resumo de F-001 (perguntas de Fase 1)  
**Responsável:** Criação inicial em parceria com book-summarizer agent
