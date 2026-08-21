# Capítulo 1 — Introdução aos Agentes

> **Metadados**
> - Livro: *Building Applications with AI Agents: Designing and Implementing Multiagent Systems* (ed. bras.: *Construindo Aplicações com Agentes de IA: Projeto e Implementação de Sistemas Multiagentes*)
> - Autor: Michael Albada
> - Editora/Ano: O'Reilly Media, 2025 — ISBN 9781098176501, 352 p. [confirmado — Open Library, consulta 2026-08-20]
> - Fonte no repo: `[B-018]` em `BIBLIOGRAFIA.md`
> - Relevância: Fase 3 (agentes e *tool calling*), com ponte para Fase 4
> - Edição consultada: tradução PT-BR. Edição PT-BR não localizada em catálogo público `[não verificado]`

## Abertura com Contexto

Você já sabe que um LLM sozinho gera texto, e já viu em ReAct `[F-018]` que alternar pensamento e ação melhora resolução de tarefas. O que faltava era a pergunta de engenharia: **quando vale a pena construir um agente, e quando isso é over-engineering caro?** Este capítulo responde exatamente isso. Ele é o mapa antes do território — não ensina a construir nada, ensina a decidir o que construir, e dá o vocabulário (*agentic system*, espectro de agência, seleção de modelo) que os capítulos seguintes assumem como dado.

É o capítulo certo para ler agora porque o mestrado está saindo de "como o modelo raciocina" para "como o sistema opera". São problemas diferentes, e confundir os dois é o erro mais comum de quem vem da leitura de papers.

## Resumo em Uma Frase

Agência é um espectro — não um rótulo — e a decisão de construir um agente deve ser tomada comparando-o honestamente com três alternativas mais baratas (código puro, *workflow* determinístico, RAG), porque agentes só compensam quando as entradas são imprevisíveis e o planejamento precisa se adaptar em tempo de execução.

## Conceitos-Chave

- **Espectro de agência** [confirmado — tese central do autor]: "a capacidade de agir existe em um espectro" `[trad.]`. Muita coisa vendida como agente executa script determinístico. O teste que o autor propõe: o sistema toma decisão de verdade, ou segue trilho fixo? Isso casa exatamente com a regra do repo de tratar "raciocínio" e "planejamento" como reivindicações operacionais, não como descrições.

- **Sistema agêntico (*agentic system*)** [confirmado — definição estipulativa do autor]: não é o agente, é tudo que o sustenta — ferramentas, memória, *foundation model*, orquestração e infraestrutura. Distinção útil: quando um agente falha, na maioria das vezes o que falhou foi o sistema em volta, não o modelo.

- **O pivô técnico que criou agentes** [confirmado]: *foundation models* deixaram de apenas produzir saída legível por humanos e passaram a emitir **assinaturas de função estruturadas com seleção de parâmetros**. Um framework de orquestração executa essas funções. Esse é o mecanismo concreto por trás de "o agente usa ferramentas" — sem misticismo.

- **Árvore de decisão em quatro degraus** [confirmado — é a contribuição prática mais forte do capítulo]: código puro → *workflow* determinístico → RAG/chatbot → agente autônomo. Quatro fatores decidem: variabilidade das entradas, complexidade do raciocínio, restrições de desempenho/conformidade, custo contínuo de manutenção.

- **Deslocamento síncrono → assíncrono** [hipótese]: o autor afirma que agentes são projetados para operação assíncrona e que isso "aumenta drasticamente a eficiência" `[trad.]`. É afirmação de design, sem número no capítulo. E é discutível: assincronia é propriedade do orquestrador, não do agente — dá para ter agente síncrono e *workflow* assíncrono.

- **Humano de executor para gestor de tarefas** [hipótese]: e-mail que chega com rascunho pronto, chamado que chega com código e teste unitário. Visão plausível e já parcialmente observável, mas é projeção, não resultado medido.

