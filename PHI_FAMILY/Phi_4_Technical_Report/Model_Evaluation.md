---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2412.08905"
---


# Model Evaluation
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## Model Evaluation - A Diagrammatic Guide



```mermaid
---
title: "Phi-4 Technical Report"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false, 'curve': 'linear' },
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
    subgraph Model_Evaluation["Model Evaluation"]
        A["Model Evaluation"] --> B{"Benchmarking"}
        B --> C("Academic Benchmarks")
        C --> D["MMLU"]
        C --> E["GPQA"]
        C --> F["MATH"]
        C --> G["HumanEval"]
        C --> H["MGSM"]
        C --> I["SimpleQA"]
        C --> J["DROP"]
        C --> K["MMLU-Pro"]
        C --> L["HumanEval+"]
        C --> M["ArenaHard"]
        C --> N["IFEval"]

        B --> O("Internal Benchmarks")
        O --> P["PhiBench"]
        B --> Q("Other Benchmarks")
        Q --> R["AMC-10/AMC-12"]
        Q --> S["HELMET"]
        
        B --> T{"Evaluation Metrics"}
        T --> AA["RMSE"]
        T --> AB["F1-score"]
        T --> AC["SubEM"]
        T --> AD["nDCG@10"]

        B --> AE{"Comparison to Other Models"}
        AE --> AF["Qwen-2.5-14B-Instruct"]
        AE --> AG["Llama-3.3-70B-Instruct"]
        AE --> AH["GPT-4o-mini"]
        AE --> AI["GPT-4o"]
        
        B --> AK{"Performance Trends"}
        AK --> AL["Table 1<br>(Overall Performance)"]
        AK --> AM["Table 2<br>(Pretraining Comparison)"]
        AK --> AN["Table 9<br>(Post-Training Comparison)"]
        AK --> AO["Figure 1<br>(AMC-10/12 Results)"]
        AK --> AP["Figure 6<br>(Hallucination Mitigation)"]

        B --> AQ{"Limitations and Weaknesses"}
        AQ --> AR["Data Contamination"]
        AQ --> AS["Limited Skill Scope"]
        AQ --> AT["Bias in Generation-Based Benchmarks"]
        AQ --> AU["Limitations of Multiple-Choice Tasks"]
        AQ --> AV["Hallucinations<br>(Factual Knowledge)"]
        AQ --> AW["Instruction Following<br>(Specific Formatting)"]
    
    end

```


---

### Explanation

This Mermaid diagram provides a more detailed and structured view of the model evaluation aspects of the phi-4 technical report. It incorporates the evaluation process, metrics, benchmarks, and crucial observations about performance, weaknesses, and limitations.

* **Subgraphs:** Organize related concepts into subgraphs for better clarity (e.g., `Academic Benchmarks`, `Internal Benchmarks`).
* **Nodes:** Represent specific benchmarks, evaluation metrics, and model comparisons using more detailed labels (e.g., `MMLU`, `RMSE`, `Qwen-2.5-14B-Instruct`).
* **Edges:** Illustrate the relationships between components of the evaluation process (e.g., `Academic Benchmarks` are evaluated using `Evaluation Metrics`).
* **Performance Trends:** Explicitly link to tables and figures that show performance trends over time or across different conditions (e.g., `Table 1`, `Figure 1`, `Table 9`). This helps connect the visual representations to the quantitative data presented in the report.
* **Limitations and Weaknesses:**  A dedicated subgraph highlights the limitations and weaknesses identified in the evaluation, drawing connections to the report's discussions on these issues.

This more comprehensive diagram allows for a better understanding of the model evaluation strategy and the key findings from the report.  Remember that this diagram is adaptable; you can add or modify nodes and edges based on specific details or new information discovered in the report.  Note that some concepts, like "Overfitting Analysis", are not directly part of "Model Evaluation" but are important supporting elements. Consider adding a link between these supporting elements and the evaluation aspects to complete the visual representation.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---