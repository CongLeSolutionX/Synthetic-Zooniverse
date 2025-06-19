---
created: 2025-03-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.06252"
---



# BERT (Bidirectional Encoder Representations from Transformers) 
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 


The diagram below provides a comprehensive overview of the BERT architecture, highlighting its foundation in the Transformer encoder and its adaptations for pretraining and fine-tuning on various natural language understanding tasks.



````mermaid
---
title: BERT (Bidirectional Encoder Representations from Transformers) Architecture
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%{
  init: {
    'fontFamily': 'Comic Sans MS',
    'themeVariables': {
      'primaryColor': '#a80077',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#78005a',
      'lineColor': '#f90',
      'secondaryColor': '#f3e8fb',
      'tertiaryColor': '#fff'
    }
  }
}%%
%%%%%%%% Mermaid version v11.4.1-b.14
graph LR
    subgraph BERT_Architecture["BERT Architecture<br>(Encoder-Only Transformer)"]
    style BERT_Architecture fill:#f8fb,stroke:#78005a,stroke-width:2px

        A["Input Sequence<br>([CLS], x<sub>1</sub>, ..., x<sub>n</sub>, [SEP])"] --> B["Token Embeddings<br>(Embedding(x<sub>i</sub>))"]
        C["Segment Embeddings<br>(Embedding(Segment ID))"]
        D["Positional Embeddings<br>(PE)"]
        B --"'+'"--> E["Sum of Embeddings"]
        C --"'+'"--> E
        D --"'+'"--> E
        E --> F["Transformer Encoder Stack<br>(N Layers)"]

        subgraph Encoder_Layer["Encoder Layer<br>(Layer Norm & Residuals)"]
        style Encoder_Layer fill:#d8ff,stroke:#78005a,stroke-width:2px
            subgraph Multi_Head_Self_Attention["Multi-Head Self-Attention"]
                direction LR
                G_Q["Queries (Q)"]
                G_K["Keys (K)"]
                G_V["Values (V)"]
                G_Q & G_K & G_V -- Parallel Projections<br>(W<sup>Q</sup><sub>i</sub>, W<sup>K</sup><sub>i</sub>, W<sup>V</sup><sub>i</sub>) --> H["Scaled Dot-Product<br>Attention Heads<br>(h Heads)"]
            end
            H --> I["Concatenate Heads"]
            I --> J["Output Projection<br>(W<sup>O</sup>)"]
            J --> K["Add & Norm 1<br>(LayerNorm)"]
            K -- "'+'<br>Input from<br>Self-Attention"--> L["Residual Connection 1"]
            L --> M["Position-wise FFN<br>(FFN)"]
             M_IN["Input"]-- L --> M
            M --> N["Add & Norm 2<br>(LayerNorm)"]
            N -- "'+'<br>Output from<br>FFN"--> O["Residual Connection 2"]
            O --> P["Output<br>to Next Layer"]

            E --> G_Q
            E --> G_K
            E --> G_V
            P -->|Output to Next Layer| F
        end

        F --> Q["Pooler Layer<br>(Linear + Tanh)<br>(Output of [CLS] token)"]

        subgraph Pretraining_Tasks["Pretraining Tasks"]
            direction LR
            Q --> R{"Masked Language Modeling<br>(MLM)"}
            F --> S{"Next Sentence Prediction<br>(NSP)"}

            subgraph MLM["Masked Language Modeling"]
                R -- Output from Encoder --> T["Linear Layer"]
                T --> U["Softmax<br>(Vocabulary Size)"]
                U --> V["Predicted Masked Tokens"]
            end

            subgraph NSP["Next Sentence Prediction"]
                Q --> W["Linear Layer"]
                W --> X["Softmax<br>(IsNextSentence)"]
                X --> Y["Predicted Next Sentence Label"]
            end
        end

        subgraph Fine_Tuning_Tasks["Fine-Tuning Tasks (Example)"]
            direction LR
            F'["BERT Encoder Stack<br>(Fine-Tuned Weights)"] -- Output for each token --> Z["Sequence Classification<br>(Linear + Softmax on [CLS])"]
            F' -- Output for each token --> AA["Token Classification<br>(Linear + Softmax per Token)"]
            F' -- Output for two sequences --> BB["Question Answering<br>(Start & End Span Prediction)"]
            F' -- Output for two sequences --> CC["Sentence Pair Classification<br>(Linear + Softmax on [CLS])"]
        end

    end
    
