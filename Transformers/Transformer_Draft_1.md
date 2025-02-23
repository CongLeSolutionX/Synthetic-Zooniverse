---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Transformers
> This content is dual-licensed under your choice of the following licenses:
> 1.  **MIT License:** For the code implementations in Swift and Mermaid provided in this document.
> 2.  **Creative Commons Attribution 4.0 International License (CC BY 4.0):** For all other content, including the text, explanations, and the Mermaid diagrams and illustrations.

---

Below is my personal notes on the topics and I might gather information from various sources, which I wil cite accordingly.

---


## 1. Overview: The Transformer's Role

```mermaid
%%{
  init: {
    'theme': 'dark',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Transformer] --> B{Core Function};
    B --> C[Sequence Modeling & Generation];
    C --> C1[Developed by Google];
    C --> C2[Based on Attention Mechanism];
    C --> C3[Advantage: No Recurrent Units, so it requires less training time than RNNs];
    A --> D{Applications};
    D --> D1[NLP - Machine Translation, Text Summarization, etc.];
    D --> D2[Computer Vision - Vision Transformers];
    D --> D3[Speech Recognition];
    D --> D4[Robotics];
    D --> D5[Multimodal Learning];

    classDef detail fill:#f9f,stroke:#333,stroke-width:2px
```

**Description:** Establishes the Transformer as a key architecture for sequential data. It highlights applications besides NLP such as CV, speech and robotics.

----

## 2. Historical Context: From RNNs to Transformers

```mermaid
%%{
  init: {
    'theme': 'dark',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Sequence Modeling Before Transformers] --> B{Key Architectures:};
    B --> B1["Early: Elman network (1990)"];
    B1 --> B2{"Problem: Vanishing Gradient"};
    B --> B3["Breakthrough: LSTM (1995)"];
    B3 --> B4{"Innovations"};
    B4 --> B4a[Overcame Vanishing Gradient];
    B4 --> B4b["Attention Mechanism (Multiplicative Units)"];
    B4 --> B5["Drawbacks: Sequential Processing; Cannot Parallelize"];
    A -->C[Transformer Architecture];
    C-->C1[Developed by Google in 2017];
    C-->C2[Attention Is All You Need];

    classDef detail fill:#f9f,stroke:#333,stroke-width:2px
    
```

**Description:** Places the Transformer in the historical progression of sequence modeling. Introduces the need for better architectural performance than LSTMs.

----


## 3. Transformer's Core Principle: The Attention Mechanism

```mermaid
%%{
  init: {
    'theme': 'dark',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Attention Mechanism (Core)"] --> B{"Scaled Dot-Product"};
    B --> C["Queries (Q), Keys (K), Values (V)"];
    C --> C1[Derived from Input];
    C --> C2[Query attends to Key];
    C --> D["Attention Score = softmax(QK^T / sqrt(d_k)) * V"];
    D --> D1["Scales Dot Product (d\_k stabilizes gradients)"];
    D --> E{"Key Properties of self Attention heads and multihead attention which can be used for different attentions on inputs"};
    E --> E1["Allows parallel processing of the full sequence context for efficient contextualization"];

   classDef detail fill:#f9f,stroke:#333,stroke-width:2px
   
```

**Description:** Isolates the core computational unit, "scaled dot-product".  It breaks down the input vector and its role within the Transformer. Important in relation to multi head attention.

----

## 4. Encoder-Decoder Architecture: The Transformer's Blueprint

```mermaid
%%{
  init: {
    'theme': 'dark',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f3ff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A{"Encoder-Decoder Architecture"} --> B[Encoder];
    B --> B1[Processes Input Tokens Together];
    B --> B1a[Creates Contextualized Representations];
    B1a --> B1b[Mixing information via self-attention];
    B --> C[Decoder];
    C --> C1["Processes Encoder Output & its Output Tokens"];
    C --> C1A["Has 2 or 3 attention sublayers - cross and self (masked)"];
    C --> D["Encoder & Decoder Building Blocks: Stacked Layers"];
    D --> E{Each Layer};
    E --> EA[Self-Attention Mechanism];
    E --> EB[Feedforward Neural Network];

    classDef detail fill:#f9f,stroke:#333,stroke-width:2px
    
```


