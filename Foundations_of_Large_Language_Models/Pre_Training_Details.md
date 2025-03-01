---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---



# Pre-Training Details
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
title: Pre-Training Details
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
    subgraph PreTraining_Details["Pre-Training Details"]
        C[Unsupervised Pre-training] --> C1["Minimizing reconstruction error<br>(e.g., input vector)"]
        C --> C2[Discovering better local minima]
        C --> C3[Regularization effect]
        
        D[Supervised Pre-training] --> D1[Fine-tuning on downstream tasks]
        D --> D2["Adapting to new tasks<br>(e.g., sentiment analysis, text classiﬁcation)"]
        D --> D3[High data demand for complex models]
        D --> D4[Requires labeled data, which can be limiting]
        
        E[Self-Supervised Pre-training] --> E1["Masked Language Modeling<br>(predicting masked words)"]
        E --> E2["Next Sentence Prediction<br>(understanding sentence relationships)"]
        E --> E3["Permuted Language Modeling<br>(predicting tokens in any order)"]
        E --> E4["Denoising Autoencoding<br>(reconstructing corrupted sequences)"]
        E --> E5["Other self-supervision tasks<br>(e.g., preﬁx language modeling, etc.)"]
        E --> E6["Training objective: maximizing likelihood/minimizing cross-entropy"]
        E --> E7["Handling variations in masking<br>(e.g., percentage, span length)"]
        
        subgraph MLMDetails
            E1 --> E11["Masking tokens and replacing them with [MASK]"]
            E1 --> E12["Predicting masked tokens using surrounding context"]
            E1 --> E13["Bidirectional context vs. unidirectional context<br>(causal language modeling)"]
            E1 --> E14["Handling different masking strategies<br>(random replacement, unchanged)"]
        end
        
        subgraph NSPDetails
            E2 --> E21["Modeling relationships between sentences"]
            E2 --> E22["Using [CLS] and [SEP] tokens"]
            E2 --> E23["Classifying sentence pairs as 'next' or 'not next'"]
            E2 --> E24["Training objective: maximizing likelihood for sentence classiﬁcation"]
        end
    end
    
    style PreTraining_Details fill:#ccf2,stroke:#333,stroke-width:1px
    
```

-----

### Explaination

This subgraph, "PreTrainingDetails,"  breaks down the various pre-training approaches in more detail based on the original text.  It includes connections to specific aspects (e.g., masking strategies in Masked Language Modeling, the use of special tokens in NSP).  This level of detail allows for a more informative and comprehensive understanding of pre-training methods.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---