- **Seleção automática de modelo (*model routing*)** [confirmado como tendência]: rotear consulta simples para modelo pequeno e barato, reservar o grande para raciocínio complexo. O autor chama de otimização dinâmica em tempo de teste.

- **"Um padrão por grupo grande"** [hipótese — heurística organizacional do autor]: deixe as equipes experimentarem livre no começo; padronize por departamento quando o padrão vencedor aparecer. Padronizar cedo demais mata criatividade; nunca padronizar gera projetos duplicados.

## Explicação Didática

**Primeiro, o que mudou tecnicamente.** Durante anos, um modelo de linguagem era um escritor: você pedia, ele devolvia texto para um humano ler. O destravamento foi ensinar o modelo a devolver **um formulário preenchido** em vez de prosa — o nome da função, os parâmetros, os tipos. Quem executa o formulário é o orquestrador, código comum que você escreve. Analogia: antes o modelo escrevia a receita e você ia para o fogão; agora ele preenche a comanda e a cozinha executa. *Aqui a analogia trinca:* a cozinha de verdade recusa comanda impossível; um orquestrador sem validação executa alegremente uma chamada com parâmetro inventado. Por isso validação não é detalhe — é o que separa a analogia da realidade.

**Segundo, e mais importante, quando não construir um agente.** Este é o miolo do capítulo e onde ele se descola dos papers. O autor monta uma escada de custo crescente. No degrau mais baixo, código puro: se as entradas são totalmente previsíveis e as saídas possíveis cabem numa lista, uma *regex* resolve mais rápido, mais barato e é muito mais fácil de testar do que qualquer *pipeline* de ML. Ele dá o caso do log em formato fixo `AAAA-MM-DD HH:MM:SS—mensagem`. Some a isso duas condições que **eliminam o modelo de linguagem por decreto**: latência na casa de milissegundos (sistema embarcado reagindo a sensor — não há tempo para chamada de API) e domínio regulado (dispositivo médico, aeronáutica, certos sistemas financeiros), onde a lógica precisa ser determinística e auditável e rede neural caixa-preta não passa na certificação.

No degrau seguinte, *workflow* determinístico: a lógica cabe num conjunto finito de ramificações e você sabe de antemão onde precisa de humano no meio. O exemplo é fatura chegando em três formatos conhecidos (CSV, JSON, PDF) — roteie cada um para seu *parser*, verifique inconsistência, pare para revisão humana se a reconciliação falhar. Airflow ou AWS Step Functions dão controle mais claro sobre caminhos de erro do que um LLM. Repare no argumento: não é que o LLM não conseguiria; é que você perde auditabilidade e ganha custo.

Só no topo, agentes — e o critério é preciso: **entradas não estruturadas, inéditas ou muito variáveis, mais necessidade de planejamento dinâmico em várias etapas ou de melhoria contínua por feedback.** O exemplo que ilumina: uma central de atendimento que recebe desde "a bateria do meu laptop está estufada e pode explodir" até "estou sendo cobrado por serviços que não solicitei". Nenhuma árvore de regras cobre essa variedade, e uma FAQ com RAG desaba. O agente interpreta intenção, extrai entidades, consulta base de conhecimento, redige resposta e escala para humano se precisar — sem que você tenha enumerado as ramificações antes.

**Terceiro, o custo.** O autor é honesto: agentes são "poderosos, mas exigem muito — tanto em termos de computação em nuvem quanto de esforço de engenharia para monitorar, ajustar e governar" `[trad.]`. A moeda de troca do capítulo inteiro está aí. Você compra adaptabilidade a entradas imprevisíveis; paga em computação, em não-determinismo e em esforço permanente de observabilidade. Se você não precisa da primeira, está só pagando.

## Exemplos Práticos

