# Mapa visual: o caminho até AGI

> Diagramas em Mermaid. No VS Code, abra o preview com `Ctrl+Shift+V` (ou `Ctrl+K V` para lado a lado).
> Os quatro diagramas usam as mesmas cores: conceitos de base em amarelo, hardware em laranja, capacidades em azul, segurança em verde, pessoas em rosa, empresas em verde-água, papers e livros em marrom.

## 1. Mapa conceitual

```mermaid
flowchart TB
    classDef core fill:#B8ACFB,stroke:#8A7BE0,color:#231266,font-weight:bold
    classDef found fill:#FFE86D,stroke:#A28E26,color:#574900
    classDef hw fill:#FFB575,stroke:#CC7830,color:#542700
    classDef cap fill:#9CE6FF,stroke:#2C97BB,color:#1C4657
    classDef safe fill:#B3E65F,stroke:#6E9A24,color:#2F440B

    subgraph HW["Hardware e escala"]
        direction LR
        GPU["GPU"]:::hw
        TPU["TPU / AI Accelerators"]:::hw
        CMP["Compute e Scaling Laws"]:::hw
    end

    subgraph FUND["Fundamentos"]
        direction TB
        ML["Machine Learning"]:::found
        NN["Neural Networks"]:::found
        DL["Deep Learning"]:::found
        TR["Transformers"]:::found
        DATA["Training Data"]:::found
        LLM["LLM<br/>Large Language Models"]:::found
        RL["Reinforcement Learning"]:::found
    end

    AGI(["<b>AGI</b><br/>Artificial General Intelligence"]):::core

    subgraph CAP["Capacidades exigidas"]
        direction LR
        REA["Reasoning"]:::cap
        PLN["Planning"]:::cap
        MEM["Memory e<br/>Continual Learning"]:::cap
        MM["Multimodal<br/>Perception"]:::cap
        AGT["AI Agents"]:::cap
    end

    subgraph SAFE["Segurança"]
        direction LR
        ALN["Alignment"]:::safe
        SAF["AI Safety"]:::safe
        ETH["Ethics e Governance"]:::safe
    end

    GPU -->|fornece| CMP
    TPU -->|fornece| CMP
    CMP -->|treina| DL

    ML -->|inclui| NN
    ML -->|inclui| RL
    NN -->|escalado em| DL
    DL -->|arquitetura| TR
    TR -->|sustenta| LLM
    DATA -->|alimenta| LLM

    LLM -->|caminho candidato| AGI
    RL -->|aprendizado por recompensa| AGI
    CMP -->|viabiliza| AGI

    AGI -->|exige| REA
    AGI -->|exige| PLN
    AGI -->|exige| MEM
    AGI -->|exige| MM
    AGI -->|age por meio de| AGT

    AGI -->|precisa de| ALN
    ALN -->|parte de| SAF
    AGI -->|levanta questões de| ETH
```

## 2. Pessoas e o que cada uma moveu

```mermaid
flowchart LR
    classDef person fill:#FD9AE7,stroke:#D756BA,color:#511341
    classDef found fill:#FFE86D,stroke:#A28E26,color:#574900
    classDef core fill:#B8ACFB,stroke:#8A7BE0,color:#231266,font-weight:bold

    subgraph PIONEIROS["Pioneiros (1950-1960)"]
        P1(["<b>Alan Turing</b><br/>Turing Test, 1950"]):::person
        P2(["<b>John McCarthy</b><br/>cunhou 'AI', 1956"]):::person
        P3(["<b>Marvin Minsky</b><br/>cofundador do campo"]):::person
        P4(["<b>Arthur Samuel</b><br/>cunhou 'Machine Learning'"]):::person
        P5(["<b>Frank Rosenblatt</b><br/>Perceptron, 1958"]):::person
    end

    subgraph DLGEN["Geração deep learning"]
        P6(["<b>Geoffrey Hinton</b><br/>Backpropagation"]):::person
        P7(["<b>Yann LeCun</b><br/>Convolutional Networks"]):::person
        P8(["<b>Yoshua Bengio</b><br/>Deep Learning"]):::person
        P9(["<b>Richard Sutton</b><br/>Reinforcement Learning"]):::person
        P10(["<b>Fei-Fei Li</b><br/>ImageNet"]):::person
    end

    subgraph MODERNOS["Era Transformer e escala"]
        P11(["<b>Ashish Vaswani et al.</b><br/>Attention Is All You Need"]):::person
        P12(["<b>Ilya Sutskever</b><br/>modelos GPT"]):::person
        P13(["<b>Demis Hassabis</b><br/>DeepMind, AlphaGo"]):::person
    end

    AGI(["<b>AGI</b>"]):::core
    ML["Machine Learning"]:::found
    NN["Neural Networks"]:::found
    DL["Deep Learning"]:::found
    RL["Reinforcement Learning"]:::found
    DATA["Training Data"]:::found
    TR["Transformers"]:::found
    LLM["LLM"]:::found

    P1 -.->|imaginou| AGI
    P2 -.->|fundou o campo de AI| AGI
    P3 -.->|trabalhos iniciais| NN
    P4 -.->|nomeou| ML
    P5 -.->|inventou o perceptron| NN
    P6 -.->|avançou| DL
    P7 -.->|avançou| DL
    P8 -.->|avançou| DL
    P9 -.->|formalizou| RL
    P10 -.->|construiu dataset| DATA
    P11 -.->|inventou| TR
    P12 -.->|escalou| LLM
    P13 -.->|aplicou| RL
```

