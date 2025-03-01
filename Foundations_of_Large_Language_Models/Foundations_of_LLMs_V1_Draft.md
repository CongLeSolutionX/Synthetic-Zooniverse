---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---



# Foundations of Large Language Models
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## A Hierarchical Structure of the Document

```mermaid
---
title: Foundations of LLMs
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
    subgraph Foundations_of_LLMs
        A["Large Language Models (LLMs)"] --> B{Pre-training}
        B --> C(Unsupervised)
        B --> D(Supervised)
        B --> E(Self-Supervised)
        
        subgraph PreTrainingDetails
            C --> C1(Minimizing reconstruction error)
            C --> C2(Discovering better local minima)
            C --> C3(Regularization)
            
            D --> D1(Fine-tuning on downstream tasks)
            D --> D2(Adapting to new tasks)
            D --> D3(Increased data demand)
            
            E --> E1(Masked Language Modeling)
            E --> E2(Next Sentence Prediction)
            E --> E3(Permuted Language Modeling)
            E --> E4(Denoising Autoencoding)
        end
        
        B --> F(Prompting)
        F --> G(In-context Learning)
        F --> H(Advanced Methods)
        F --> I(Learning to Prompt)
        
        subgraph PromptingDetails
            G --> G1(Zero-shot)
            G --> G2(One-shot)
            G --> G3(Few-shot)
            
            H --> H1(Chain-of-Thought)
            H --> H2(Problem Decomposition)
            H --> H3(Self-Refinement)
            H --> H4(Ensembling)
            H --> H5(Retrieval Augmented Generation)
            H --> H6(Tool Use)
        end
        
        B --> J(Alignment)
        J --> K(Instruction Alignment)
        J --> L(Human Preference Alignment)
        J --> M(Inference-time Alignment)
        
        subgraph AlignmentDetails
            K --> K1(Supervised Fine-tuning)
            K --> K2(Instruction Data Acquisition)
            K --> K3(Instruction Generalization)
            K --> K4(Weak Models to Improve Strong Models)
            
            L --> L1(Reward Modeling)
            L --> L2(RLHF)
            L --> L3(Direct Preference Optimization)
            L --> L4(Automatic Preference Data Generation)
            
            M --> M1(Best-of-N Sampling)
            M --> M2(Rejection Sampling)
        end

        B --> N(Scaling Laws)
        N --> N1(Model Size, Training Data, Computation)
        N --> N2(Emergent Abilities)

        B --> O(Long Sequence Modeling)
        O --> P(Efficient Attention Mechanisms)
        O --> Q(Memory-Based Models)
        O --> R(Positional Encodings)

    end
    
    
    style A fill:#f9f5,stroke:#333,stroke-width:1px;
    style B fill:#ccf5,stroke:#333,stroke-width:1px;
    style C fill:#ccf5,stroke:#333,stroke-width:1px;
    style D fill:#ccf5,stroke:#333,stroke-width:1px;
    style E fill:#ccf5,stroke:#333,stroke-width:1px;
    style F fill:#ccf5,stroke:#333,stroke-width:1px;
    style G fill:#ccf5,stroke:#333,stroke-width:1px;
    style H fill:#ccf5,stroke:#333,stroke-width:1px;
    style I fill:#ccf5,stroke:#333,stroke-width:1px;
    style J fill:#ccf5,stroke:#333,stroke-width:1px;
    style K fill:#ccf5,stroke:#333,stroke-width:1px;
    style L fill:#ccf5,stroke:#333,stroke-width:1px;
    style M fill:#ccf5,stroke:#333,stroke-width:1px;
    style N fill:#ccf5,stroke:#333,stroke-width:1px;
    style O fill:#ccf5,stroke:#333,stroke-width:1px;
    style P fill:#ccf5,stroke:#333,stroke-width:1px;
    style Q fill:#ccf5,stroke:#333,stroke-width:1px;
    style R fill:#ccf5,stroke:#333,stroke-width:1px;
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---