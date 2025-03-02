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
title: Transformer Model - Optimized Diagram with Equations
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
graph TD
    %% Main Transformer Architecture %%
    subgraph Transformer_Model["Transformer Model"]
    style Transformer_Model fill:#e8f3fb,stroke:#005a9e,stroke-width:2px

        A["Input Sequence<br>(x<sub>1</sub>, ..., x<sub>n</sub>)"] --> B["Input Embeddings<br>(Embedding(x<sub>i</sub>))"]
        B --> C["Positional Encoding<br>(PE<sub>pos,2i</sub> = sin(pos/10000<sup>2i/d<sub>model</sub></sup>)<br>PE<sub>pos,2i+1</sub> = cos(pos/10000<sup>2i/d<sub>model</sub></sup>))"]
        C --> D["Encoder Stack<br>(N=6 Layers)"]

        %% Encoder Stack %%
        subgraph Encoder_Stack["Encoder Stack (N Layers)"]
        style Encoder_Stack fill:#d8e8ff,stroke:#005a9e,stroke-width:2px
            D1["Encoder Layer"] --> D2
            D2 --> D3
            D3 -->|Repeated N Times| D4
            D4 --> D5[Output to Decoder]
        end

        %% Encoder Layer %%
        subgraph Encoder_Layer["Encoder Layer"]
        style Encoder_Layer fill:#d4edda,stroke:#28a745,stroke-width:2px
            E1["Multi-Head Self-Attention<br>(MultiHead(Q, K, V))"] --> E2["Add & Norm<br>(LayerNorm(x + Sublayer(x))"]
            E2 --> E3["Position-wise Feed-Forward Network<br>(FFN(x) = max(0, xW<sub>1</sub> + b<sub>1</sub>)W<sub>2</sub> + b<sub>2</sub>)"]
            E3 --> E4["Add & Norm<br>(LayerNorm(x + Sublayer(x))"]
        end

        %% Connecting Encoder Layer %%
        D1 --> E1
        E4 -->|Output to Next Layer| D2

        %% Decoder Stack %%
        subgraph Decoder_Stack["Decoder Stack (N Layers)"]
        style Decoder_Stack fill:#fdf3e6,stroke:#d39e00,stroke-width:2px
            I1["Decoder Layer"] --> I2
            I2 --> I3
            I3 -->|Repeated N Times| I4
            I4 --> I5[Output to Linear & Softmax]
        end

        %% Decoder Layer %%
        subgraph Decoder_Layer["Decoder Layer"]
        style Decoder_Layer fill:#fff3cd,stroke:#ffc107,stroke-width:2px
            J1["Masked Multi-Head Self-Attention<br>(MultiHead(Q, K, V))"] --> J2["Add & Norm<br>(LayerNorm(x + Sublayer(x))"]
            J2 --> J3["Encoder-Decoder Attention<br>(MultiHead(Q from Decoder, K/V from Encoder))"]
            J3 --> J4["Add & Norm<br>(LayerNorm(x + Sublayer(x))"]
            J4 --> J5["Position-wise Feed-Forward Network<br>(FFN(x) = max(0, xW<sub>1</sub> + b<sub>1</sub>)W<sub>2</sub> + b<sub>2</sub>)"]
            J5 --> J6["Add & Norm<br>(LayerNorm(x + Sublayer(x))"]
        end

        %% Connecting Decoder Layer %%
        I1 --> J1
        J6 -->|Output to Next Layer| I2

        %% Output Embeddings and Softmax %%
        I5 --> K["Linear Transformation<br>(z = Wx + b)"]
        K --> L["Softmax<br>(softmax(z<sub>i</sub>) = e<sup>z<sub>i</sub></sup> / Σ<sub>j</sub>e<sup>z<sub>j</sub>)"]
        L --> M["Output Sequence<br>(y<sub>1</sub>, ..., y<sub>m</sub>)"]

    end

    %% Scaled Dot Product Attention %%
    subgraph Scaled_Dot_Product_Attention["Scaled Dot-Product Attention"]
    style Scaled_Dot_Product_Attention fill:#c8e6c9,stroke:#43a047,stroke-width:2px
        N1["Input (Q, K, V)"] --> N2["Compute QK<sup>T</sup><br>(Dot Product)"]
        N2 --> N3["Scale by 1/√d<sub>k</sub><br>(Avoid Vanishing/Exploding Gradients)"]
        N3 --> N4["Apply Softmax<br>(softmax(QK<sup>T</sup>/√d<sub>k</sub>))"]
        N4 --> N5["Weight Values (V)<br>(Attention = softmax(...)V)"]
    end

    %% Multi-Head Attention %%
    subgraph Multi_Head_Attention["Multi-Head Attention"]
    style Multi_Head_Attention fill:#e8f3fb,stroke:#005a9e,stroke-width:2px
        O1["Input (Q, K, V)"] --> O2["Linear Projections<br>(QW<sup>Q</sup>, KW<sup>K</sup>, VW<sup>V</sup>)"]
        O2 --> O3["Apply Scaled Dot-Product Attention<br>(h Parallel Heads)"]
        O3 --> O4["Concatenate Heads<br>(Concat(head<sub>1</sub>, ..., head<sub>h</sub>)"]
        O4 --> O5["Final Linear Projection<br>(Apply W<sup>O</sup>)"]
    end

    %% Connecting Attention Mechanisms %%
    E1 -.-> N1
    J1 -.-> N1
    J3 -.-> O1