**Description:** Explains the architecture used in the original transformer. Shows the role of each sublayer, the use of self, cross - attentions and FFN.

----

## 5. Deep Dive: The Encoder Layer

```mermaid
%%{
  init: {
    'theme': 'dark',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Encoder Layer] --> B{Components:};
    B --> C[Self-Attention];
    C --> C1[Input: Sequence of Vectors];
    C --> C2[Output: Intermediate Sequence of Vecctors];
    B --> D["Feedforward Network (FFN)"];
    D --> D1[Applies to Each Vector Individually];
    D --> E["Residual Connections & Layer Normalization (for Performance)"];
    E --> F[Used inside and outside blocks];

    classDef detail fill:#f9f,stroke:#333,stroke-width:2px
    
```


**Description:** Breaks down what the encoder constitutes of.

----

## 6. Deciphering Sublayers: Encoder (simplified)

```mermaid
%%{
  init: {
    'theme': 'dark',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Sublayer<br>(Feed Forward)"] --> B{Input};
    B --> C[x];
    B --> C1["Dimension: d_emb or d model in the paper"];
    A --> D["FFN(x)"];
    D --> E{"Computation:<br>FFN(x) =  ϕ(x*W^(1) + b^(1)) * W^(2)+ b^(2)"};
    D -->F["Intermediate Size or Feedforward Size (4 * d\_emb)"];
    A --> G[Output];
    G --> H["Dimension: d\_emb"];

    classDef detail fill:#f9f,stroke:#333,stroke-width:2px
    
```


----

## 7. Feedforward Network (FFN)

```mermaid
%%{
  init: {
    'theme': 'dark',
     'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A{"Feedforward Network (FFN)"} --> B[Two-Layered Multilayer Perceptron];
    B --> C["Function = FFN(x) = ϕ(xW(1)+b(1))*W(2)+b(2)"];
    C --> D{Layers};
    D --> D1[x multiplied by weight matrix + bias, then activated];
    D --> D2[activation function as ϕ];
    
    D2 --b/2--> D3[original used ReLu];

    classDef detail fill:#f9f,stroke:#333,stroke-width:2px
```

**Description:** Focuses the calculation made, size, and activation calculations on the Feedward Network.

----

## 8. Self-Attention Expanded: Attention with scaled dot-product

```mermaid
%%{
  init: {
    'theme': 'dark',
    'layout': 'elk',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Scaled Dot-Product Attention"]
    B{"Inputs:<br>Query (Q), Key (K), Value (V) Sequences"}:::detail
    C["Create Weights"]
    CA["Matrix Q = XQWQ"]
    CB["Matrix K = XK\W^K"]
    CC["Matrix V = XV\W^V"]
    D{"Calculation"}
    E["Attention Weights:<br> $$a\_ij = dot\_product(Qi, Kj)$$ "]:::detail
    F["Normalize weights, scaled to stabilize gradients <br> ( a\_ij / sqrt(the key) is dot product between qi and kj)"]:::detail

    H["Attention with Softmax"]
    H1["Attention (Q, K ,V )<br> softmax⁡((Q* Kᵀ)/sqrt(d\_k)) V)"]:::detail
    G["Output for token i:<br>weighted sum of value vectos ai j i  = Attention(Qi,Kj,V)"]:::detail

    A --> B
    B --> C
    C --> CA
    C --> CB
    C --> CC
    A --> D
    D --> E
    D --> F
    D --> G

    subgraph Formulas
        H -- One Large Matrix Calculation (for Training) --> H1
      end

    classDef detail fill:#f339,stroke:#333,stroke-width:2px
    
```


**Description:** Isolate the computational unit, "scaled dot-product attention" It highlights inputs, calculations for finding weight, and calculating the scaled result.

----



## 9. Encoder Calculations

