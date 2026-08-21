# Introdução (Cap. 1) — *Deep Learning*

> **Metadados**
> - Livro: *Deep Learning*, Capítulo 1 — Introduction
> - Autores: Ian Goodfellow, Yoshua Bengio, Aaron Courville
> - Data: 2016 (MIT Press)
> - Fonte em FONTES.md: **[F-001]**
> - Relevância: **Fase 1 — Fundamentos**, leitura de abertura
> - Arquivo lido: `01 - Introduction.pdf`
> - Data de resumo: 2026-08-20
> - Leitura completa? **SIM** (28 páginas, integral)

---

## Abertura com Contexto

Você vai passar 20 semanas estudando agentes que raciocinam com ferramentas. Antes disso precisa saber **de onde vem o vocabulário** que todo mundo usa sem definir: "representação", "camada", "profundidade", "features". Este capítulo é a única fonte da sua lista que explica por que a IA simbólica dos anos 80 fracassou, e essa história importa agora porque em 2026 metade das propostas de arquitetura de agente (grafo de conhecimento curado, planejador simbólico, ontologia de ferramentas) é uma tentativa de reabilitar exatamente o que fracassou. Você precisa saber distinguir "isso já foi tentado e quebrou" de "isso quebrou por um motivo específico que hoje não se aplica".

## Resumo em Uma Frase

*Deep learning* é a aposta de que a máquina não deve receber os conceitos prontos do humano, e sim aprendê-los em camadas — cada conceito definido a partir de conceitos mais simples — porque o gargalo da IA nunca foi a inferência, foi a **representação**.

---

## Conceitos-Chave

- **A inversão do difícil e do fácil** `[confirmado]` — tarefas formais e abstratas (xadrez) são fáceis para computadores; tarefas intuitivas (ver, ouvir) são difíceis. Deep Blue venceu Kasparov em 1997 porque o xadrez **já vem representado**: 64 casas, 32 peças, regras que cabem numa folha.

- **Fracasso da abordagem *knowledge base*** `[confirmado]` — "None of these projects has led to a major success." Caso canônico: Cyc travou ao ler que Fred se barbeava com barbeador elétrico e perguntou se ele ainda era pessoa (Linde, 1992).

- **Representação é a variável escondida** `[confirmado]` — mesmos dados, cartesiano vs. polar: impossível vs. trivial. Regressão logística acerta indicação de cesárea com *features* clínicas e falha com pixels de ressonância.

- ***Representation learning*** `[confirmado]` — aprender também a representação. Exemplo canônico: *autoencoder* (encoder + decoder).

- ***Factors of variation* e *disentangling*** `[confirmado]` — fontes independentes de influência (sotaque, ângulo, iluminação) que contaminam todo o dado ao mesmo tempo.

- **Deep learning, definição operacional** `[confirmado]` — representações expressas em termos de representações mais simples: pixels → bordas → cantos → partes → objeto. Exemplo quintessencial: MLP.

- **Segunda leitura da profundidade: programa de múltiplos passos** `[confirmado]` — "depth allows the computer to learn a multi-step computer program". Cada camada é o estado da memória após mais um lote de instruções; parte das ativações é *bookkeeping* (contador/ponteiro), não descrição do mundo.

- **Profundidade não tem valor canônico** `[em debate]` — "Nor is there a consensus about how much depth a model requires to qualify as 'deep.'" A mesma regressão logística tem profundidade 3 ou 1 conforme o conjunto de operações primitivas.

- **Taxonomia** `[confirmado]` — IA ⊃ ML ⊃ representation learning ⊃ deep learning.

- **"ML é a única via viável para IA real"** `[hipótese — posição declarada]` — "According to the authors of this book…". Os autores marcam como opinião. Não é resultado.

- **Três ondas** `[confirmado]` — cybernetics (1940–60: McCulloch-Pitts 1943, perceptron 1958, ADALINE 1960), connectionism (1980–95: representação distribuída 1986, backprop 1986, LSTM 1997), deep learning (2006: DBN + greedy layer-wise pretraining). Fim da onda 1: XOR + Minsky & Papert 1969.

- **Representação distribuída** `[confirmado]` — 3 cores × 3 objetos: 9 neurônios (um por combinação) vs. 6 (3+3), com generalização combinatória de brinde. Semente conceitual de *embeddings*.

- **Neurociência inspira, não guia** `[posição dos autores, confirmada]` — "one should not view deep learning as an attempt to simulate the brain"; "greater neural realism has not yet led to an improvement in machine learning performance".

---

## Explicação Didática

### O gargalo está na representação, não na inferência