````

DOI: [10.13140/RG.2.2.22192.67845](http://dx.doi.org/10.13140/RG.2.2.22192.67845)



---

![[BERT.svg]]




----


### Explanation of the BERT Architecture Diagram

The diagram illustrates the architecture of BERT (Bidirectional Encoder Representations from Transformers), which is primarily composed of a stack of Transformer encoders. Key components and processes are detailed below:

1.  **Input Sequence:** BERT takes a sequence of tokens as input, typically with special tokens:
    *   ` `**: Indicates the beginning of a sequence and is used for classification tasks.
    *   **`x`<sub>1</sub>, ..., x<sub>n</sub>**: The actual input tokens of the sequence.
    *   **` `**: Separates two sentences in tasks like Next Sentence Prediction.

2.  **Embeddings:** The input tokens are converted into embeddings through three types of embedding layers, which are then summed element-wise:
    *   **Token Embeddings:** Standard word/token embeddings that map each token in the vocabulary to a dense vector.
    *   **Segment Embeddings:** Used for tasks involving two sentences. Each token is embedded based on whether it belongs to the first or the second sentence.
    *   **Positional Embeddings:** Similar to the original Transformer, positional embeddings are added to incorporate information about the position of each token in the sequence. These can be learned or fixed.

3.  **Transformer Encoder Stack:** The core of BERT is a stack of `N` identical Transformer encoder layers. The number of layers (`N`), the hidden size, and the number of attention heads are the main hyperparameters of BERT models (e.g., BERT-base vs. BERT-large).

4.  **Encoder Layer:** Each encoder layer consists of two main sub-layers:
    *   **Multi-Head Self-Attention:** This mechanism allows the model to attend to different parts of the input sequence when processing each token. It involves parallel computation of multiple attention heads.
    *   **Position-wise Feed-Forward Network (FFN):** After the self-attention mechanism, each token's representation is passed through a feed-forward network independently. This network typically has two linear layers with a non-linear activation (e.g., GELU) in between.
    *   **Residual Connections and Layer Normalization:** Similar to the original Transformer, each sub-layer is followed by a residual connection (adding the input of the sub-layer to its output) and then Layer Normalization.

5.  **Pooler Layer:** The output of the ` ` token from the final encoder layer is passed through a linear layer followed by a `tanh` activation function. This produces a fixed-size vector representation of the entire input sequence, which is often used for classification tasks.

6.  **Pretraining Tasks:** BERT is pre-trained on two unsupervised tasks using a large corpus of text:
    *   **Masked Language Modeling (MLM):** Some percentage of the input tokens are randomly masked, and the model is trained to predict the original masked tokens based on the context of the unmasked tokens.
    *   **Next Sentence Prediction (NSP):** Given pairs of sentences, the model is trained to predict whether the second sentence is the subsequent sentence in the original document. (Note: The effectiveness of NSP has been debated in later research).

7.  **Fine-Tuning Tasks:** After pre-training, BERT can be fine-tuned on various downstream tasks by adding a task-specific output layer on top of the pre-trained encoder. Examples include:
    *   **Sequence Classification:** Using the output of the ` ` token for tasks like sentiment analysis.
    *   **Token Classification:** Using the output of each token for tasks like Named Entity Recognition (NER).
    *   **Question Answering:** Predicting the start and end positions of the answer span in a given context based on a question.
    *   **Sentence Pair Classification:** Using the ` ` token output for tasks like natural language inference.

### Key Differences from the Original Transformer Decoder

*   **Encoder-Only Architecture:** BERT exclusively uses the encoder part of the Transformer. There is no decoder component with masked self-attention and encoder-decoder attention.
*   **Bidirectional Attention:** The self-attention in BERT's encoder is bidirectional, meaning that when processing a token, the model can attend to all other tokens in the input sequence, both preceding and following it. This is in contrast to the masked self-attention in the Transformer decoder, which only allows attention to preceding tokens.
*   **Pretraining Objectives:** BERT's pretraining on MLM and NSP is a crucial aspect that allows it to learn rich contextualized representations.
*   **Special Tokens:** The use of ` ` and ` ` tokens is specific to BERT's input format and pretraining tasks.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---