```mermaid
%%{
  init: {
    'theme': 'dark',
    'layout': 'elk',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Key Encoder operations"]
    B{"Input Token Embedding, Positional Encoding and Self- Attention"}
    C{"Operations"}
    
    A --> B
    A --> C

    %%  Given Input as vectors, we will get the following
    C -->  CA["$$H_0, h_1, h_2 ....$$"]:::detail
    CA --> CB["combine in H"]:::detail
    CB --> CC["encoderLayer(H)"]:::detail
    CC --> CD[Multi Head Attention to Feed Forward]:::detail
    
    classDef detail fill:#f919,stroke:#333,stroke-width:2px

```

----


## 10. Decoder Expanded: Decoding steps

```mermaid
%%{
  init: {
    'theme': 'dark',
    'layout': 'elk',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Key sublayers in Encoder Layer"]
    B{"Decoder Functions"}
    BC["MaskedMultiheadedAttention<br>(H, H, H)"]:::detail
    BD["FFN - MultiheadedAttentionH, HE, HE)"]:::detail

    C{"Un-embedding to Probabilities, Unembedding Matrix"}
    CE["Final Token Output"]


    A --> B
    B --> BC
    BC --> BD
    A --> C
    A --> CE
    
classDef detail fill:#f912,stroke:#333,stroke-width:2px

```

## 11. Deep Dive: Transformer's Full Architecture

```mermaid
%%{
  init: {
    'theme': 'dark',
    'layout': 'elk',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Full Transformer] --> B{Layers:<br>Encoder Layers xN, Decoder Layers xN};
    B --> C[Encoder:<br>Input -> Embedding -> Positional Encoding -> N Encoder Layers -> Output];
    B --> D[Decoder: <br>Start token + Output -> Embedding -> Positional Encoding -> N Decoder Layers -> Un-embedding -> Output Probabilities];
    C --> CEA[Encoder<br>- Process Entire input at once. Can pay attention to every other token <br>- uses all to all attention. No casusal mask needed];
    D --> DEA[Decoder<br>- Autoregressive, causally masked.<br>Token cannot attend to other tokes not yer calculated .];


   classDef detail fill:#f9f,stroke:#333,stroke-width:2px
   
```


**Description:** Presents one encoder and decoder (original case) architecture and the functionality including residual connection  and layer normalization steps within each block and connections together. This shows input, output, and the flow as vector data from layer embedding.

----

## 12. Variants and Enhancements

```mermaid
%%{
  init: {
    'theme': 'dark',
    'layout': 'elk',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Adapted Architectures] --> B{"Based on original one<br>(with minor change)"};
    B --> B1["Encoder-Only Transformers<br>(e.g., BERT)"]
    B --> B2["Decoder-Only Transformers<br>(e.g., GPT)"]
    B --> B3["Encoder-Decoder Tranformers<br>(e.g. T5)"]

    A --> C{"Training Enhancements"};
    C --> D1[alternate Activation Functions];
    C --> D1A["GELU or SwiGLU"]
    C --> D2[alternative Normalizations]

    A --> E{Positional Encoding}
    E --> EA["learnable Positional Encoding"]
    E --> EB[RoPE]
    E --> EC[ALiBi]
    E --> ED["Relative position Encodoing B =B i,j =Bi\’, j\’  whenever if - j =i/’=j"]
    
    C --> CC["Normilization with before (pre-LN), after sublayer (post LN)"]

    style EA fill:#c922
    style EC fill:#f224
    style ED fill:#c921
    classDef detail fill:#f912,stroke:#333,stroke-width:2px
    
```

**Description:** Presents several variations possible in Transformers architectures: (Encoder, Decoder, etc..) and different approach to solve the difficulty/pain points in various scenarios. This highlights different function modifications.

----

## 13 Tokenizing

