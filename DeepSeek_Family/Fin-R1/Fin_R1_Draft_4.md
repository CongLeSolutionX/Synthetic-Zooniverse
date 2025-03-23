---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://github.com/SUFE-AIFLM-Lab/Fin-R1/blob/main/README.md"
---



# Fin-R1: A Large Language Model for Financial Reasoning through Reinforcement Learning
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---




## Key Features of Fin-R1

```mermaid
---
title: "Key Features of Fin-R1"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Fin-R1:<br>Financial Reasoning LLM"] --> B{"Key Features"}
    style A fill:#ccf3,stroke:#333,stroke-width:1px

    B --> C(Purpose-Built for Financial Reasoning)
    style C fill:#ddf3,stroke:#333,stroke-width:1px
    C --> CA[Complex Financial Domain]
    C --> CB[Lightweight 7B Params]

    B --> D(Two-Stage Training)
    style D fill:#ddf3,stroke:#333,stroke-width:1px
    D --> DA[SFT on High-Quality Data]
    D --> DB[RL for Format & Accuracy]

    B --> E(Enhanced Reasoning)
    style E fill:#ddf3,stroke:#333,stroke-width:1px
    E --> EA[Solid Foundation]
    E --> EB[Effective Support]

```

## Fin-R1 Overall Workflow

```mermaid
---
title: "Fin-R1 Overall Workflow"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Fin-R1 Workflow] --> B{Data Construction}
    style A fill:#ccf3,stroke:#333,stroke-width:1px

    B --> C[Knowledge Distillation]
    style C fill:#ddf3,stroke:#333,stroke-width:1px
    C --> CA[DeepSeek-R1 Distillation]
    C --> CB[Multiple Datasets]

    B --> D[Quality Scoring]
    style D fill:#ddf3,stroke:#333,stroke-width:1px
    D --> DA[Two-Round Scoring]
    D --> DB[Qwen2.5-72B-Instruct]

    B --> E[Dataset Creation]
    style E fill:#ddf3,stroke:#333,stroke-width:1px
    E --> EA[COT for SFT]
    E --> EB[Reasoning QA for RL]

    A --> F{Fine-Tuning}
    style F fill:#ccf3,stroke:#333,stroke-width:1px
    F --> G["SFT<br>(Stage 1)"]
    style G fill:#ddf3,stroke:#333,stroke-width:1px
    G --> GA[ConvFinQA & FinQA]

    F --> H["RL<br>(Stage 2)"]
    style H fill:#ddf3,stroke:#333,stroke-width:1px
    H --> HA[GRPO Algorithm]
    H --> HB[Dual-Reward]
    H --> HC[Model-Based Verifier]
    
```


## Fin-R1 Data Distribution

```mermaid
---
title: "Fin-R1 Data Distribution"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Fin-R1 Data] --> B{Four Modules};
    style A fill:#ccf3,stroke:#333,stroke-width:1px

    B --> C[Financial Code];
    style C fill:#ddf3,stroke:#333,stroke-width:1px
    C --> CA[Code for Models];

    B --> D[Financial Expertise];
    style D fill:#ddf3,stroke:#333,stroke-width:1px
    D --> DA[Theories & Regulations];

    B --> E[Non-Reasoning Business Knowledge];
    style E fill:#ddf3,stroke:#333,stroke-width:1px
    E --> EA[Factual Information];

    B --> F[Reasoning Business Knowledge];
    style F fill:#ddf3,stroke:#333,stroke-width:1px
    F --> FA[Analytical & Inferential];

```

## Model Evaluation Benchmarks

```mermaid
---
title: "Model Evaluation Benchmarks"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Model Evaluation] --> B{Benchmarks};
    style A fill:#ccf3,stroke:#333,stroke-width:1px

    B --> C[FinQA];
    style C fill:#ddf3,stroke:#333,stroke-width:1px
    C --> CA[Table Reasoning];

    B --> D[ConvFinQA];
    style D fill:#ddf3,stroke:#333,stroke-width:1px
    D --> DA[Multi-Turn Reasoning];

    B --> E[Ant_Finance];
    style E fill:#ddf3,stroke:#333,stroke-width:1px
    E --> EA[Ant Financial Data];

    B --> F[TFNS];
    style F fill:#ddf3,stroke:#333,stroke-width:1px
    F --> FA[Trend Forecasting];

    B --> G[Finance-Instruct-500k];
    style G fill:#ddf3,stroke:#333,stroke-width:1px
    G --> GA[Large-Scale Instruction];

```

Key improvements applied:

*   **Styling:** Consistent styling (fill colors, borders) for visual appeal and readability.
*   **Conciseness:** Shortened labels while retaining essential information.
*   **Structure:** Diagrams maintain the hierarchical structure of the concepts.
*   **Arrow Flow:** Clear directional flow to represent relationships between steps or categories.
*   **Diagram Choice:** Used `graph TD` for directional flow and clear hierarchical relationships.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---