---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2501.12948"
---



# DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## An Overview of the Paper



```mermaid
---
title: DeepSeek-R1 Overview
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
graph TD
    subgraph DeepSeek_R1_Overview["DeepSeek-R1 Overview"]
        A[DeepSeek-R1] --> B{Enhanced Reasoning}
        B --> C[Reinforcement Learning]
        B --> D[Supervised Fine-Tuning]
        C --> E[DeepSeek-R1-Zero]
        C --> F[DeepSeek-R1]
        D --> F
        E --> G["Rule-based Rewards<br>(Accuracy, Format)"]
        E --> H["Simple Training Template"]
        E --> I["Aha! Moment<br>(Self-Evolution)"]
        F --> J["Cold-Start Data<br>(Long CoT examples)"]
        F --> K["Reasoning-Oriented RL"]
        F --> L["Rejection Sampling & SFT<br>(diverse domains)"]
        F --> M["Multi-stage Training"]
        F --> N["Language Consistency Reward"]
        F --> O["Combined Reasoning/Language Reward"]
    end

    subgraph Distillation["Distillation"]
        F --> P{Distillation}
        P --> Q["Smaller Dense Models<br>(Qwen, Llama)"]
        P --> R[SFT Distillation]
    end
    
    subgraph Evaluation["Evaluation"]
        A --> S{Evaluation}
        S --> T["Reasoning Benchmarks<br>(AIME, MATH-500, etc.)"]
        S --> U["Open-Ended Generation Tasks<br>(AlpacaEval, ArenaHard)"]
        S --> V["Knowledge Benchmarks<br>(MMLU, MMLU-Pro, etc.)"]
        S --> W["Code and Engineering Benchmarks<br>(LiveCodeBench, Codeforces, SWE-Bench)"]
        S --> X["Baselines<br>(DeepSeek-V3, OpenAI models)"]
        S --> Y["Evaluation Setup<br>(Length Limits, Sampling Temperature, Pass@k)"]

    end

    subgraph Discussion["Discussion"]
        A --> Z{Discussion}
        Z --> AA["Distillation vs. RL"]
        Z --> AB["Unsuccessful Attempts<br>(PRM, MCTS)"]
        Z --> AC["Future Directions<br>(General Capability, Language Mixing, etc.)"]
    end
    
```


---


### Explanation of the Diagram

This Mermaid graph uses subgraphs to organize the different aspects of the DeepSeek-R1 model and its surrounding concepts.

*   **DeepSeek-R1 Overview:** This subgraph encompasses the core components of DeepSeek-R1.  The nodes represent concepts, and the arrows indicate the flow or relationship between them. The use of subgraphs visually organizes the concepts, making it easier to understand the overall structure.

*   **Distillation:** This subgraph focuses on the distillation process.  It shows how knowledge is transferred from the larger DeepSeek-R1 model to smaller models.

*   **Evaluation:** This subgraph illustrates the evaluation process, outlining the types of benchmarks and baselines used for comparison.

*   **Discussion:** This subgraph summarizes the key points of discussion in the paper, such as the comparison between distillation and reinforcement learning, the analysis of unsuccessful attempts, and future research directions.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---