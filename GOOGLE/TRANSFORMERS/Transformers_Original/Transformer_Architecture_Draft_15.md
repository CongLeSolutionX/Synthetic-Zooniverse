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
title: Transformer Model - Optimized Diagram 
config:
  layout: elk
  look: handDrawn
  theme: default
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
    style TB fill:#f9f,stroke:#333,stroke-width:4px
    TB[Textual Information] --> TI[Input Sequence]
    TI --> IE[Input Embeddings]
    IE --> PE[Positional Encoding]
    PE --> ES[Encoder Stack]
    
    subgraph "Encoder Stack (N layers)"
        ES --> E1[Encoder Layer 1]
        ES --> E2[Encoder Layer 2]
        ES -.-> EN[Encoder Layer N]
    end
    
    E1 -. "Multi-Head Attention & FFN" .-> E2
    EN --> ED[Encoded Representation]
    
    ED --> DS[Decoder Stack]
    subgraph "Decoder Stack (N layers)"
        DS --> D1[Decoder Layer 1]
        DS --> D2[Decoder Layer 2]
        DS -.-> DN[Decoder Layer N]
    end

    D1 -. "Masked Multi-Head Attention & FFN" .-> D2
    ED -. "Encoder-Decoder Attention" .-> DN
    DS --> TO[Target Output Embeddings]
    TO --> PS[Positional Encoding]
    PS --> LF[Linear & Softmax]
    
    %% Encoder Layer Details
    E1 -->|"Self-Attention & Add&Norm"| SA1["Self-Attention"]
    E1 -->|"FFN & Add&Norm"| FFN1["Feed-Forward"]
    
    %% Decoder Layer Details
    D1 -->|"Masked Self-Attention & Add&Norm"| MSA1["Masked Self-Attention"]
    D1 -->|"Enc-Dec Attention & Add&Norm"| EDA1["Enc-Dec Attention"]
    D1 -->|"FFN & Add&Norm"| FFND1["Feed-Forward"]
    
    %% Equations
    SA1 -->|"Q, K, V"| EQ["Attention(Q, K, V) = softmax(QK^T / sqrt(d_k))V"]
    MSA1 -->|"Q, K, V, Mask"| EQM["Masked Attention(Q, K, V)"]
    EDA1 -->|"Q, K from Encoder, V"| EQEDA["Attention(Q, Encoder K, Encoder V)"]
    
    %% Final Output
    LF --> OS["Output Sequence (y_1, ..., y_m)"]
    
    %% Styling for equations
    class EQ,EQM,EQEDA equation;
    
    classDef encoder fill:#bbf,stroke:#00f;
    classDef decoder fill:#fbf,stroke:#f0f;
    classDef equation fill:#ff6,stroke:#000;
    
    class ES,D1 encoder;
    class DS,DN decoder;
    
```

---

### Key Aspects and Strategic Optimizations:

- **Hierarchical Structure:** The architecture is divided into two main subgraphs: Encoder Stack and Decoder Stack, with further breakdowns into individual layers. This visual hierarchy enhances understanding.
  
- **Sequential Flow:** Arrows clearly indicate the sequential flow of information through the model, from input to output.

- **Encoder and Decoder Layers:** Distinct sections for Encoder and Decoder layers elucidate their roles and internal components. 

- **Attention Mechanisms:** Key equations for the attention mechanisms (Self-Attention in the encoder, Masked Self-Attention, and Encoder-Decoder Attention in the decoder) are depicted right where they are applied to emphasize their importance.

- **Equations:** Specific attention mechanism equations are presented next to their respective processes. This highlights the Transformer's core mathematical operations without cluttering the overall architecture flow.

- **Component Connections:** The diagram ensures all components are properly connected, illustrating dependencies between layers and between the encoder and decoder stacks.

- **Visual Design:** The use of color coding (optional in Mermaid but described here for context) differentiates between encoder-related components, decoder-related components, and equations. This visual differentiation aids in quickly grasitating the distinct parts of the model.

### Conclusion:

This optimized Mermaid diagram of the Transformer model strategically arranges components to emphasize clarity and connectivity. It highlights the model's architecture and core mathematical principles underlying its operation, providing a comprehensive yet understandable overview of the Transformer mechanism.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---