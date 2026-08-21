# Capítulo 1 — Introdução aos Agentes

> **Metadados**
> - Livro: *Building Applications with AI Agents: Designing and Implementing Multiagent Systems* (ed. bras.: *Construindo Aplicações com Agentes de IA: Projeto e Implementação de Sistemas Multiagentes*)
> - Autor: Michael Albada
> - Editora/Ano: O'Reilly Media, 2025 — ISBN 9781098176501, 352 p. [confirmado — Open Library, consulta 2026-08-20]
> - Fonte no repo: `[B-018]` em `BIBLIOGRAFIA.md`
> - Relevância: Fase 3 (agentes e *tool calling*), com ponte para Fase 4
> - Edição consultada: tradução PT-BR. Edição PT-BR não localizada em catálogo público `[não verificado]`

## Abertura com Contexto

Você já sabe que um modelo de linguagem (ChatGPT, Claude, etc.) consegue gerar texto. Agora vem a pergunta prática: **quando você realmente precisa construir um "agente" (um programa que usa o modelo de linguagem para resolver problemas)?**

Porque aqui está o ponto: nem tudo que parece "agente" é realmente um agente. Às vezes é só um programa comum disfarçado. E construir um agente de verdade é caro e complicado.

Este capítulo responde: **Como você sabe se precisa de um agente ou se algo mais simples resolve o seu problema?**

## Resumo em Uma Frase

Agência é um espectro — não um rótulo — e a decisão de construir um agente deve ser tomada comparando-o honestamente com três alternativas mais baratas (código puro, *workflow* determinístico, RAG), porque agentes só compensam quando as entradas são imprevisíveis e o planejamento precisa se adaptar em tempo de execução.

## Conceitos-Chave (Explicados Simples)

### 1. Agência é um Espectro, Não um Rótulo

**O que significa?** Não é "agente sim/não". É "quão inteligente a decisão é?"

**Exemplo 1 (NÃO é agente):** Um programa que envia e-mail automático sempre que alguém preenche um formulário. É determinístico — "se formulário = preenchido, então envie e-mail". Sem decisões reais.

**Exemplo 2 (É agente):** Um programa que lê e-mail de reclamação, entende se é urgente ou não, responde com a solução apropriada e escala para humano se muito complicado. Aqui há decisões reais.

**Moral:** Muita coisa vendida como "agente" é só o Exemplo 1 com nome chique.

---

### 2. Sistema Agêntico (O Ecossistema)

**O que é?** Um agente não é só o modelo de linguagem. É o agente **MAIS** tudo ao redor dele:
- Ferramentas que o agente pode usar
- Memória (histórico de conversas)
- O modelo de linguagem em si
- O código que orquestra (coordena) tudo

**Analogia:** Um jogador de futebol é só uma parte do time. Precisa de: técnico, companheiros, uniforme, campo, bola, regras. Tirar qualquer um desses, o time não funciona.

**Moral:** Quando um agente falha, 80% das vezes a culpa não é do modelo. É do sistema em volta.

---

### 3. O que Mudou: Models Passaram a Chamar Funções

**Antes:** Modelo de linguagem recebia pergunta, devolvia texto para humano ler.
- Entrada: "qual é a capital de França?"
- Saída: "Paris é a capital da França."

**Agora:** Modelo de linguagem recebe pergunta, devolve **instruções estruturadas** que o programa executa.
- Entrada: "você quer fazer reserva de voo?"
- Saída: `chamar_funcao("buscar_voos", origem="São Paulo", destino="Rio")`
- Programa executa essa função

**Por que mudou?** O modelo aprendeu a "dizer" o que fazer, não só "descrever".

---

### 4. A Escada de Custo (A Contribuição Mais Importante do Capítulo)

Albada oferece uma árvore de decisão: **use a solução mais simples que resolve seu problema.**

**Degrau 1 — Código Puro:** Se o problema é totalmente previsível, escreva um programa normal.
- Exemplo: programa que divide arquivo CSV em colunas