```

----


### Optimized Diagram Explanation

This optimized Mermaid diagram strategically organizes all components of the Transformer model while ensuring the connections between components are clearly represented. It also includes mathematical equations where appropriate for a detailed understanding.

---

### Key Features and Structure:

#### **Main Architecture:**
1. **Input Sequence:**
   - The sequence (e.g., words or tokens) is passed through an embedding layer (`Embedding(x_i)`), followed by positional encoding to add order information.
   - Formula for Positional Encoding is displayed:
     - \( PE_{pos, 2i} = \sin\left(\frac{pos}{10000^{\frac{2i}{d_{model}}}}\right) \)
     - \( PE_{pos, 2i+1} = \cos\left(\frac{pos}{10000^{\frac{2i}{d_{model}}}}\right) \)

2. **Encoder Stack:**
   - Consists of **N layers**, where each layer contains:
     - **Multi-Head Self-Attention:** Captures relationships within the input sequence.
     - **Position-wise Feed-Forward Network (FFN):** Applies transformations independently at each position.
     - Residual connections and layer normalization ensure stable training.

3. **Decoder Stack:**
   - Mirrors the encoder stack but includes additional **Masked Multi-Head Attention** and **Encoder-Decoder Attention** to process the target sequence and leverage encoder outputs.
   - Masking ensures that predictions depend only on past tokens.

4. **Output Embeddings and Softmax:**
   - Outputs from the final decoder layer pass through a linear layer and a softmax function:
     - \( softmax(z_i) = \frac{e^{z_i}}{\sum_j e^{z_j}} \)
   - Produces probabilities over the vocabulary for generating the output sequence.

---

#### **Attention Mechanisms:**
1. **Scaled Dot-Product Attention:**
   - Core attention operation:
     - \( \text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V \)
   - Steps:
     - Compute dot product \( QK^T \).
     - Scale by \( \frac{1}{\sqrt{d_k}} \).
     - Apply softmax for normalization.
     - Weight values \( V \) by attention scores.

2. **Multi-Head Attention:**
   - Extends scaled dot-product attention:
     - Projects \( Q, K, V \) into multiple subspaces using learnable weight matrices \( W^Q, W^K, W^V \).
     - Computes attention independently in parallel across heads.
     - Concatenates results and applies a final projection \( W^O \).

---

### Strategic Optimizations:
1. **Hierarchical Organization:** Clearly separates components into `Encoder`, `Decoder`, `Scaled Dot-Product Attention`, and `Multi-Head Attention`.
2. **Equations Integrated into Components:** Key equations (e.g., attention mechanism, FFN transformations) are embedded directly within the relevant sections.
3. **Connections Between Components:** Arrows show data flow explicitly between encoder-decoder stacks and the attention mechanisms.
4. **Subgraph Modularity:** Each component is isolated in its subgraph (e.g., `Encoder Layer`, `Decoder Layer`, `Scaled Dot-Product Attention`) for better readability.

---

This diagram is designed to provide a complete and interconnected view of the Transformer model while remaining modular for individual focus on components like attention mechanisms or specific layers in the architecture. The mathematical precision adds depth for advanced readers or practitioners.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---