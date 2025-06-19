---
created: 2025-03-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://arxiv.org/pdf/1810.04805"
---



# BERT Model Architecture
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



```mermaid
---
title: BERT Model Architecture
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
graph LR
    subgraph BERT_Model_Architecture["BERT Model Architecture"]
        A[BERT] --> B{Transformer Encoder}
        B --> C["Input Embedding (E)"]
        C --> D[Token Embeddings]
        C --> E[Segment Embeddings]
        C --> F[Position Embeddings]
        
        subgraph "Layers"
            D -- (Token i) --> G[Layer 1]
            E -- (Segment A/B) --> G
            F -- (Position i) --> G
            G --> H[Layer 2]
            H --> I[...]
            I --> J[Layer L]
            J --> K[Output Layer]
        end

        
        K --> L["Masked Language Model<br>(MLM)"]
        K --> M["Next Sentence Prediction<br>(NSP)"]
    end
    
    subgraph Masked_Language_Model["Masked Language Model<br>(MLM)"]
        L --> N["Masked Tokens (e.g., [MASK])"]
        N -- Prediction --> O(Vocabulary IDs)
        N --> P[Cross-Entropy Loss]
    end
    
    subgraph Next_Sentence_Prediction["Next Sentence Prediction<br>(NSP)"]
        M --> Q[Sentence A]
        M --> R[Sentence B]
        M --> S[IsNext/NotNext Label]
        S --> T[Binary Classification Loss]
    end
    
    subgraph "Output"
        K --> U["Classification Token<br>([CLS])"]
        U -- Aggregate Representation --> V[Classification Layer]
        
        K --> W["Token Representations<br>(T<sub>i</sub>)"]
        W -- Token-Level Tasks --> X[Output Layer]
    end
    
```

---


### Explanation and Improvements


This Mermaid diagram focuses specifically on the BERT model's architecture. It's structured to show the flow of information from input to output, highlighting the key components involved in pre-training and fine-tuning.  It's more precise and avoids the overly general structure of the previous attempt.

* **Input Embedding (E):**  The diagram explicitly shows the input embedding `E` as the combination of token, segment, and position embeddings.
* **Layers (L):** The repeated layers (`Layer 1`, `Layer 2`, ..., `Layer L`) are now represented to indicate the multi-layered transformer architecture.
* **Output Layer (K):** This layer is specifically labeled and connected to the MLM and NSP tasks.
* **Masked Language Model (MLM) and Next Sentence Prediction (NSP):**  The diagram explicitly shows how these tasks are incorporated as branches of the output layer, connecting the outputs to appropriate loss functions.
* **Output Representations:** The output of the model for both token-level and classification tasks is clearly illustrated. The `[CLS]` token's hidden state is used for classification.

---


### How to further improve

* **Connection to Special Tokens:** Add a visual link between the input embedding `E` and the special tokens ([CLS], [SEP]) to clarify their role in the input.
* **Attention Mechanism:**  While this diagram doesn't visualize the attention mechanism itself, consider adding a note or annotation to indicate its presence in each layer.
* **Fine-tuning Context:** Include a smaller subgraph showing the addition of a classification layer during fine-tuning, clarifying how downstream tasks are handled.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---