**Degrau 2 — Workflow Determinístico:** Se o problema tem passos conhecidos mas pode ter variações pequenas, use um "fluxo de trabalho" (regras de negócio).
- Exemplo: "se fatura for PDF, converta; se for CSV, processe; se erro, envie para humano"

**Degrau 3 — RAG (Recuperação + Geração):** Se você precisa responder perguntas sobre um conjunto de documentos, use recuperação + modelo.
- Exemplo: "responda perguntas sobre nossa política de RH a partir desses 300 documentos"

**Degrau 4 — Agente:** Só use agente se as entradas forem imprevisíveis E você precisar de planejamento dinâmico.
- Exemplo: suporte ao cliente que recebe reclamações sobre qualquer coisa possível

**Moral:** Suba de degrau só quando o anterior não funciona.

- **Deslocamento síncrono → assíncrono** [hipótese]: o autor afirma que agentes são projetados para operação assíncrona e que isso "aumenta drasticamente a eficiência" `[trad.]`. É afirmação de design, sem número no capítulo. E é discutível: assincronia é propriedade do orquestrador, não do agente — dá para ter agente síncrono e *workflow* assíncrono.

- **Humano de executor para gestor de tarefas** [hipótese]: e-mail que chega com rascunho pronto, chamado que chega com código e teste unitário. Visão plausível e já parcialmente observável, mas é projeção, não resultado medido.

- **Seleção automática de modelo (*model routing*)** [confirmado como tendência]: rotear consulta simples para modelo pequeno e barato, reservar o grande para raciocínio complexo. O autor chama de otimização dinâmica em tempo de teste.

- **"Um padrão por grupo grande"** [hipótese — heurística organizacional do autor]: deixe as equipes experimentarem livre no começo; padronize por departamento quando o padrão vencedor aparecer. Padronizar cedo demais mata criatividade; nunca padronizar gera projetos duplicados.

## Explicação Didática Simplificada

### A Mudança Técnica: O Modelo Passou a Usar Ferramentas

**Antes:** Você pergunta "Qual é o voo mais barato para Rio?". Modelo responde: "O voo mais barato é R$ 200 com a companhia X às 8h."

**Agora:** Você pergunta a mesma coisa. Modelo responde: "Chame a função buscar_voos(origem='São Paulo', destino='Rio')." O programa executa essa função, recebe os voos de verdade, e volta com a resposta real.

**Por que é importante?** O modelo aprendeu que não é só gerador de texto — é **coordenador**. Ele sabe quando precisa chamar uma ferramenta externa.

**Aviso:** Isso é simplificado. A verdade tem mais detalhes técnicos. Mas a intuição "o modelo coordena ferramentas" está correta.

---

### Quando Usar Cada Solução

#### Degrau 1: Código Puro (Mais Barato)

**Use quando:** Problema é 100% previsível.

**Exemplos:**
- Arquivo com formato fixo AAAA-MM-DD HH:MM:SS (sempre igual)
- Lê um número, multiplica por 2, devolve resultado
- Divide arquivo grande em pedaços

**Por que?** É rápido, barato, fácil de testar, confiável.

**Quando NÃO usar?** Se as entradas variam muito, código puro fica muito complicado (muitos if/else).

---

#### Degrau 2: Workflow Determinístico (Médio)

**Use quando:** Você conhece as regras, mas há variações pequenas.

**Exemplos:**
- "Se documento é PDF, processe assim. Se é CSV, processe assado. Se erro, mande para humano."
- "Se cliente é VIP, responda em 5 min. Se normal, responda em 2h."

**Por que?** Controla o fluxo (quem faz o quê), fácil de auditar (importante para lei/regulação).

**Quando NÃO usar?** Se não consegue listar todas as regras, ou se número de combinações explode.

---

#### Degrau 3: RAG — Recuperação + Resposta (Moderado)

**Use quando:** Você tem documentos e quer responder perguntas sobre eles.

**Exemplos:**
- "Responda dúvidas de funcionários sobre nossa política de RH" (lê 300 documentos internos)
- "Responda sobre características do produto" (lê manual de 50 páginas)