## 3. Empresas

```mermaid
flowchart LR
    classDef company fill:#81E7DE,stroke:#259D92,color:#0E4343
    classDef person fill:#FD9AE7,stroke:#D756BA,color:#511341
    classDef found fill:#FFE86D,stroke:#A28E26,color:#574900
    classDef hw fill:#FFB575,stroke:#CC7830,color:#542700
    classDef safe fill:#B3E65F,stroke:#6E9A24,color:#2F440B

    P12(["<b>Ilya Sutskever</b>"]):::person
    P13(["<b>Demis Hassabis</b>"]):::person
    P7(["<b>Yann LeCun</b>"]):::person

    subgraph LABS["Laboratórios de modelos"]
        C1[["<b>OpenAI</b><br/>GPT, ChatGPT"]]:::company
        C2[["<b>Google DeepMind</b><br/>Gemini, AlphaGo"]]:::company
        C3[["<b>Anthropic</b><br/>Claude, safety research"]]:::company
        C4[["<b>Meta AI</b><br/>Llama, open models"]]:::company
        C7[["<b>xAI</b><br/>Grok"]]:::company
        C8[["<b>Mistral AI</b><br/>open models europeus"]]:::company
        C9[["<b>DeepSeek</b><br/>open LLMs eficientes"]]:::company
    end

    subgraph INFRA["Infraestrutura"]
        C5[["<b>Microsoft</b><br/>Azure AI, Copilot"]]:::company
        C6[["<b>NVIDIA</b><br/>GPUs, CUDA"]]:::company
    end

    P12 -.->|cofundou| C1
    P13 -.->|cofundou| C2
    P7 -.->|liderou pesquisa| C4

    LLM["LLM"]:::found
    TR["Transformers"]:::found
    ALN["Alignment"]:::safe
    TPU["TPU"]:::hw
    GPU["GPU"]:::hw
    CMP["Compute"]:::hw

    C1 -.->|constrói| LLM
    C4 -.->|abre pesos de| LLM
    C7 -.->|constrói| LLM
    C8 -.->|constrói| LLM
    C9 -.->|constrói| LLM
    C2 -.->|Google Brain publicou| TR
    C2 -.->|Google projeta| TPU
    C3 -.->|foco em| ALN
    C5 -.->|fornece| CMP
    C6 -.->|fabrica| GPU
```

## 4. Linha do tempo de papers e livros

```mermaid
timeline
    title Papers e livros que moldaram o caminho
    1943 : McCulloch e Pitts, A Logical Calculus of Nervous Activity → primeiro modelo de Neural Network
    1950 : Turing, Computing Machinery and Intelligence → "can machines think?"
    1969 : Minsky e Papert, Perceptrons (livro) → expôs limites das redes de uma camada
    1986 : Rumelhart, Hinton, Williams, Back-propagating Errors → tornou redes profundas treináveis
    1995 : Russell e Norvig, AI - A Modern Approach (livro) → livro-texto padrão
    1998 : Sutton e Barto, Reinforcement Learning - An Introduction (livro) → formalizou RL
    2012 : Krizhevsky, Sutskever, Hinton, AlexNet → iniciou o boom de DL e provou o valor das GPUs
    2014 : Bostrom, Superintelligence (livro) → alerta sobre AI Safety
    2016 : Goodfellow, Bengio, Courville, Deep Learning (livro) → referência de DL
         : Silver et al., Mastering the Game of Go → marco de RL
    2017 : Vaswani et al., Attention Is All You Need → introduziu o Transformer
    2020 : Kaplan et al., Scaling Laws for Neural Language Models → descreveu as scaling laws
         : Brown et al., Language Models are Few-Shot Learners (GPT-3) → in-context learning em escala
    2022 : Ouyang et al., Training LMs to Follow Instructions (RLHF) → método prático de alignment
```