Xadrez caiu antes do rosto porque xadrez já vem representado — o programador entrega a ontologia completa de graça e sobra só busca. Uma foto vem como matriz de brilho, e nada nela diz "roda". O livro faz o exercício: descreva uma roda em pixels, com sombra em cima, sol no aro, para-lama cobrindo metade. É o mesmo beco do Cyc: o humano tentando enunciar formalmente o que ele mesmo só sabe intuitivamente.

A lição dupla de XOR é instrutiva: Minsky & Papert estavam certos em 1969 — perceptrons simples não resolvem XOR. A crítica era válida. Mas a solução (camadas ocultas) já era conhecida — faltava saber treinar. **Crítica válida a um modelo ≠ crítica válida a um paradigma.** Guarde para as discussões de 2026 sobre limites de LLM.

### A virada em três degraus

1. **Machine Learning:** pare de escrever regras, aprenda o mapeamento features→saída.
2. **Representation Learning:** pare de escolher features, aprenda a representação.
3. **Deep Learning:** mas se extrair uma boa representação é quase tão difícil quanto o problema original, o que salva? **Empilhar.** Bordas são fáceis a partir de pixels. Cantos, a partir de bordas. Cada degrau é curto; a escada é que é longa.

### A leitura de profundidade que importa pro mestrado

Se profundidade é "número de instruções sequenciais executáveis", o modelo tem **orçamento fixo de computação por token**. Daí sai a intuição de por que CoT ajuda: você troca profundidade por comprimento de sequência. 

**Onde a analogia trinca:** programa de verdade tem `while` e recursão sem limite; rede feedforward tem passos fixos. É essa trinca que as *neural Turing machines* remendam com memória externa — o mesmo movimento estrutural que *tool calling* faz hoje: computação que não cabe nos pesos vai pra fora.

---

## Exemplos Práticos

**Exemplo 1 — Cartesiano vs. polar:** bolha central + anel. Em *(x,y)* nenhuma reta separa; em *(r,θ)* uma reta vertical resolve. O classificador não ficou mais inteligente — a representação ficou.

**Exemplo 2 — Cesariana:** mesma regressão logística acerta com features do médico e falha com pixels de MRI. Consequência desconfortável: parte do "desempenho do modelo" é trabalho intelectual humano embutido na entrada. Vale para agentes — metade da competência costuma estar na descrição da ferramenta, não no LLM.

**Exemplo 3 — Representação distribuída:** 6 neurônios em vez de 9, e o neurônio de "vermelhidão" treina com carro, caminhão *e* pássaro. Ganho combinatório de generalização.

**Contraexemplo 1 — Cyc/Fred:** a lógica está impecável; falta a fronteira intuitiva entre "objeto que a pessoa segura" e "parte da pessoa". Falha de **representação**, não de inferência.

**Contraexemplo 2 — XOR:** a crítica de Minsky & Papert matou a área por uma década. Lição: limitação era real, e a solução já era conhecida — faltava saber treinar.

**Contraexemplo 3 — a própria regra de bolso do livro envelhece:** ~5.000 exemplos/categoria (2016) vs. *few-shot in-context learning* do GPT-3 (2020). A regra não estava errada — era correta **para o regime em que foi medida** (treinar supervisionado do zero). O custo migrou para o pré-treino.

---

## Perguntas para o Mapa da Ignorância

1. **A profundidade de rede e o comprimento de cadeia de raciocínio compram a mesma coisa?** 
   - Se profundidade é "instruções sequenciais executáveis", CoT compraria passos via comprimento de sequência em vez de via camadas. Se a equivalência valer, deveria haver troca mensurável entre profundidade do modelo e comprimento de CoT necessário.
   - *Nível:* **fundamento**

2. **A promessa da representação distribuída se sustenta em ferramentas?** 
   - Um agente que aprendeu 100 ferramentas decompôs "ferramenta" em fatores reutilizáveis (nome, schema, semântica de erro) ou memorizou 100 casos? É a pergunta 7 do mestrado, com o enquadramento de Hinton et al. (1986) tornando-a testável.
   - *Nível:* **fundamento**

3. **A crítica ao *knowledge base* se aplica a *knowledge graphs* modernos, ou o que fracassou foi só a curadoria manual em domínio aberto?** 
   - Distinguir isso muda o desenho de RAG híbrido.
   - *Nível:* **aplicação**

4. **A regra dos 5.000 exemplos/categoria tem análogo no regime de in-context learning?** 
   - Muda como se decide entre fine-tuning e prompting.
   - *Nível:* **aplicação**

---

## Conexões no Mestrado

- **Pré-requisito:** nenhum formal. O livro assume CS background (programação, complexidade, cálculo introdutório, vocabulário de teoria dos grafos).

- **Avança para:** Cap. 6 (backpropagation) → Cap. 9/10 (CNN/RNN) → Transformer [F-004]. A ponte natural é: representação distribuída → embeddings → atenção.