**Por que?** Encontra informação relevante e formata resposta. Não requer "decisão criativa" — só busca + formatação.

**Quando NÃO usar?** Se precisa fazer ações (marcar reunião, aprovar despesa), ou se respostas dependem de múltiplos passos ligados.

---

#### Degrau 4: Agente (Mais Caro)

**Use quando:** Entradas são imprevisíveis + você precisa de planejamento dinâmico.

**Exemplos:**
- Suporte ao cliente (recebe reclamação sobre *qualquer coisa*)
- Planejador de viagem (cada cliente tem necessidades diferentes)
- Assistente de pesquisa (cada pesquisa é única)

**Por que?** Consegue entender contexto, tomar decisões, replanejar conforme aprende.

**Quando NÃO usar?** Se problema é simples. Agentes são caros (processamento + energia + engenharia).

---

### A Moeda de Troca (O Preço que Você Paga)

**Agentes são poderosos, mas caros:**
- **Computação:** Modelos grandes precisam de GPU caras
- **Não-determinismo:** Você não sabe 100% o que o agente vai fazer
- **Engenharia:** Precisa monitorar, ajustar, consertar bugs

**Se você não precisa de adaptabilidade, você está só pagando o preço.**

## Exemplos Práticos

**Exemplo 1 — funciona (agente é a escolha certa): triagem de alertas em SOC.** O agente analista consulta APIs de *threat intelligence*, verifica telemetria de rede e roda análise de binário suspeito em *sandbox* — em paralelo. Mecânica: as subtarefas são independentes entre si, o resultado de cada uma muda a prioridade das seguintes, e cada alerta é diferente do anterior. Bate nos três critérios (entrada variável, planejamento adaptativo, paralelismo). Um *workflow* rígido faria as três consultas sempre na mesma ordem e não repriorizaria.

**Exemplo 2 — funciona de outro jeito (agente por composição, não por paralelismo): cadeia de suprimentos.** O agente ingere estoque em tempo real, prazo de fornecedor e previsão de venda, e **replaneja** o cronograma de remessa. Aqui o valor não é paralelismo, é replanejamento: um *workflow* determinístico exigiria que alguém atualizasse manualmente as regras a cada nova exceção. O agente absorve a exceção sem *deploy*.

**Contraexemplo 1 — não use agente: parser de log com formato fixo.** Entradas totalmente previsíveis, saídas enumeráveis. Uma expressão regular em Python resolve, roda em microssegundos, custa zero e você testa com 20 casos. Botar LLM aqui é pagar latência e não-determinismo para resolver um problema já resolvido.

**Contraexemplo 2 — não use agente: domínio regulado.** Certificação exige lógica de decisão auditável passo a passo. Um modelo caixa-preta não atende ao requisito, por melhor que seja seu desempenho. Repare que aqui o agente **falha mesmo funcionando bem** — o bloqueio é regulatório, não técnico. Esse é o contraexemplo mais instrutivo do capítulo.

**Contraexemplo 3 (autoral — teste Feynman): folha de pagamento.** Entradas variam bastante (horas extras, faltas, adicional noturno, dependentes, sindicato), o que tenta você a chamar de "variável". Mas a variabilidade é **estruturada e finita**, e o resultado precisa ser exatamente reproduzível e auditável perante a lei. Logo: *workflow* determinístico, não agente. Lição: variabilidade de entrada, sozinha, não justifica agente — ela precisa vir acompanhada de imprevisibilidade *semântica*.

## Exercícios Simples

**Exercício 1 — Verdadeiro ou Falso?**

"Um programa que recebe cadastro, checa CPF, envia e-mail e cria conta (sempre nessa ordem) é um agente."

<details>
<summary>Resposta</summary>

**FALSO.** Isso é um *workflow* determinístico. Não há decisões reais — tudo segue a mesma ordem sempre. Um agente tomaria decisões diferentes conforme o contexto (por exemplo: "se CPF inválido, pergunte novamente; se válido, prossiga").

**Moral:** Muita coisa vendida como "agente" é só um programa com nome chique.
</details>

---

