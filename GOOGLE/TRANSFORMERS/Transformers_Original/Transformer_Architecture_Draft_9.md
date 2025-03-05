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
title: Optimized Transformer Architecture
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%{
  init: {
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD

  %% Input and Embeddings
  A["Input Sequence<br>(x₁, …, xₙ)"]
  B["Input Embeddings<br>E(xᵢ)"]
  C["Positional Encoding<br>PE(pos,2i)=sin(pos/10000^(2i/d_model))<br>PE(pos,2i+1)=cos(pos/10000^(2i/d_model))"]
  
  A --> B
  B --> C
  
  %% Encoder Stack: N layers (illustrated as one representative layer)
  D["Encoder Stack<br>(N layers)"]
  C --> D

  subgraph Encoder_Layer["Encoder Layer <br> (Repeated N times)"]
    %% direction TD
    E["Multi-Head Self-Attention<br>headᵢ = Attention(QWᵢᴾ, KWᵢᴷ, VWᵢⱽ) <br> MultiHead(Q,K,V) = Concat(head₁, …, head_h)Wᴼ"]
    F["Add & Norm<br>LayerNorm(x + Sublayer(x))"]
    G["Position-wise Feed-Forward<br>FFN(x)=max(0, xW₁+b₁)W₂+b₂"]
    H["Add & Norm<br>LayerNorm(x + FFN(x))"]

    D --> E
    E --> F
    F --> G
    G --> H
  end
  
  %% Encoder Output
  I["Encoder Output<br>(z₁, …, zₙ)"]
  H --> I
  
  %% Decoder Stack: N layers (illustrated as one representative layer)
  J["Decoder Stack<br>(N layers)"]
  I --> J_enc[Encoder-Decoder Connection]
  
  %% For decoder input, we use target sequence shifted right:
  K["Target Sequence<br>(y₁, …, yₘ₋₁)"]
  L["Target Embeddings<br>E(yᵢ)"]
  M[Positional Encoding<br>same as for inputs]
  K --> L
  L --> M
  
  subgraph Decoder_Layer["Decoder Layer <br> (Repeated N times)"]
    %% direction TD
    N["Masked Multi-Head Self-Attention<br>(with masking to block future tokens)"]
    O["Add & Norm<br>LayerNorm(x + Sublayer(x))"]
    P["Encoder-Decoder Attention<br>Attention(Q, K_enc, V_enc)"]
    Q["Add & Norm<br>LayerNorm(x + Sublayer(x))"]
    R["Position-wise Feed-Forward<br>FFN(x)=max(0,xW₁+b₁)W₂+b₂"]
    S["Add & Norm<br>LayerNorm(x + Sublayer(x))"]
    
    M --> N
    N --> O
    %% Use the encoder outputs as keys and values in the next attention sub-layer:
    I --> P
    O --> P
    P --> Q
    Q --> R
    R --> S
  end
  
  J --> S
  
  %% Final Linear and Softmax
  T["Linear Projection<br>(project to vocabulary dimension)"]
  U["Softmax Layer<br>softmax(zᵢ)=e^(zᵢ) / Σⱼ e^(zⱼ)"]
  
  S --> T
  T --> U
  U --> V["Output Sequence<br>(y₁, …, yₘ)"]
  
  %% Scaled Dot-Product Attention (used inside multi-head attention)
  subgraph SDPA["Scaled Dot-Product Attention"]
    %% direction TD
    W["Compute Dot Product<br>(QKᵀ)"]
    X["Scale by 1/√dₖ<br>(QKᵀ/√dₖ)"]
    Y["Apply Softmax<br>softmax(QKᵀ/√dₖ)"]
    Z["Weighted Sum with V<br>= softmax(QKᵀ/√dₖ)V"]
  end
  %% Linking Multi-Head Attention components with SDPA
  E ---|For each head: Q, K, V| SDPA
  
  %% Encoder-Decoder Attention also uses SDPA:
  P ---|Uses Q from decoder & K,V from encoder| SDPA
  
```

-----

### Diagram Explanation

1. **Input Processing:**  
   • The input sequence (x₁, …, xₙ) is converted into embeddings E(xᵢ) and added with sinusoidal positional encodings (using the equations shown).

2. **Encoder Stack:**  
   • The encoder consists of N stacked identical layers.  
   • Each layer applies multi-head self-attention (with the multi-head equation shown) and then a residual connection with layer normalization.  
   • A position-wise feed-forward network follows, again with a residual connection.

3. **Encoder Output:**  
   • The final output of the encoder (z₁, …, zₙ) is fed into the decoder’s encoder-decoder attention sub-layer.

4. **Decoder Stack:**  
   • The target sequence (shifted right) is embedded and combined with positional encodings.  
   • Each decoder layer begins with masked multi-head self-attention to prevent information flow from future tokens.  
   • The encoder-decoder attention sub-layer then allows the decoder to attend to the encoder’s output.  
   • A final feed-forward network with residual connection completes each decoder layer.

5. **Output Generation:**  
   • The decoder’s final output is passed through a linear projection and softmax layer to generate a probability distribution over the vocabulary and produce the output sequence.

6. **Scaled Dot-Product Attention (SDPA):**  
   • Shown as a separate subgraph, it details the internal computations used in both self-attention and encoder-decoder attention:
     - Compute QKᵀ, scale by 1/√dₖ, apply softmax, and compute the weighted sum with V.

Every component is connected sequentially to show the full flow from input processing through encoder and decoder layers to the final prediction. This optimized diagram integrates the essential equations and connections to provide a complete view of the Transformer model.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---