---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2503.16252"
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


## A Diagrammatic Guide

### 1. Data Distillation and Filtering Pipeline

```mermaid
---
title: "Fin-R1: Data Distillation and Filtering Pipeline"
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
    subgraph Data_Sources["Data Sources"]
        A[Ant_Finance]
        B[FinanceIQ]
        C[FinPEE]
        D[Quant-Trading-Instruct]
        E[ConvFinQA]
        F[FinQA]
        G[TFNS]
        H[Finance-Instruct-500K]
        I[FinCorpus]
    end

    subgraph Stage_1["Stage 1:<br>Data Distillation"]
        J[DeepSeek-R1]
        K[Generated CoT Data]
    end
    
    subgraph Stage_2["Stage 2:<br>Data Filtering"]
        L{"Qwen2.5-72B-Instruct<br>(Answer Check)"}
        M{"Qwen2.5-72B-Instruct<br>(Reasoning Selection)"}
    end

    N["Fin-R1-Data<br>(High-Quality Dataset)"]

    A --> J
    B --> J
    C --> J
    D --> J
    E --> J
    F --> J
    G --> J
    H --> J
    I --> J

    J --> K
    K --> L
    K --> M

    L --> N
    M --> N

    style A fill:#ccf3,stroke:#333,stroke-width:1px
    style B fill:#ccf3,stroke:#333,stroke-width:1px
    style C fill:#ccf3,stroke:#333,stroke-width:1px
    style D fill:#ccf3,stroke:#333,stroke-width:1px
    style E fill:#ccf3,stroke:#333,stroke-width:1px
    style F fill:#ccf3,stroke:#333,stroke-width:1px
    style G fill:#ccf3,stroke:#333,stroke-width:1px
    style H fill:#ccf3,stroke:#333,stroke-width:1px
    style I fill:#ccf3,stroke:#333,stroke-width:1px

    style J fill:#aac3,stroke:#333,stroke-width:1px
    style K fill:#aaf3,stroke:#333,stroke-width:1px

    style L fill:#ffa3,stroke:#333,stroke-width:1px
    style M fill:#ffa3,stroke:#333,stroke-width:1px

    style N fill:#afa3,stroke:#333,stroke-width:1px
    
```

---

### 2. Fin-R1 Training Framework

```mermaid
---
---
title: "Fin-R1 Training Framework"
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
    A["Qwen2.5-7B-Instruct<br>(Base Model)"] --> B("Fin-R1-SFT")
    C["Fin-R1-Data<br>(Training Data)"] --> B
    D(GRPO) --> E["Format Reward"]
    D --> F["Accuracy Reward"]
    B --> D
    D --> G["Fin-R1<br>(Final Model)"]
    E -.-> D
    F -.-> D
    
    style A fill:#ccf3,stroke:#333,stroke-width:1px
    style B fill:#aaf3,stroke:#333,stroke-width:1px
    style C fill:#afa3,stroke:#333,stroke-width:1px
    style D fill:#ffa3,stroke:#333,stroke-width:1px
    style E fill:#fcf3,stroke:#333,stroke-width:1px
    style F fill:#fcf3,stroke:#333,stroke-width:1px
    style G fill:#a3a3,stroke:#333,stroke-width:1px

    classDef reward fill:#ffc3,stroke:#333,stroke-width:1px;
    class E,F reward
```

### 3. Evaluation Process

```mermaid
---
title: "Fin-R1: Evaluation Process"
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
    A[Evaluation Datasets] --> B(Fin-R1)
    C{LLM as Automated Evaluation Judge}
    B --> C
    C --> D[Evaluation Metrics]
    D --> E[Performance Results]
    
    style A fill:#ccf3,stroke:#333,stroke-width:1px
    style B fill:#aaf3,stroke:#333,stroke-width:1px
    style C fill:#afa3,stroke:#333,stroke-width:1px
    style D fill:#ffa3,stroke:#333,stroke-width:1px
    style E fill:#aea3,stroke:#333,stroke-width:1px
    
```

**Key Improvements and Explanations:**

*   **Subgraphs:**  Used to visually group related components (Data Sources, Data Distillation, etc.) in the Data Pipeline.
*   **Labels:** Descriptive labels are essential for understanding the diagrams.  Use parentheses or other notations to add extra info.
*   **Styling:** Different colors help to distinguish between types of nodes (e.g., data sources, models, processes).
*   **Directionality:** Arrows clearly show the flow of data and the sequence of operations.
*   **Reward Loop (Training Framework):**  The dashed arrow in the training diagram (E -.-> D and F -.-> D) emphasize that the reward model provides *feedback* to the GRPO algorithm.
*   **Simplified Factors (For more details check out tutorial)** Each diagram shows the factorization relationship between each stages.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---