**Exemplo 1 — funciona (agente é a escolha certa): triagem de alertas em SOC.** O agente analista consulta APIs de *threat intelligence*, verifica telemetria de rede e roda análise de binário suspeito em *sandbox* — em paralelo. Mecânica: as subtarefas são independentes entre si, o resultado de cada uma muda a prioridade das seguintes, e cada alerta é diferente do anterior. Bate nos três critérios (entrada variável, planejamento adaptativo, paralelismo). Um *workflow* rígido faria as três consultas sempre na mesma ordem e não repriorizaria.

**Exemplo 2 — funciona de outro jeito (agente por composição, não por paralelismo): cadeia de suprimentos.** O agente ingere estoque em tempo real, prazo de fornecedor e previsão de venda, e **replaneja** o cronograma de remessa. Aqui o valor não é paralelismo, é replanejamento: um *workflow* determinístico exigiria que alguém atualizasse manualmente as regras a cada nova exceção. O agente absorve a exceção sem *deploy*.

**Contraexemplo 1 — não use agente: parser de log com formato fixo.** Entradas totalmente previsíveis, saídas enumeráveis. Uma expressão regular em Python resolve, roda em microssegundos, custa zero e você testa com 20 casos. Botar LLM aqui é pagar latência e não-determinismo para resolver um problema já resolvido.

**Contraexemplo 2 — não use agente: domínio regulado.** Certificação exige lógica de decisão auditável passo a passo. Um modelo caixa-preta não atende ao requisito, por melhor que seja seu desempenho. Repare que aqui o agente **falha mesmo funcionando bem** — o bloqueio é regulatório, não técnico. Esse é o contraexemplo mais instrutivo do capítulo.

**Contraexemplo 3 (autoral — teste Feynman): folha de pagamento.** Entradas variam bastante (horas extras, faltas, adicional noturno, dependentes, sindicato), o que tenta você a chamar de "variável". Mas a variabilidade é **estruturada e finita**, e o resultado precisa ser exatamente reproduzível e auditável perante a lei. Logo: *workflow* determinístico, não agente. Lição: variabilidade de entrada, sozinha, não justifica agente — ela precisa vir acompanhada de imprevisibilidade *semântica*.

## Exercícios com Verificação

**Exercício 1 — Classificação.** Um time diz ter construído "um agente de onboarding". O sistema recebe o cadastro, checa CPF numa API, envia e-mail de boas-vindas e cria a conta. Sempre nessa ordem. É agente?

<details>
<summary>Gabarito comentado</summary>

**Não** — pelo teste do próprio autor, é um *workflow* determinístico com rótulo de marketing. O critério é "tomada de decisão significativa e comportamento adaptativo"; aqui a sequência é fixa e conhecida de antemão.

Por que isso importa e não é implicância: se você chamar isso de agente, vai importar o custo do agente (observabilidade, avaliação de trajetória, tratamento de não-determinismo) para um sistema que não precisa de nada disso. O rótulo errado gera arquitetura errada.

Quando viraria agente: se o sistema precisasse decidir *quais* verificações fazer conforme o perfil do cadastro, e replanejar quando uma delas falhasse de forma inesperada.
</details>

**Exercício 2 — Escolha de arquitetura.** Seu cliente quer um sistema que responda dúvidas dos funcionários sobre a política interna de RH. São 300 páginas de PDF, atualizadas trimestralmente. Código puro, *workflow*, RAG ou agente?

<details>
<summary>Gabarito comentado</summary>

**RAG.** A tarefa é essencialmente "responder perguntas sobre conteúdo documental", sem necessidade de chamar APIs externas nem de orquestrar decisões. O autor é explícito sobre esse degrau: custo de manutenção menor que o de agente, sua despesa principal é manter os documentos indexados atualizados e refinar os *prompts*.

O que você sacrifica ao escolher RAG: planejamento multietapas e aprendizado por ciclos de feedback. Você não precisa de nenhum dos dois aqui.

Erro comum: escolher agente porque "as perguntas são variadas". Perguntas variadas sobre um corpus fixo é o caso canônico de RAG, não de agente. A variabilidade que exige agente é a de *ações necessárias*, não a de formulações da pergunta.
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
