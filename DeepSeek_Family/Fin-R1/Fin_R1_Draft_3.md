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


## A Diagrammatic Guide

### Fin-R1: Financial Reasoning Large Language Model
```mermaid
---
title: "Fin-R1: Financial Reasoning Large Language Model"
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
    A["Fin-R1:<br>Financial Reasoning Large Language Model"] --> B{"Key Features"}

    B --> C["Purpose-Built for Financial Reasoning"]:::detail
    C --> CA["Designed specifically for complex reasoning in the financial domain"]
    C --> CB["Lightweight 7B parameter architecture for reduced deployment costs"]

    B --> D["Two-Stage Training Methodology"]:::detail
    D --> DA["Supervised Fine-Tuning (SFT) on high-quality financial reasoning data"]
    D --> DB["Reinforcement Learning (RL) for optimizing format and accuracy"]

    B --> E["Enhanced Financial Reasoning Capabilities"]:::detail
    E --> EA["Solid theoretical foundation, business rules, decision logic, and technical implementation skills for financial applications"]
    E --> EB["Effective support for core financial business scenarios in banking, securities, insurance, and trust"]

    A --> F{"Applications"}
    F --> G["Financial Code Generation"]:::detail
    G --> GA["Automated generation of computer code for financial models and analyses"]
    
    F --> H["Financial Calculations"]:::detail
    H --> HA["Quantitative analysis and calculation for solving financial problems"]
    
    F --> I["English Financial Calculations"]:::detail
    I --> IA["Cross-language financial model construction and calculation using English"]
    
    F --> J["Financial Security and Compliance"]:::detail
    J --> JA["Prevention of financial crime and adherence to regulatory requirements"]
    
    F --> K["Intelligent Risk Control"]:::detail
    K --> KA["AI-driven identification and management of financial risks"]
    
    F --> L[ESG Analysis]:::detail
    L --> LA["Assessment of corporate environmental, social, and governance performance"]
    
    classDef detail fill:#fef3,stroke:#333,stroke-width:1px
    
```

**Explanation:**
*   **Fin-R1: Financial Reasoning Large Language Model:** Represents the core concept.
*   **Key Features:** High-level functionalities and benefits.
*   **Applications:** Real-world scenarios where Fin-R1 can be applied.

---

### Overall Workflow of Fin-R1

```mermaid
---
title: "Overall Workflow of Fin-R1"
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
    A["Overall Workflow of Fin-R1"] --> B{"Data Construction"}
    B --> C["Knowledge Distillation"]:::detail
    C --> CA["Utilize DeepSeek-R1 to distill knowledge from multiple datasets covering industry-specific language, professional knowledge, business insights, and quantitative investment"]
    
    B --> D["Two-Round Quality Scoring"]:::detail
    D --> DA["Score the distilled data based on answer accuracy and reasoning logic"]
    D --> DB["Use Qwen2.5-72B-Instruct to assess the reasoning chains for logical consistency and compliance with financial terminology"]
    
    B --> E["Dataset Construction"]:::detail;
    E --> EA["High-quality COT(Chain-of-Thought) dataset for SFT (Supervised Fine-Tuning)"]
    E --> EB["Reasoning QA dataset for Reinforcement Learning (RL)"]

    A --> F{"Fine-Tuning Training"}
    F --> G["Stage 1:<br>Supervised Fine-Tuning (SFT)"]:::detail
    G --> GA["Use ConvFinQA and FinQA datasets to enhance the model's understanding and processing of complex financial reasoning problems"]
    
    F --> H["Stage 2:<br>Reinforcement Learning (RL)"]:::detail
    H --> HA["Employ GRPO (Group Relative Policy Optimization) algorithm"]
    H --> HB["Optimize model output format and accuracy using a dual-reward mechanism"]
    H --> HC["Introduce a Model-Based Verifier using Qwen2.5-Max for accurate reward signal generation"]

    A --> I{"Model Evaluation Results"}
    I --> J["Performance Benchmarks"]:::detail
    J --> JA["Evaluate the model on various benchmarks covering multiple financial business scenarios"]
    J --> JB["Compare the performance of Fin-R1 (SFT+RL) with DeepSeek-R1 and other models"]
    
    classDef detail fill:#fef3,stroke:#333,stroke-width:1px
    
```


**Explanation:**
*   **Overall Workflow of Fin-R1:** The entire process of data preparation, training, and evaluation.
*   **Data Construction:** Steps involved in creating a high-quality financial dataset.
*   **Fine-Tuning Training:** Detailed breakdown of the two-stage training process.
*   **Model Evaluation Results:** The results of testing and comparing the model against other baselines.

---

### Fin-R1 Data Distribution

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
    A["Fin-R1 Data Distribution"] --> B{"Four Key Modules"}
    B --> C["Financial Code"]:::detail
    C --> CA["Computer code used for financial models, algorithms, and analysis tasks"]
    
    B --> D["Financial Expertise"]:::detail
    D --> DA["In-depth knowledge related to financial theories, regulations, and markets"]
    
    B --> E["Financial Non-Reasoning Business Knowledge"]:::detail
    E --> EA["Factual and procedural information for financial operations"]
    
    B --> F["Financial Reasoning Business Knowledge"]:::detail
    F --> FA["Knowledge requiring analytical and inferential abilities"]
    
    classDef detail fill:#fef3,stroke:#333,stroke-width:1px
```

**Explanation:**
*   **Fin-R1 Data Distribution:**  How the training data is organized into specific categories.
*   **Four Key Modules:** Categories that the training data falls into.

---

### Model Evaluation
```mermaid
---
title: "Model Evaluation"
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
    A["Model Evaluation"] --> B{"Benchmarks"}
    B --> C["FinQA"]:::detail
    C --> CA["Focuses on financial table reasoning tasks"]
    
    B --> D["ConvFinQA"]:::detail
    D --> DA["Tests multi-turn reasoning interaction in the financial domain"]
    
    B --> E[Ant_Finance]:::detail
    E --> EA["Includes datasets from Ant Financial covering various financial applications"]
    
    B --> F[TFNS]:::detail
    F --> FA["Covers tasks related to trend forecasting and news sentiment analysis"]
    
    B --> G["Finance-Instruct-500k"]:::detail
    G --> GA["A large-scale instruction dataset for financial tasks"]
    
    classDef detail fill:#fef3,stroke:#333,stroke-width:1px
```

**Explanation:**
*   **Model Evaluation:**  The procedure and specific datasets used to evaluate the model's performance.
*   **Benchmarks:**  Different test datasets utilized in the model's evaluation.

---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---