**Exercício 2 — Qual solução?**

Seu cliente quer um sistema que responda perguntas de funcionários sobre política de RH (300 páginas de documentos internos). Qual você escolhe?

- (a) Código puro
- (b) Workflow determinístico
- (c) RAG
- (d) Agente

<details>
<summary>Resposta</summary>

**(c) RAG.**

**Por quê?** 
- Problema é "responder perguntas sobre documentos conhecidos"
- Documentos não mudam (só atualizam a cada 3 meses)
- Não precisa de "decisões criativas" — só busca + resposta
- Agente seria overkill (caro demais para o problema)

**Erro comum:** "Mas as perguntas são variadas!" Sim, as *perguntas* são variadas. Mas o *conjunto de documentos* é fixo. RAG lida bem com isso.
</details>

---

**Exercício 3 — Qual NÃO é agente?**

- (a) Programa que toma decisões diferentes conforme o contexto
- (b) Programa que segue a mesma sequência de passos sempre
- (c) Programa que chama ferramentas externos quando precisa
- (d) Programa que aprende com feedback

<details>
<summary>Resposta</summary>

**(b) Programa que segue a mesma sequência sempre.**

Um agente de verdade toma decisões diferentes conforme o contexto. Se tudo é sequencial e fixo, é um workflow (ou código puro), não um agente.
</details>

**Exercício 3 — Crítica de afirmação.** O capítulo diz que agentes "são projetados para operação assíncrona" e que isso "aumenta drasticamente a eficiência". Critique essa afirmação nos termos do repo.

<details>
<summary>Gabarito comentado</summary>

Três problemas, em ordem de gravidade:

1. **Confusão de camadas.** Assincronia é propriedade do orquestrador e da infraestrutura, não do agente. Existem agentes ReAct estritamente sequenciais (o passo *n+1* depende do resultado do passo *n*) e existem *workflows* determinísticos massivamente paralelos. A dicotomia "software tradicional = síncrono / agente = assíncrono" não se sustenta.

2. **"Drasticamente" sem número.** Não há benchmark, medida de latência nem baseline no capítulo. Pela regra do repo, isso é `[hipótese]`, não `[confirmado]`.

3. **Limite real ignorado.** Raciocínio genuinamente multietapas é *serialmente dependente* por definição — se o passo seguinte depende do resultado do anterior, paralelizar não ajuda. O ganho assíncrono aparece em subtarefas independentes (o caso do SOC), que é um subconjunto, não a regra.

Classificação correta: `[hipótese]` para o ganho de eficiência, `[em debate]` para a caracterização de agentes como intrinsecamente assíncronos.
</details>

**Exercício 4 — Diagnóstico de princípio.** Seu agente jurídico classifica errado a mesma cláusula contratual pela quinquagésima vez neste mês. Ninguém percebeu antes. Qual princípio está quebrado, e qual é o *segundo* quebrado?

<details>
<summary>Gabarito comentado</summary>

**Primeiro: aprendizado contínuo.** É literalmente o exemplo que o autor usa — agentes sem ciclo de feedback "podem continuar cometendo os mesmos erros, como classificar incorretamente cláusulas de contrato" `[trad.]`.

**Segundo, e o mais interessante: observabilidade.** "Ninguém percebeu antes" é um problema distinto de "o agente não aprendeu". Você não pode fechar um ciclo de feedback que não mede nada. E aqui está uma lacuna do capítulo: observabilidade e avaliação **não estão** entre os cinco princípios, embora sejam pré-requisito de dois deles (aprendizado contínuo e resiliência).

Se você respondeu só "aprendizado contínuo", acertou o gabarito do livro. Se percebeu a lacuna de observabilidade, encontrou algo que o capítulo não cobre — vale pergunta no Mapa.
</details>

## Resumo que Fica

