---
created: 2025-02-27 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://arxiv.org/abs/1706.03762"
---



# Transformer Architecture Drafts
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Transformer Architecture - A Draft Comprehensive Diagram





```mermaid
---
title: Optimized Transformer Architecture - Comprehensive Overview
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%{
  init: {
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#007acc',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#005a9e',
      'lineColor': '#f90',
      'secondaryColor': '#e8f3fb',
      'tertiaryColor': '#fff'
    }
  }
}%%
%%%%%%%% Mermaid version v11.4.1-b.14
graph LR
    subgraph Transformer_Architecture["Transformer Architecture"]
    style Transformer_Architecture fill:#e8f3fb,stroke:#005a9e,stroke-width:2px

        A["Input Sequence<br>(x<sub>1</sub>, ..., x<sub>n</sub>)"] --> B["Input Embeddings<br>(Embedding(x<sub>i</sub>))"]
        B --> C["Positional Encoding<br>(PE)"]
        C --> D["Encoder Stack<br>(N=6 Layers)"]

        subgraph Encoder_Layer["Encoder Layer (Layer Norm & Residuals)"]
        style Encoder_Layer fill:#d8e8ff,stroke:#005a9e,stroke-width:2px
            E["Multi-Head Self-Attention<br>(MultiHead)"]
             E_Q["Queries (Q)"] --"Input from<br>Prev. Layer"--> E
             E_K["Keys (K)"] --"Input from<br>Prev. Layer"--> E
             E_V["Values (V)"] --"Input from<br>Prev. Layer"--> E
            E --> F["Add & Norm 1<br>(LayerNorm)"]
            F --"+<br>Input from<br>Self-Attention"--> G["Residual Connection 1"]
            G --> H["Position-wise FFN<br>(FFN)"]
             H_IN["Input"]-- G --> H
            H --> I["Add & Norm 2<br>(LayerNorm)"]
            I --"+<br>Output from<br>FFN"--> J["Residual Connection 2"]
            J --> K["Output<br>to Next Layer"]

            C --> E_Q
            C --> E_K
            C --> E_V
            J -->|Output to Next Layer| D
        end

        D --> L["Decoder Stack<br>(N=6 Layers)"]

        subgraph Decoder_Layer["Decoder Layer (Layer Norm & Residuals)"]
        style Decoder_Layer fill:#d8e8ff,stroke:#005a9e,stroke-width:2px
            M["Masked Multi-Head<br>Self-Attention<br>(Masked MultiHead)"]
             M_Q["Queries (Q)"] --"Input from<br>Prev. Layer"--> M
             M_K["Keys (K)"] --"Input from<br>Prev. Layer"--> M
             M_V["Values (V)"] --"Input from<br>Prev. Layer"--> M
            M --> N["Add & Norm 1<br>(LayerNorm)"]
            N --"+<br>Input from<br>Masked Self-Attn"--> O["Residual Connection 1"]
            O --> P["Encoder-Decoder<br>Attention<br>(MultiHead)"]
             P_Q["Queries (Q)"] -- O --> P
             P_K["Keys (K)"] --"Encoder Output"--> P
             P_V["Values (V)"] --"Encoder Output"--> P
            P --> Q["Add & Norm 2<br>(LayerNorm)"]
            Q --"+<br>Input from<br>Enc-Dec Attn"--> R["Residual Connection 2"]
            R --> S["Position-wise FFN<br>(FFN)"]
             S_IN["Input"]-- R --> S
            S --> T["Add & Norm 3<br>(LayerNorm)"]
            T --"+<br>Output from<br>FFN"--> U["Residual Connection 3"]
            U --> V["Output to<br>Next Layer"]

            W --> M_Q
            W --> M_K
            W --> M_V
            D --> P_K
            D --> P_V
            U -->|Output to Next Layer| L
        end

        L --> AA["Linear Layer"]
        AA --> BB["Softmax<br>(Output Probabilities)"]
        BB --> CC["Output Sequence<br>(y<sub>1</sub>, ..., y<sub>m</sub>)"]

        A --> W["Target Sequence<br>(Offset by 1)<br>(y<sub>1</sub>, ..., y<sub>m-1</sub>)"]
        W --> X["Target Embeddings<br>(Embedding(y<sub>i</sub>))"]
        X --> Y["Positional Encoding<br>(PE)"]
        Y --> M_Q
        Y --> M_K
        Y --> M_V
        D --> P_K
        D --> P_V
    end

    subgraph Attention_Mechanism["Attention Mechanism"]
    style Attention_Mechanism fill:#c8e6c9,stroke:#43a047,stroke-width:2px
        Z["Multi-Head Attention<br>(MultiHead)"] --> Z1["Linear Projections<br>(W<sup>Q</sup>, W<sup>K</sup>, W<sup>V</sup>)"]
        Z1 --> Z2["Scaled Dot-Product<br>Attention Heads<br>(h heads)"]
         subgraph Scaled_Dot_Product_Attention["Scaled Dot-Product Attention"]
         style Scaled_Dot_Product_Attention fill:#e8f5e9,stroke:#43a047,stroke-width:1px
             Z2 --> Z3["Queries, Keys, Values<br>(Q<sub>i</sub>, K<sub>i</sub>, V<sub>i</sub>)"]
             Z3 --> Z4["Dot Product<br>(Q<sub>i</sub>K<sub>i</sub><sup>T</sup>)"]
             Z4 --> Z5["Scale<br>(/ √d<sub>k</sub>)"]
             Z5 --> Z6["Softmax<br>(Weights)"]
             Z6 --> Z7["Weighted Values<br>(Softmax(QK<sup>T</sup>/√d<sub>k</sub>)V<sub>i</sub>)"]
             Z7 --> Z2
         end
        Z2 --> Z8["Concatenate Heads"]
        Z8 --> Z9["Output Projection<br>(W<sup>O</sup>)"]
        Z9 --> Z["Output"]
    end

    E --> Attention_Mechanism
    M --> Attention_Mechanism
    P --> Attention_Mechanism
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---