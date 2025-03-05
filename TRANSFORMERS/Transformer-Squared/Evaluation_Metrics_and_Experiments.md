---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.06252"
---



# Evaluation Metrics and Experiments
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Evaluation Metrics and Experiments - A Diagrammatic Guide 



```mermaid
---
title: "Transformer-Squared: Self-Adaptive LLMs"
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
    subgraph Evaluation_Metrics_and_Experiments["Evaluation Metrics and Experiments"]
        A["Evaluation Metrics"] --> B("Performance Metrics")
        B --> B1["Accuracy<br>(e.g., GSM8K, MBPP-Pro, ARC-Easy)"]
        B --> B2["Precision<br>(e.g., task categorization)"]
        B --> B3["Recall<br>(e.g., task categorization)"]
        B --> B4["F1-Score<br>(e.g., task categorization)"]
        B --> B5["RMSE<br>(Root Mean Squared Error)"]


        A --> C("Ablation Studies")
        C --> C1["Parameter Efficiency<br>(comparing SVF vs. LoRA)"]
        C --> C2["Training Stability<br>(impact of different objective functions)"]
        C --> C3["Inference Speed<br>(comparing different adaptation strategies)"]
        C --> C4["Module Sensitivity<br>(impact of updating different model modules)"]
        C --> C5["Cross-model Compatibility<br>(transferring SVF experts across LLMs)"]
        C --> C6["Few-shot Adaptation Scaling<br>(evaluating performance with different numbers of few-shot examples)"]
        
        A --> D("Experiments on Unseen Tasks")
        D --> D1["MATH<br>(Mathematical Reasoning)"]
        D --> D2["Humaneval<br>(Human Evaluation)"]
        D --> D3["ARC-Challenge<br>(AI2 Reasoning Challenge)"]
        D --> D4["OKVQA<br>(Visual Question Answering)"]


        B -- Details --> B_details[Tables 1, 2, 7, 9 displaying quantitative results]
        C -- Details --> C_details[Tables 4, 8 displaying ablation study results, Figures 4, 5, 9, 10, 11 showcasing visualizations of results]
        D -- Details --> D_details[Table 2 and Figure 6 displaying quantitative results on unseen tasks]
    
        A --> E(Inference Time)
        E --> E1[Table 3 displaying inference time results, with specific focus on 1st and 2nd pass times]
        E --> E2[Analysis of inference time ratios between passes, considering number of prompts]
    
    end
    
```



----

### Explanation

This Mermaid diagram provides a structured overview of the evaluation metrics and experiments used in the paper "Transformer-Squared: Self-Adaptive LLMs".

* **Subgraph "Evaluation Metrics & Experiments":** Encompasses all aspects of the evaluation.

* **Nodes:**  Represent key elements of the evaluation, categorized into "Performance Metrics," "Ablation Studies," "Experiments on Unseen Tasks," and "Inference Time."  These nodes are connected by edges that represent the relationships between them.

* **Edges:**  Define the connections between different evaluation types and the supporting details.

* **Detailed Nodes:** Nodes like `B1` specify the types of tasks and metrics used.  `B_details`, `C_details`, and `D_details` represent tables and figures from the original paper that display the quantitative or visual results of the specific experiments.

* **Metrics:**  The diagram explicitly lists various evaluation metrics used (accuracy, precision, recall, F1-score, RMSE) to give a clear understanding of the evaluation procedures.

* **Emphasis on Tables and Figures:**  The diagram explicitly notes that the supporting data is presented in tables and figures from the original document, making it clear that this is not a re-creation but a visualization of the existing content.

* **Inference Time:**  A dedicated section for analyzing inference time and the relative costs of the adaptation process.

This diagram provides a structured representation of the evaluation methodology, highlighting the specific experiments and tables from the original paper where results are presented.  It makes it easier to quickly locate and understand the methodology behind the evaluation of the different components of the model.  Crucially, it doesn't attempt to recreate the results but rather shows *how* and *where* the results are documented in the original paper.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---