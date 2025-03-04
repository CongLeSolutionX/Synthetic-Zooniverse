---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# DeepSeek V3 Post-Training
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## DeepSeek V3 Post-Training - A Diagrammatic Guide



```mermaid
---
title: "DeepSeek-V3 Technical Report"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
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
    subgraph DeepSeek_V3_Post_Training["DeepSeek V3 Post Training"]
        A[DeepSeek-V3 Post-Training] --> B(Supervised Fine-Tuning)
        A --> C(Reinforcement Learning)
        A --> D(Knowledge Distillation)
    end
    
    subgraph Supervised_Fine_Tuning["Supervised Fine Tuning"]
        B(Supervised Fine-Tuning) --> B1(Instruction Tuning Data)
        B1 --> B1a(Reasoning Data)
        B1 --> B1b(Non-Reasoning Data)
        B1a --> B1a1(DeepSeek-R1 Model)
        B1a --> B1a2(System Prompts)
        B1a --> B1a3("Reflection/Verification Mechanisms")
        B1b --> B1b1("DeepSeek-V2.5 Model")
        B1b --> B1b2(Human Annotation)
        B --> B2(SFT Settings)
        B2 --> B2a(Epochs)
        B2 --> B2b(Learning Rate Scheduling)
        B2 --> B2c(Sample Masking)

    end

    subgraph Reinforcement_Learning["Reinforcement Learning"]
        C(Reinforcement Learning) --> C1(Reward Model)
        C1 --> C1a(Rule-Based)
        C1 --> C1b(Model-Based)
        C1a --> C1a1(Deterministic Tasks)
        C1a --> C1a2(Verification with Rules)
        C1b --> C1b1(Free-Form Ground Truth)
        C1b --> C1b2(Reward Model Training)
        C1b --> C1b3(Chain-of-Thought Feedback)
        C1b --> C1b4(Mitigation of Reward Hacking)
        C --> C2(Group Relative Policy Optimization)
        C2 --> C2a(Group Sampling)
        C2 --> C2b(Advantage Calculation)
        C2 --> C2c(Reference Model)
        C2 --> C2d(Hyperparameters: epsilon, beta)
        
    end

    subgraph Knowledge_Distillation["Knowledge Distillation"]
        D(Knowledge Distillation) --> D1(DeepSeek-R1 Distillation)
        D1 --> D1a(Reasoning Capabilities)
        D1 --> D1b("Long Chain-of-Thought (CoT) Models")
        D1 --> D1c(Performance Improvement)
        D1 --> D1d(Trade-off with Response Length)

    end

```

---


### Explanation

This Mermaid diagram provides a more detailed breakdown of the DeepSeek-V3 post-training stages, expanding on the previous, higher-level graph.

* **Subgraphs:** The diagram uses subgraphs to group related concepts, making it more organized and readable.
* **Nodes and Relationships:** The nodes represent key components (like "Instruction Tuning Data," "Reward Model") and the arrows show their relationships (e.g., how reasoning data is generated or how RL influences the model).
* **Detailing Sub-components:**  Crucially, this graph breaks down the data generation process for SFT, the mechanics of the reward models, and the specific details of the knowledge distillation process.
* **Clearer Representation:** It clarifies the specific data used, the optimization methods, and the evaluation metrics used in each phase.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---