# Linha do Tempo — Marcos Técnicos em IA e Deep Learning

Cronologia dos eventos que moldaram o caminho até agentes autônomos com raciocínio. Apenas marcos com **consequência técnica ou mercado rastreável**.

---

## Primeira Onda: Fundamentos Biológicos (1943–1969)

| Data | Marco | Por que importa | Fonte |
|------|-------|-----------------|-------|
| **1943-00-00** `[data parcial]` | **Neurônio de McCulloch-Pitts** — modelo matemático de um neurônio biológico como porta lógica | Primeira formalização de "neurônio artificial". Define a metáfora que sobrevive até hoje. Sem isso, não há rede neural. | [F-001] |
| **1958-00-00** `[data parcial]` | **Perceptron (Rosenblatt)** — máquina de aprender com uma camada que consegue classificar dados linearmente separáveis | Primeira máquina que aprende sem ser explicitamente programada. Esperança: "a máquina pensante está aqui". | [F-001] |
| **1960-00-00** `[data parcial]` | **ADALINE (Widrow & Hoff)** — rede treinável com regra delta, precursor do backpropagation | Mostra que regra de aprendizado existe; o problema é só encontrá-la. Define otimização como método. | [F-001] |
| **1969-00-00** `[data parcial]` | **Minsky & Papert publicam crítica ao perceptron** — provam que perceptrons simples não conseguem aprender XOR | Mata a primeira onda. Funding some. Comunidade conclui: "redes neurais não funcionam". Lição oculta: o mecanismo (camadas ocultas) já existia; faltava saber treinar. | [F-001] |

---

## Segunda Onda: Reconexionismo (1980–1997)

| Data | Marco | Por que importa | Fonte |
|------|-------|-----------------|-------|
| **1986-06-00** | **Backpropagation popularizado** — Rumelhart, Hinton, Williams publicam método eficiente de treino em redes profundas | A solução que faltava na onda 1. Mesmo método existe desde 1974 (Werbos) mas não propagou. Esta data é quando comunidade acorda. | [F-001] |
| **1986-11-00** `[data parcial]` | **Representação Distribuída** — Hinton et al. propõem que conhecimento em redes vive em padrões de ativação, não em neurônios individuais | Muda a visão de como aprender funciona. Cada neurônio é fator de variação, não "célula de avó". Ancestral conceitual de embeddings. | [F-001] |
| **1997-11-11** | **LSTM (Hochreiter & Schmidhuber)** — célula de memória com porta que aprende quando lembrar e esquecer | Resolvem vanishing gradient em sequências longas. Permite treino estável de RNNs profundas. Rede que raciocina no tempo passa a ser treináv. | [F-001] |

---

## Terceira Onda: Deep Learning (2006–presente)

| Data | Marco | Por que importa | Fonte |
|------|-------|-----------------|-------|
| **2006-00-00** `[data parcial]` | **Deep Belief Networks + Greedy Layer-Wise Pretraining** — Hinton et al. mostram que treinar camada por camada funciona | Destrava o treino de redes muito profundas. Marca o início da onda 3 e primeiro reconhecimento de que "profundo" é melhor. | [F-001] |
| **2012-12-03** | **AlexNet vence ILSVRC** — Krizhevsky, Sutskever, Hinton: CNN com 8 camadas reduz erro de top-5 de 26,1% para 15,3% | Breakthrough público. Prova que deep learning em escala funciona. Muda mercado: AI deixa ser acadêmica, vira prioridade de negócio. Início da era dos modelos escalonados. | [F-001] |

---

## Marcos Subsequentes (Referência para Fase 2–4)

Estes marcos aparecem em fontes futuras (F-004+) e entram aqui conforme lidas:

- **2017-06** — Transformer ("Attention Is All You Need") — Vaswani et al. → será F-004 quando lido
- **2018-06** — BERT e evolução em PLN
- **2020-06** — GPT-3 e in-context learning — será F-009 quando lido completamente  
- **2023-04** — GPT-4 com function calling (tool use nascente)
- **2024+** — o-1 e raciocínio explícito; scaling laws; agentes autônomos com planejamento

---

## Notas Metodológicas

**Data parcial:** quando só o ano é conhecido, marca-se `YYYY-00-00` com etiqueta `[data parcial]`. Não se inventa dia.

**Consequência:** entra em linha do tempo só o que moveu a agulha — lançamento de modelo sem novidade arquitetural (GPT-3.5 → 4.0 melhor preço) não entra. Lançamento que introduz mecanismo novo (LSTM, backprop, transformer) entra.

**Fonte:** toda linha cita `[F-xx]`. Quando data for corrigida, a fonte que a corrigiu é registrada. Exemplo: "corrigida em F-015 que publicou histórico de lançamentos".

---

**Última atualização:** 2026-08-20  
**Cobertura:** 1943–2012 (Fases 1–3 do mestrado)  
**Próximos marcos:** A adicionar conforme Fase 4 prosseguir
