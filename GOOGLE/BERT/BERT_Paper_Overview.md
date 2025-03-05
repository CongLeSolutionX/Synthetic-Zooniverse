---
created: 2025-03-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://arxiv.org/pdf/1810.04805"
---



# BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding
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
title: BERT - Pre-training of Deep Bidirectional Transformers for Language Understanding
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
    subgraph "BERT Model Overview"
        A[BERT] --> B{Core Idea};
        B -- Bidirectional Transformer Encoder --> C[Pre-training Tasks];
        C --> D(Masked Language Model);
        C --> E(Next Sentence Prediction);
        C --> F[Fine-tuning];
        F -- Unified Architecture --> G[Downstream Tasks];
        G --> H[Question Answering];
        G --> I[Language Inference];
        G --> J[Other NLP Tasks];
        
        subgraph "Pre-training Details"
            D -- Random Masking --> K[Masked Tokens];
            D -- Prediction --> L(Vocabulary IDs);
            E -- Sentence Pairs --> M(IsNext/NotNext);
        end
        
        subgraph "Architecture"
            C --> N["Layers (L)"]
            C --> O["Hidden Size (H)"]
            C --> P["Attention Heads (A)"]
            
            N --> Q[BERTBASE];
            O --> Q;
            P --> Q;
            N --> R[BERTLARGE];
            O --> R;
            P --> R;
        end
        
        subgraph "Input Representation"
            F --> S[WordPiece Embeddings];
            S --> T["Special Tokens ([CLS], [SEP])"]
            S --> U[Sentence A/B Embeddings];
            S --> V[Position Embeddings];
            
            T --> W["Classification Token ([CLS])"]
        end
    end
    
    subgraph "Related Work"
        A --> X{Comparison};
        X -- Unidirectional Models --> Y[OpenAI GPT];
        X -- Unidirectional Models --> Z[ELMo];
        X -- Feature-based vs. Fine-tuning --> AA[Feature-based Approach];
        X -- Feature-based vs. Fine-tuning --> BB[Fine-tuning Approach];
        
        AA --> CC[ELMo];
        BB --> DD[OpenAI GPT];
    end
    
    subgraph "Experimental Results"
        A --> EE[GLUE Benchmark];
        EE --> FF(Results Table);
        A --> GG[SQuAD v1.1/v2.0];
        GG --> HH(Results Table);
        A --> II[SWAG];
        II --> JJ(Results Table);
    end
    
    subgraph "Ablation Studies"
        A --> KK[Impact of Pre-training Tasks];
        KK --> LL(Table 5 - Pre-training Task Impact);
        A --> MM[Model Size];
        MM --> NN(Table 6 - Model Size Impact);
        A --> OO[Masking Strategies];
        OO --> PP(Table 8 - Masking Strategy Impact);
    end
    
    subgraph "Further Considerations"
        A --> QQ[Computational Cost];
        A --> RR[Pre-training Data];
        A --> SS[Fine-tuning Procedure];
    end
    
    subgraph "Additional Figures"
        A --> TT[Figure 1 - Overall Procedures];
        A --> UU[Figure 2 - Input Representation];
        A --> VV[Figure 3 - Model Architecture Comparison];
        A --> WW[Figure 5 - Training Steps Impact];
        A --> XX[Figure 4 - Fine-tuning on Different Tasks];
    end
    
```

----


### Explanation

This Mermaid graph uses nested subgraphs to organize the key concepts and relationships within the BERT paper.  It incorporates tables to represent experimental results and ablation study data, effectively showcasing the connections between concepts and their supporting evidence.  This structure allows for a more comprehensive and easily navigable visualization of the paper's content.  Each subgraph is labeled for clarity, and nodes and edges are semantically connected, mimicking the hierarchical structure of the paper itself.

---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---