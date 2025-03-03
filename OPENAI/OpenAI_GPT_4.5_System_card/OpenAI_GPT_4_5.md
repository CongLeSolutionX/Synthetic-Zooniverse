---
created: 2025-03-02 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf"
---



# OpenAI GPT-4.5
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## OpenAI GPT-4.5 - A Diagrammatic Guide 



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
    subgraph OpenAI_GPT_4_5_System_Overview[""OpenAI GPT-4.5 System Overview""]
        A[OpenAI GPT-4.5] --> B{"Model Overview"}
        B --> C["Large Language Model<br>(LLM)"]
        B --> D[Knowledge Base]
        D --> D1[Expanded Knowledge]
        B --> E[Alignment with User Intent]
        B --> F[Improved Emotional Intelligence]
        B --> G[Reduced Hallucinations]
        B --> H[Training Data]
        H --> H1[Public Data]
        H --> H2[Proprietary Data]
        H --> H3[Custom Data]
        B --> I[Safety Evaluation]

    end


    subgraph Safety_Evaluation_Details["Safety Evaluation Details"]
        I --> J[Disallowed Content]
        J --> J1[Harmful Content]
        J1 --> J1a[Hate Speech]
        J1 --> J1b[Illicit Advice]
        J1 --> J1c[Sexual Content]
        J --> J2[Jailbreak Robustness]
        J2 --> J2a[Adversarial Prompts]
        J2 --> J2b[Human-Sourced Jailbreaks]
        J2 --> J2c[StrongReject]
        J --> J3[Hallucination Evaluation]
        J3 --> J3a[PersonQA]
        J3a --> J3b[Accuracy]
        J3a --> J3c[Hallucination Rate]
        J --> J4[Bias Evaluation]
        J4 --> J4a[BBQ Evaluation]
        J4a --> J4b[Ambiguous Questions]
        J4a --> J4c[Unambiguous Questions]
        J --> J5[Instruction Hierarchy]
        J5 --> J5a[System vs. User Conflicts]
        J5a --> J5b[Accuracy]
        J5 --> J5c[Tutor Jailbreaks]
        J5c --> J5d[Accuracy]
        J5 --> J5e[Phrase/Password Protection]
        J5e --> J5f[Accuracy]
        J --> J6[Red Teaming Evaluations]
        J6 --> J6a[Adversarial Jailbreaks]
        J6a --> J6b[GPT-4o Performance]
        J6a --> J6c[o1 Performance]
        J6a --> J6d[o3-mini Performance]
        J6a --> J6e[GPT-4.5 Performance]
        J6 --> J6f[Risky Advice]
        J6f --> J6g[GPT-4o Performance]
        J6f --> J6h[o1 Performance]
        J6f --> J6i[Deep Research Performance]
        J6f --> J6j[GPT-4.5 Performance]
        J --> J7[Apollo Research Evaluations]
        J7 --> J7a[Scheming Reasoning]
        J7 --> J7b[In-Context Alignment Faking]
        J7 --> J7c[Sandbagging]
        J7 --> J7d[Self-Exfiltration]
        J --> J8[METR Evaluation]
        J8 --> J8a[Model Autonomy Tasks]
        J8a --> J8b[Time Horizon Score]
        J8 --> J8c[Internal Evaluation Results]

    end
    
    subgraph Multilingual_Performance["Multilingual Performance"]
        I --> K[Multilingual Evaluation]
        K --> K1[MMLU Dataset]
        K1 --> K1a["Accuracy<br>(14 Languages)"]
    end

    subgraph Model_Capabilities["Model Capabilities"]
        B --> L[Model Capabilities]
        L --> L1[Unsupervised Learning]
        L --> L2[Chain-of-Thought Reasoning]
        L --> L3[Improved Steerability]
        L --> L4[Aesthetic Intuition]
        L --> L5[Creative Writing/Design]

    end


    subgraph Preparedness_Framework["Preparedness Framework"]
        I --> M[Preparedness Framework]
        M --> M1[CBRN Risk]
        M --> M2[Persuasion Risk]
        M --> M3[Cyber Risk]
        M --> M4[Model Autonomy Risk]
        M --> M5[Overall Risk Rating]

    end

```


----


### Explanation and Improvements

This revised Mermaid diagram is significantly more detailed and organized based on the provided text.

* **Subgraphs:**  The subgraphs now provide clear groupings for different evaluation types and model characteristics.
* **Relationships:**  Connectors are added to show the relationships between the components of the system and the evaluations.
* **Evaluation Metrics:**  Nodes like "PersonQA" now explicitly link to the metrics measured within those evaluations, like "Accuracy" and "Hallucination Rate."
* **Red Teaming and Apollo Research:** The structure has been significantly refined to clearly differentiate between various red teaming evaluations and the independent evaluation from Apollo.
* **Preparedness Framework:** A dedicated subgraph now encapsulates the evaluation results through the lens of the OpenAI Preparedness Framework.
* **Clearer Visual Representation:**  The use of distinct node colors (or shapes) could further enhance clarity.  Consider different colors for the various evaluation categories (e.g., red for harmful content, blue for robustness).

This detailed structure provides a more accurate and comprehensive visualization of the OpenAI GPT-4.5 system card's content.  Remember that numerical results from the tables should be incorporated into the relevant evaluation nodes in subgraph "Safety Evaluation Details" to make the visualization actionable.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---