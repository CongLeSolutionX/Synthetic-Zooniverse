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


## Optimized Transformer Architecture Overview with Mermaid

```mermaid
---
title: Optimized Transformer Architecture Overview with Mermaid
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
    classDef default fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef component fill:#bbdefb,stroke:#1e88e5;
    classDef attention fill:#c8e6c9,stroke:#2e7d32;
    classDef embedding fill:#fff3e0,stroke:#fb8c00;
    classDef operation fill:#ffcdd2,stroke:#d32f2f;
    classDef sublayer fill:#e1bee7,stroke:#8e24aa;
    
    %% Input and Output sequences
    inputSeq("Input Sequence <br> (x₁, ..., xₙ)"):::embedding --> inputEmb("Input Embeddings"):::embedding
    targetSeq("Target Sequence <br> (y₁, ..., yₘ₋₁)"):::embedding --> targetEmb("Target Embeddings"):::embedding
    
    %% Positional Encoding
    inputEmb --> posEncInput("Positional Encoding"):::operation
    targetEmb --> posEncTarget("Positional Encoding"):::operation
    
    %% Encoder and Decoder Stacks
    posEncInput --> encoderStack("Encoder Stack <br> (N layers)"):::component
    posEncTarget --> decoderStack("Decoder Stack <br> (N layers)"):::component
    
    %% Encoder Layers Detail
    encoderStack --> multiHeadAttention("Multi-Head Attention<br>(Self-Attention)"):::attention
    multiHeadAttention --> addNorm1("Add & Norm"):::sublayer
    addNorm1 --> posFFN("Position-wise Feed-Forward Network"):::sublayer
    posFFN --> addNorm2("Add & Norm"):::sublayer
    
    %% Decoder Layers Detail
    decoderStack --> maskedMultiHeadAttention("Masked Multi-Head Attention <br> (Self-Attention)"):::attention
    maskedMultiHeadAttention --> addNorm3("Add & Norm"):::sublayer
    addNorm3 --> encoderDecoderAttention("Encoder-Decoder Attention"):::attention
    encoderDecoderAttention --> addNorm4("Add & Norm"):::sublayer
    addNorm4 --> posFFNDecoder("Position-wise Feed-Forward Network"):::sublayer
    posFFNDecoder --> addNorm5("Add & Norm"):::sublayer
    
    %% Connections between Encoder and Decoder
    addNorm2 -.-> encoderDecoderAttention
    
    %% Final Output Predictions
    addNorm5 --> linearLayer("Linear Layer"):::operation
    linearLayer --> softmaxLayer("Softmax Layer"):::operation
    softmaxLayer --> outputSeq("Output Sequence <br> (y₁, ..., yₘ)"):::embedding
    
    %% Scaled Dot-Product Attention Detail (Separate for clarity)
    subgraph scaledDotProductAttention["Scaled Dot-Product Attention"]
        direction TB
        attentionInput(Q, K, V) --> scaledDotProduct("Scaled Dot-Product <br> (QKᵀ / √dₖ)"):::operation
        scaledDotProduct --> softmaxAttention("Softmax"):::operation
        softmaxAttention --> attentionOutput("Output = softmax(QKᵀ / √dₖ)V"):::attention
    end

    %% Connection to Scaled Dot-Product Attention Detail
    multiHeadAttention -.-> scaledDotProductAttention
    maskedMultiHeadAttention -.-> scaledDotProductAttention
    encoderDecoderAttention -.-> scaledDotProductAttention

    %% Applying classes for styling
    classDef seqEmb fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px;
    class inputSeq,targetSeq,outputSeq seqEmb;

```

---

### Optimizations and Clarifications

1. **Class Definitions:** Utilized class definitions (`styleDef`, `classDef`) to apply consistent visual styles across similar components (e.g., all attention mechanisms share the same visual style). This enhances readability and visual hierarchy.

2. **Component Grouping:** Grouped related components into subgraphs where appropriate (e.g., the detailed view of Scaled Dot-Product Attention) to visually segregate distinct functional areas of the architecture.

3. **Directional Flow:** Employed directional arrows (`-->` for direct flow, `-.->` for conceptual or indirect connections) to delineate data flow versus conceptual relationships, such as the influence of the encoder's output on the encoder-decoder attention mechanism.

4. **Equation Representation:** Included key equations directly within node labels (e.g., "Scaled Dot-Product (QKᵀ / √dₖ)") to provide mathematical context inline with the architecture diagram.

5. **Enhanced Semantic Clarity:** Labels and node names explicitly describe each component's role within the architecture, e.g., "Masked Multi-Head Attention (Self-Attention)" clarifies the masking aspect relevant to decoder layers.

6. **Visual Cohesion:** Maintained a visually cohesive color scheme that aligns with the functional categorization of model components (attention mechanisms, embedding layers, etc.), facilitating quicker recognition and understanding of the architecture's key areas.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---