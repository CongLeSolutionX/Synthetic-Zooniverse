---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---



# One-shot In-context Learning
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
title: One-shot In-context Learning
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
    subgraph One_Shot_InContext_Learning["One-shot In-context Learning"]
        A[In-Context Learning] --> B(One-Shot Learning)
        B --> C{Key Idea}
        C --> C1[LLM learns from a single demonstration]
        C --> C2[Demonstration provides a pattern]
        C --> C3[Pattern applied to new inputs]
        
        subgraph One_Shot_Example["One-Shot Example"]
            C --> D[Example: Text Classification]
            D --> D1[Instruction: Classify sentiment as positive, negative, or neutral]
            D --> D2[Demonstration 1]
            D2 -- "Example 1: I love this product!" --> D3("Positive")
            D --> D4[Demonstration 2]
            D4 -- "Example 2: The service was terrible!" --> D5("Negative")
            D --> D6[New Input]
            D6 -- "Example 3: This book is okay." --> D7["Output: (e.g., Neutral)"]
        end
        
        B --> E(Prompt Structure)
        E --> E1[Instruction + Demonstration]
        E --> E2[Input for Prediction]
        E --> E3[Output]
    end

    style A fill:#ccf3,stroke:#333,stroke-width:1px;
    style B fill:#ccf3,stroke:#333,stroke-width:1px;
    style C fill:#ccf3,stroke:#333,stroke-width:1px;
    style D fill:#ccf3,stroke:#333,stroke-width:1px;
    style E fill:#ccf3,stroke:#333,stroke-width:1px;
    style One_Shot_InContext_Learning fill:#c2c2,stroke:#333,stroke-width:1px;
    
```

---


### Explanation

This Mermaid graph visually represents one-shot in-context learning.  It's a simplified version of the broader in-context learning concept, focusing specifically on the case where a single demonstration is used to guide the model.

* **Subgraph `One-Shot In-Context Learning`:** Encloses the core elements.
* **Node `A` (In-Context Learning):** Represents the overall concept.
* **Node `B` (One-Shot Learning):** The specific focus of the diagram.
* **Node `C` (Key Idea):**  Highlights the fundamental idea—learning from a single example.
* **Subgraph `OneShotExample` (Example):**  Illustrates the concept with a concrete text-classification scenario.
    *   **Node `D` (Example):** Shows the task.
    *   **Nodes `D1` to `D7`:** Detail the instruction, demonstrations, and the resulting output for a new input.
* **Node `E` (Prompt Structure):** Shows the structure of the prompt containing the instruction and the example.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---