1. **Agência é espectro, não crachá.** O teste é "decide de verdade ou segue trilho?" — e a maioria do que se vende como agente segue trilho.
2. **A escada de custo tem quatro degraus** e você deve descer o máximo possível: código puro → *workflow* → RAG → agente. Suba um degrau só quando o de baixo comprovadamente quebra.
3. **Dois vetos absolutos ao LLM:** latência de milissegundos e domínio regulado que exige decisão auditável. Nesses casos o agente falha mesmo funcionando bem.
4. **"Sistema agêntico" é o conceito que você leva embora:** o agente é a menor parte; ferramentas, memória, orquestração e infraestrutura são onde mora o trabalho — e onde moram as falhas.

**Takeaway para repetir na reunião de lab:** *"Antes de perguntar qual arquitetura de agente usar, prove que você precisa de um agente. Entrada imprevisível mais replanejamento dinâmico — sem os dois, você está pagando computação e não-determinismo para resolver um problema que uma regex resolvia."*

## Termos e Números Encontrados

| Termo | Definição no capítulo | Marcador |
|---|---|---|
| *Agentic system* / sistema agêntico | Toda a funcionalidade de suporte que permite o agente funcionar: ferramentas, memória, *foundation model*, orquestração, infraestrutura | [confirmado — definição estipulativa do autor] |
| **MCP** (*Model Context Protocol*) | Protocolo para uso de ferramentas remotas. Detalhado no Cap. 4 | [conceito não traduzido no Cap. 1 — só nomeado] |
| **A2A** (Protocolo Agente-para-Agente) | Colaboração entre agentes. Detalhado no Cap. 8 | [conceito não traduzido no Cap. 1 — só nomeado] |
| *Model routing* / seleção automática de modelo | Roteia consulta simples para modelo pequeno, complexa para modelo grande | [confirmado como tendência] |
| Sete tipos de agentes | Negócios/RPA, conversacional, pesquisa, analítico, desenvolvimento, domínio específico, navegador (+ voz e vídeo emergentes) | [confirmado no livro]; atribuído a **The Information** — publicação original `[não verificado]` |

**Números que NÃO deve citar sem checar** `[não verificado]`: o capítulo reporta pontuação média de GPT-5 mini 0,819; o4-mini 0,812; o3 0,811; GPT-5 (2025-08-07) 0,807 — **sem nomear o benchmark**. Score médio de quê, em quais tarefas, com qual protocolo? Sem isso, o número é inutilizável pelos critérios deste repo. Trate como ilustração de "vários modelos estão próximos", nunca como dado.

**Repositório de apoio citado:** `https://oreil.ly/GitHub-scenarios`, com sete cenários de agentes e sistemas de avaliação. `[não verificado]` — não consegui resolver o encurtador nem localizar o repo via API do GitHub. Vale conferir: se existir, é o material mais valioso do livro para os Projetos 1-4.

## Crítica e Lacunas

**Dois defeitos na fonte** (podem ser do original ou da tradução — não pude conferir contra o inglês):

1. **O degrau do RAG evaporou.** O capítulo anuncia quatro alternativas e discute código puro, *workflows* e agentes com exemplos. Mas o parágrafo de *workflows* termina com uma frase que descreve RAG, não *workflow*: "Fluxos de trabalho determinísticos fazem sentido sempre que a tarefa é principalmente responder a perguntas sobre conteúdo estruturado ou não... sua principal despesa é manter os documentos incorporados atualizados" `[trad.]`. "Documentos incorporados" (*embedded documents*) é vocabulário de RAG. Parece haver um parágrafo perdido na edição. Consequência prática: o degrau que mais gente pula na vida real é justamente o pior explicado.

2. **Copy-paste na tabela de frameworks.** AutoGen e CrewAI recebem *trade-offs* idênticos, palavra por palavra ("Pode ser complexo ou pesado em casos de uso simples; mais opinativo quanto aos padrões de interação do agente"), o que é implausível — CrewAI é vendido como o framework simples. E a descrição do LangGraph aparece duplicada como descrição e como "pontos fortes". Conclusão: **não use essa tabela para decidir framework.** Vá à documentação primária.

**Lacunas conceituais:**