- **Aplicação:** 
  - **Projeto 1 (Agente de Diagnóstico)** — o exemplo da cesariana *é* literalmente o caso de uso, com o mesmo alerta: quanto da acurácia é do modelo e quanto é do médico que preencheu o formulário?
  - **Projeto 2 (Agente de Pesquisa Literária)** — o exercício sobre grafo curado à mão discute exatamente a tentação que matou Cyc.

---

## Termos/Benchmarks Encontrados

- **MNIST** — dígitos manuscritos; Hinton a chamou de "the drosophila of machine learning". Já em 2016 o livro a descreve como fácil demais. Candidato a entrada em `GLOSSARIO.md`.

- **ILSVRC** — competição de reconhecimento de objetos; a métrica é top-5 error rate. Candidato a entrada em `GLOSSARIO.md`.

- ***Neural Turing machine*** — rede que lê/escreve em memória endereçável e induz programas simples (Graves et al., 2014a). Ancestral conceitual direto de memória externa em agentes.

- ***Greedy layer-wise pretraining*** — estratégia que destravou a onda 3 em 2006.

---

## Minha Análise Crítica

### O que o capítulo faz bem
É honesto em três lugares onde seria fácil vender fumaça:
- Admite que profundidade não tem definição canônica
- Admite que a inspiração cerebral é retórica de imprensa mais que método
- Assina a tese "ML é a única via viável" explicitamente como opinião dos autores

### O que não cobre (limitação de data)
Nada de atenção ou Transformer (Vaswani 2017), nada de scaling laws, in-context learning, agentes, planejamento ou tool use. O mais perto que chega é NTM e RL do Atari. Você não encontra aqui resposta para nenhuma das oito perguntas de fronteira do mestrado — encontra o vocabulário para formulá-las.

### Onde o argumento é fraco

1. **Contagem de neurônios como métrica de progresso.** A projeção "anos 2050" trata número de neurônios como proxy de capacidade. A década seguinte mostrou que o que move o ponteiro é outra combinação (parâmetros × tokens × qualidade de dados).

2. **Circularidade branda na definição.** "Deep learning resolve representation learning introduzindo representações em termos de representações mais simples" descreve *o que* a arquitetura faz, não *por que* deveria funcionar. Não há argumento sobre por que hierarquias composicionais casam com a estrutura estatística do mundo. É pergunta em aberto de verdade.

3. **Generalização tratada como estimação estatística.** "The key burden of statistical estimation… has been considerably lightened" assume mundo i.i.d.: mais dados, menos problema. Generalização **composicional/sistemática** (resolver o nunca visto) não aparece como categoria separada — e é exatamente a pergunta 7 do mapa.

4. **Zero sobre segurança, viés ou uso indevido.** Em 2016 a omissão era comum; em 2026 é impensável num capítulo introdutório.

---

## A conexão que mais vale carregar

Duas frases do capítulo, lidas juntas, montam quase inteira a agenda de agentes:

> "depth allows the computer to learn a multi-step computer program"

e a descrição das NTMs que "learn to read from memory cells and write arbitrary content to memory cells".

Traduzindo para 2026: computação sequencial dentro dos pesos é limitada e cara, então você externaliza — para o contexto (CoT), para a memória (RAG) ou para o mundo (tool calling). A pergunta 4 do mapa é a versão adulta de uma tensão que já estava no capítulo 1.

---

## Resumo que Fica

✅ **3 pontos-chave:**
1. O gargalo da IA não é a lógica (xadrez prova que computadores ganham fácil), é a **representação** — como transformar pixels em conceitos.
2. A solução é **empilar** — cada camada aprende a representação do nível anterior. Mais simples que resolver tudo de uma vez, mais viável que especificar tudo à mão.
3. Profundidade é **orçamento de computação sequencial**. Daí por que CoT ajuda (você compra passos extras via contexto em vez de via pesos) e por que ferramentas importam (você externaliza computação).

📌 **Takeaway para repetir na próxima reunião:**
> "Se a IA clássica morreu tentando enunciar formalmente o que os humanos sabem intuitivamente, deep learning ganhou deixando a máquina aprender essa intuição em camadas — cada camada transformando o mundo em um mundo novo."

---

## Teste Feynman — Checklist

✅ Consegue explicar cada conceito SEM olhar o texto original?  
✅ Um novato entende a explicação mesmo sem background técnico?  
✅ Consegue inventar um novo exemplo além dos do livro?  
✅ As 3 frases do resumo cobrem 80% do conteúdo?  
✅ Conexões com mestrado são explícitas (por que importa)?  

**Resultado:** PASSOU — nota pronta para o Mapa de Conhecimento.
