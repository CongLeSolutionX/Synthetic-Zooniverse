---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# DeepSeek-V3 Technical Report
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## DeepSeek-V3 Technical Report - Paper Overview


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
    subgraph DeepSeek_V3_Overview["DeepSeek V3 Overview"]
        A[DeepSeek-V3] --> B(Architecture)
        A --> C(Training)
        A --> D(Evaluation)
        A --> E(Post-Training)
        A --> F(Deployment)
    end
    
    subgraph Architecture["Architecture"]
        B(Architecture) --> B1(MLA)
        B --> B2(DeepSeekMoE)
        B --> B3(MTP)
    end

    subgraph Training["Training"]
        C(Training) --> C1(FP8 Training)
        C --> C2(DualPipe)
        C --> C3(Communication)
        C --> C4(Memory Optimization)
    end

    subgraph Evaluation["Evaluation"]
        D(Evaluation) --> D1(Benchmarks)
        D --> D2(Results)
        D1 --> D1a(MMLU, DROP, HumanEval, etc.)
        D2 --> D2a(Tables, Figures comparing DeepSeek-V3 to other models)
    end

    subgraph PostTraining["PostTraining"]
        E(Post-Training) --> E1(SFT)
        E --> E2(RL)
        E1 --> E1a(Instruction Tuning Data)
        E2 --> E2a(Reward Models)
        E2 --> E2b(GRPO)
        E --> E3(Knowledge Distillation)
    end
    
    subgraph Deployment["Deployment"]
        F(Deployment) --> F1(Prefilling)
        F --> F2(Decoding)
        F1 --> F1a(Redundant Experts)
        F1 --> F1b(Micro-batch Overlap)
        F2 --> F2a(Single Expert per GPU)
        F2 --> F2b(IB/NVLink Communication)
        F2 --> F2c(Micro-batch Overlap)
    end

    B1 --> B1a(Low-rank compression)
    B1 --> B1b(RoPE application)
    B1 --> B1c(Concatenation)
    B2 --> B2a(Shared Experts)
    B2 --> B2b(Routed Experts)
    B2 --> B2c(Gating Mechanism)
    B2 --> B2d(Auxiliary-loss-free load balancing)
    B3 --> B3a(Sequential prediction)
    B3 --> B3b(Causal chain)
    B3 --> B3c(MTP modules)
    C1 --> C1a(Fine-grained quantization)
    C1 --> C1b(High-precision accumulation)
    C2 --> C2a(Forward/Backward overlap)
    C2 --> C2b(Reduced pipeline bubbles)
    C3 --> C3a(Customized all-to-all communication kernels)
    C3 --> C3b(Warp specialization)
    C4 --> C4a(Recomputation of RMSNorm, MLA up-projections)
    C4 --> C4b(EMA in CPU)
    C4 --> C4c(Shared embedding/output head)
    
    E1a --> E1b(Reasoning Data Generation)
    E1a --> E1c(Non-Reasoning Data Generation)
    E2a --> E2b(Rule-based reward model)
    E2a --> E2c(Model-based reward model)
    E3 --> E3a(Knowledge Distillation from DeepSeek-R1)

```


----

### Explanation

This Mermaid graph provides a high-level overview of the DeepSeek-V3 model.  It's structured using subgraphs to organize the key components (Architecture, Training, Evaluation, etc.).  Each box represents a key concept and sub-boxes further break down the sub-components.  This is a starting point; you'd need to add more detail using further sub-boxes and relationships as needed.

* **Use of subgraphs:** This structure provides a more organized and manageable way to visualize complex systems like DeepSeek-V3.  Each concept is compartmentalized, helping with readability and understanding of specific aspects.
* **Arrows:**  Connect related concepts, like showing how the architecture leads to efficient training, or how evaluation results are derived from the model.
* **Detailed Components:**  The graph breaks down the components of the model and the techniques used for efficient training and inference, allowing for more specific visualization within the sub-components.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---