- **Observabilidade e avaliação ficam de fora dos cinco princípios**, apesar de serem pré-requisito de dois deles. Você não fecha ciclo de feedback sem medir, e não detecta necessidade de *fallback* sem instrumentar. `[hipótese minha]`: deveria ser um sexto princípio, ou o primeiro.
- **Segurança aparece diluída dentro de "resiliência"**, tratada junto com *timeout* e erro. Mas *prompt injection* e efeito colateral irreversível de ferramenta não são falhas de confiabilidade — são superfícies de ataque com modelo de ameaça adversarial. Categoria errada.
- **Custo nunca vira número.** O capítulo repete que agentes são caros, mas não dá nenhuma ordem de grandeza. Sem isso, "compensa ou não" continua sendo intuição.
- **Multiagente é o subtítulo do livro e quase não aparece no Cap. 1** — só como promessa (A2A, Cap. 8). O capítulo não argumenta *por que* múltiplos agentes superariam um agente único bem construído. Fica em aberto, e é a pergunta mais importante do livro inteiro.
- **A afirmação central sobre agência não é operacionalizada.** "Decisão significativa" é o critério que separa agente de script, mas o capítulo não oferece nenhum teste executável. Como você mede, num sistema dado, se houve decisão ou execução de trilho? Sem isso, o espectro é retórico.

## Perguntas para o Mapa da Ignorância

- **[fundamento]** Como operacionalizar "decisão significativa"? Existe métrica que distinga, na trajetória de execução, decisão genuína de execução de trilho? *Por que importa:* sem isso, o espectro de agência é retórica e toda comparação entre arquiteturas fica sem critério. *Já tentei:* o capítulo não oferece teste; verificar se os Caps. 6-7 (avaliação) fecham.

- **[fundamento]** Sistemas multiagentes superam um agente único bem construído? Em qual classe de tarefa, sob qual critério? *Por que importa:* é o subtítulo do livro e a premissa não é defendida no Cap. 1. Cruza com `[F-019]` Generative Agents.

- **[aplicação]** Qual é o benchmark por trás dos scores 0,819 / 0,812 / 0,811 / 0,807? *Por que importa:* número sem benchmark é inutilizável, e este repo proíbe citá-lo assim.

- **[aplicação]** Onde exatamente fica a fronteira RAG↔agente? O capítulo pula esse degrau. *Por que importa:* é a decisão de arquitetura mais frequente na prática. Cruza com `[F-026]` e `[F-040]` HotpotQA (multi-hop é justamente a zona cinzenta).

- **[aplicação]** *Model routing* funciona sem degradar qualidade? Qual é o custo do erro de roteamento — quando o roteador manda uma tarefa difícil para o modelo pequeno? Cruza com `[F-010]` Chinchilla.

- **[fundamento]** Observabilidade deveria ser o sexto princípio? Testável: pegue um agente sem instrumentação e um instrumentado, e meça o tempo até detecção de regressão.

## Conexões no Mestrado

- **Pré-requisito:** `[F-018]` ReAct e `[F-022]` Toolformer — sem entender o loop de raciocínio-ação, o capítulo soa como consultoria. Também ajuda `[F-024]` (function calling), porque o "pivô da assinatura de função" é literalmente aquilo.
- **Avança para:** Cap. 4 (MCP) e Cap. 8 (A2A) do próprio livro; e a pergunta de multiagente conecta com `[F-019]` Generative Agents.
- **Aplicação direta:** **Projeto 2** (Agente de Pesquisa Literária) — a árvore de decisão do capítulo diz que buscar e sintetizar papers está na fronteira RAG↔agente, então o Projeto 2 vira teste empírico da pergunta em aberto. E **Projeto 1** (Diagnóstico) esbarra no veto de domínio regulado: sistema de triagem médica é exatamente o caso em que auditabilidade pode inviabilizar o agente. Vale registrar essa restrição no escopo do projeto antes de começar.
- **Framework:** o livro adota **LangGraph** — vale abrir entrada separada para LangGraph em `FONTES.md` se você for seguir os exemplos do livro.

---

**Data do resumo:** 2026-08-20  
**Leitura completa do capítulo?** SIM (tradução PT-BR; original em inglês não conferido)
