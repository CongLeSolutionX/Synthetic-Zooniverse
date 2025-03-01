---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---



# In-context Learning
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
title: In-context Learning
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
    subgraph In_Context_Learning["In-Context Learning"]
        A["In-Context Learning (ICL)"] --> B(Zero-Shot Learning)
        B --> C{No explicit training}
        B --> D(Direct Application)
        
        A --> E(One-Shot Learning)
        E --> F{Single demonstration}
        E --> G(Learning from example)
        
        A --> H(Few-Shot Learning)
        H --> I{Multiple demonstrations}
        H --> J(Learning patterns)
        
        subgraph ICL_Examples["In-Context Learning Examples"]
            B --> K(Example: Grammar correction)
            E --> L(Example: Translation, demonstrating a few examples)
            H --> M(Example: Mathematical reasoning)
        end
        
        A --> N(Emergent Ability)
        N --> O(Pre-training knowledge activation)
        N --> P(Adaptability without explicit training)
        
        A --> Q(Relationship to Prompting)
        Q --> R(Effective prompts guide learning)
        Q --> S(Prompts contain examples)
        
        A --> T(Limitations)
        T --> U(Data quality & model strength)
        T --> V(Difficulties in complex tasks)
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
    style N fill:#ccf3,stroke:#333,stroke-width:1px;
    style O fill:#ccf3,stroke:#333,stroke-width:1px;
    style P fill:#ccf3,stroke:#333,stroke-width:1px;
    style Q fill:#ccf3,stroke:#333,stroke-width:1px;
    style R fill:#ccf3,stroke:#333,stroke-width:1px;
    style S fill:#ccf3,stroke:#333,stroke-width:1px;
    style T fill:#ccf3,stroke:#333,stroke-width:1px;
    style U fill:#ccf3,stroke:#333,stroke-width:1px;
    style V fill:#ccf3,stroke:#333,stroke-width:1px;
    
```


---


### Explanation



This Mermaid graph visualizes "In-Context Learning" (ICL) as a key concept within the broader framework of Large Language Model (LLM) prompting and adaptation.  It breaks down the different aspects of ICL—zero-shot, one-shot, and few-shot—and shows how these relate to prompt design and model limitations. The inclusion of example scenarios (e.g., grammar correction, translation) provides concrete application contexts.  The subgraph "ICL_Examples" is crucial for grounding the abstract concepts. The "Limitations" section highlights potential issues that can affect ICL performance.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---