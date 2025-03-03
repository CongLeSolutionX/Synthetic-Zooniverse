---
created: 2025-03-02 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf"
---



# OpenAI GPT-4.5 System Card Paper Overview
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## OpenAI GPT-4.5 System Card - A Diagrammatic Guide 






```mermaid
---
title: "OpenAI GPT-4.5 System Card"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
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
    subgraph GPT_4_5_System_Overview["GPT-4.5 System Overview"]
        A[OpenAI GPT-4.5] --> B{Model Overview}
        B --> C["Large Language Model<br>(LLM)"]
        B --> D[Advanced Knowledge Base]
        B --> E[Improved Alignment]
        B --> F[Enhanced Emotional Intelligence]
        B --> G[Reduced Hallucinations]
        B --> H[Diverse Training Data]
        
        H --> H1[Public Data]
        H --> H2[Proprietary Data]
        H --> H3[Custom Datasets]
        B --> I[Safety Evaluations]
        
    end
    
    subgraph Safety_Evaluation_Details["Safety Evaluation Details"]
        I --> J[Disallowed Content]
        J --> J1[Harmful Content]
        J1 --> J1a[Hate Speech]
        J1 --> J1b[Illicit Advice]
        J1 --> J1c[Sexual Content]
        J --> J2[Jailbreak Robustness]
        J2 --> J2a[Adversarial Prompts]
        J --> J3[Hallucinations]
        J3 --> J3a[PersonQA]
        J --> J4[Fairness & Bias]
        J4 --> J4a[BBQ Evaluation]
        J --> J5[Instruction Hierarchy]
        J5 --> J5a[System vs. User Conflicts]
        J5 --> J5b[Tutor Jailbreaks]
        J5 --> J5c[Phrase/Password Protection]
        J --> J6[Red Teaming]
        J6 --> J6a[Adversarial Jailbreaks]
        J6 --> J6b[Apollo Research]
        J6 --> J6c[METR]

        J6 --> J6d[Time Horizon Score]

        J --> J7[Preparedness Framework]
        J7 --> J7a[CBRN]
        J7 --> J7b[Persuasion]
        J7 --> J7c[Cybersecurity]
        J7 --> J7d[Model Autonomy]

    end

    subgraph Multilingual_Performance["Multilingual Performance"]
        I --> K[Multilingual Performance]
        K --> K1[MMLU Dataset]
        K1 --> K1a[Translations]

    end

    subgraph Model_Capabilities["Model Capabilities"]
        B --> L[Model Capabilities]
        L --> L1[Unsupervised Learning]
        L --> L2[Chain-of-Thought Reasoning]

        L --> L3[Improved Steerability]
        L --> L4[Aesthetic Intuition]
        L --> L5[Creative Writing/Design Support]

    end

```

---

### Explanation of the Diagram

This Mermaid diagram uses subgraphs to organize the different aspects of the GPT-4.5 system card.

* **GPT-4.5 System Overview:** This subgraph provides a high-level view of the model, its key strengths, and its training data sources.
* **Safety Evaluation Details:** This subgraph delves deeper into the various safety evaluation methods used, categorizing them for better understanding.  Note that this subgraph is quite detailed and contains sub-nodes for each specific evaluation.  Tables within the original document would need to be included as supporting data to this diagram.
* **Multilingual Performance:** This subgraph focuses on the multilingual performance evaluation aspect.
* **Model Capabilities:**  This subgraph highlights the model's advanced capabilities, including unsupervised learning and chain-of-thought reasoning, as well as improved steerability and aesthetic intuition.


---


### Important Considerations and Improvements

* **Tables:**  The diagram is meant to be a conceptual outline.  To make it fully functional, incorporate the results from the tables in the original document into the diagram.  For example, include the scores (and 95% confidence intervals) from the various evaluations in J (Safety Evaluation Details).
* **Connectors:** Add more specific connectors between nodes to show the relationships between different parts of the system.
* **Visual Cues:**  Use different shapes or colors for different types of nodes (e.g., model evaluations, data types) to enhance readability and clarity.
* **Complexity:** The diagram is still quite complex. Break down subgraphs further if necessary to avoid overwhelming the viewer with details.  This would depend on the level of detail required by the user.


This revised structure provides a better visual representation of the key concepts, allowing for a more comprehensive understanding of the OpenAI GPT-4.5 system card. Remember to add the numerical data from the tables into the diagram to make it fully functional.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---