```mermaid
---
config:
  layout: elk
  look: handDrawn
  theme: defaults
---
graph LR
    A["Transform Tokenization"];
    B{"Tokenize(convert texts into vectors)"}
    C["The conversion between test and tokens is tokenizer"]
    D["$$tokenizer = vocabulary + method (byte pair encoding, word piece, and  sentencePiece)  n_vocabulary (size of vocabulary)$$"]:::detail


    A --> B
    A --> C
    A --> D

classDef detail fill:#f933,stroke:#333,stroke-width:2px

```

----



## 13. Attention Variations for Efficient Implementation

```mermaid
%%{
  init: {
    'theme': 'dark',
    'layout': 'elk',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Efficient Implementations"] --> B{"Inference Efficiency (during generation)"}
    B --> C[KV Caching];
    C --> CA[PagedAttention = Memory Paging]
    C -->CB[Prompt Caching  = save K & V vectors in prompts in disk]

    A --> D{"Multihead attention (speeding computing):<br> Multi-Query, Groped Query and Multi Headed Latent Attention Method"}
    D --> DA["Multi-Query Attention, which has one W^K,W^V instead of W i ^{k,v) : MQA - speeds up inference"]

    D --> DB["Grouped-Query Attention (GQA,  partitions with related keys, val pairs) One MQA"]
    D --> DC["DeepSeek - Multi Headed Attention and Mult Latent Attention (MLA - low rank approximation"]
    D --> DC["Low KV cache memory"]
    A --> E["Speculative deconding: speeds up token decoding"]
    E --> EA[" Use GPT for speculative token calculation, then larger GPT will verify them quickly - is shorter with some added calcutions (each stage is fast/slow)"]

   style EA fill:#ad32
   style DC fill:#f39
   
```


**Description:** Focuses for efficient implementation using the transformer model (fast attention calculation ,etc.);

----

## 14. Sub-Quadratic Transformer Approached for Long Inputs

```mermaid
%%{
  init: {
    'theme': 'dark',
    'layout': 'elk',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    A["Sub-Quadratic Transformers"] -- Memory/Compute with Long Inputs --> B{"Solutions"}
    B --> C["Alternative Attention<br>- reduce comp or memory size from O_2 to smaller"]
    C --> CA["Reformer by Localize Hashing + Reversible Layer<br>( O(NlogN))"]
    C --> CB["Sparse transformer uses graphs <br>(BigBird- Random network) O(1)"]
    C --> CC["Attention-free - K = V"]
    C --> D["Flash Attention"]

    D --> E["Matrix multiplication blocks inside caches + minimize data copy GPU to achieve performance of performance"]

 classDef detail fill:#f9f,stroke:#333,stroke-width:2px
 
```

----

## Method / Algorithm Analysis

```mermaid
%%{
  init: {
    'theme': 'dark',
    'layout': 'elk',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
	A(Transformer) --> B{Tokenizer}
	B --> C(Embeddings)
	C --> D(Positional Encoding)
	D --> E{Multi Head Self Attention}
    E --> F(Normalizer 1+Residual Connection)
    F --> G(Feed Foward Networks)
    G --> H(Normalizer 2 + Residual)
    H --> D
    D --> I(Decoder output)
    
    style A fill:#f935,stroke:#333,stroke-width:2px
    style B fill:#f3f5,stroke:#333,stroke-width:2px
    style C fill:#f3f5,stroke:#333,stroke-width:2px
    style D fill:#e935,stroke:#333,stroke-width:2px
    style F fill:#e935,stroke:#333,stroke-width:2px
    style G fill:#f3f5,stroke:#333,stroke-width:2px
    style I fill:#e3e5,stroke:#333,stroke-width:2px
    style E fill:#f2f2,stroke:#333,stroke-width:2px
    style H fill:#e3ee,stroke:#333,stroke-width:2px
   
    click E "https://en.wikipedia.org/wiki/Attention_(machine_learning)#Multi-head_attention" "Mult Head Attention Explanation - Click to see how it works"

```

These diagrams and illustrations are designed to provide a complete understanding of the Transformer architecture. They are also consistent in formatting and labeling, which could prove extremely useful as direct setting elements in any AI agent.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---