---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---



# Ensembling
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
title: Ensembling LLMs
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
    subgraph Ensembling_LLMs["Ensembling LLMs"]
        A[Ensembling LLMs] --> B(Model Ensembling)
        B --> C(Multiple LLMs)
        B --> D(Same Prompt, Different Predictions)
        B --> E(Combining Predictions)
        
        subgraph Model_Ensembling_Details["Model Ensembling Details"]
            C --> C1(Different Architectures or Parameters)
            C --> C2(Diverse Model Outputs)
            C --> C3(Reducing Bias and Errors)
            C --> C4(Combining Predictions with Methods like Voting, Averaging, Stacking)
        end
        
        A --> F(Prompt Ensembling)
        F --> G(Multiple Prompts for Same Task)
        F --> H(Diverse Prompt Outputs)
        F --> I(Combining Predictions via Methods)
        
        subgraph Prompt_Ensembling_Details["Prompt Ensembling Details"]
            G --> G1(Diverse Prompts Increase Output Diversity)
            G --> G2(Different Prompts Generate Different Results)
            G --> G3(Combining Predictions by Voting or Overlap)
            G --> G4(Model Averaging for Prediction)
        end

        A --> J(Output Ensembling)
        J --> K(Multiple Predictions from Same LLM)
        J --> L(Sampling Outputs from Hypothesis Space)
        J --> M(Combining Predictions via Methods)
        
        subgraph Output_Ensembling_Details["Output Ensembling Details"]
            K --> K1(Beam Search for Diverse Candidates)
            K --> K2(Sampling for Diverse Candidates)
            K --> K3(Model Averaging for Predictions)
            K --> K4(Self-Consistency for Best Prediction)
            K --> K5(Ranking by Count of Predictions)
        end
        
        A --> N(Bayesian Perspective)
        N --> O(Prompt as Latent Variable)
        N --> P(Marginalizing over Prompts)
        N --> Q(Computational Issues with Integration)
        N --> R(Uniform or Non-informative Priors)
    end

    style A fill:#ccf3,stroke:#333,stroke-width:1px;
    style B fill:#ccf3,stroke:#333,stroke-width:1px;
    style C fill:#ccf3,stroke:#333,stroke-width:1px;
    style D fill:#ccf3,stroke:#333,stroke-width:1px;
    style E fill:#ccf3,stroke:#333,stroke-width:1px;
    style F fill:#ccf3,stroke:#333,stroke-width:1px;
    style G fill:#ccf3,stroke:#333,stroke-width:1px;
    style H fill:#ccf3,stroke:#333,stroke-width:1px;
    style I fill:#ccf3,stroke:#333,stroke-width:1px;
    style J fill:#ccf3,stroke:#333,stroke-width:1px;
    style K fill:#ccf3,stroke:#333,stroke-width:1px;
    style L fill:#ccf3,stroke:#333,stroke-width:1px;
    style M fill:#ccf3,stroke:#333,stroke-width:1px;
    style N fill:#ccf3,stroke:#333,stroke-width:1px;
    style O fill:#ccf3,stroke:#333,stroke-width:1px;
    style P fill:#ccf3,stroke:#333,stroke-width:1px;
    style Q fill:#ccf3,stroke:#333,stroke-width:1px;
    style R fill:#ccf3,stroke:#333,stroke-width:1px;
    
```

This Mermaid graph provides a more detailed and structured view of ensembling techniques for LLMs. It explicitly shows the different aspects of ensembling, how they relate to each other, and the methods for combining predictions.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---