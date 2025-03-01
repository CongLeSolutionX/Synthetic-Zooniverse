---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2405.04434"
---



# DeepSeek MoE Architecture Details
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


```mermaid
---
title: DeepSeekMoE Architecture
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
graph LR
    subgraph DeepSeekMoE_Architecture["DeepSeekMoE Architecture"]
        A[DeepSeekMoE] --> B{Key Ideas}
        B --> C{Fine-grained Expert Segmentation}
        B --> D{Shared Expert Isolation}
        
        B --> E[Improved Expert Specialization]
        B --> F[Reduced Knowledge Redundancy]
        
        subgraph Expert_Segmentation["Expert Segmentation"]
            C --> G[Expert Routing]
            G --> H{Token-to-Expert Affinity}
            H --> I["Softmax Calculation for s<sub>i,t</sub>"]
            H --> J["Top-K Selection (K<sub>r</sub>) of Routed Experts"]
            H --> K[Activation of Experts]
        end
        
        subgraph Shared_Expert_Isolation["Shared Expert Isolation"]
            D --> L[Shared Experts]
            L --> M["Direct Input Combination"]
            L --> N[Reduced Expert Communication]
            L --> O[Improved Model Efficiency]

        end
        
        subgraph Computational_Details["Computational Details"]
            A --> P[FFN Output Calculation]
            P --> Q{Combination of Shared & Routed Experts}
            Q --> R["u<sub>t</sub> + ∑<sub>i=1</sub><sup>N<sub>s</sub></sup> FFN<sup>(s)</sup><sub>i</sub>(u<sub>t</sub>) + ∑<sub>i=1</sub><sup>N<sub>r</sub></sup> g<sub>i,t</sub> FFN<sup>(r)</sup><sub>i</sub>(u<sub>t</sub>)"]
            R --> S[h′<sub>t</sub>]
        end
    end

```


----


### Explanation of DeepSeekMoE Architecture

* **DeepSeekMoE:**  This custom architecture aims for improved expert specialization and reduced redundancy compared to conventional MoE architectures.

* **Fine-grained Expert Segmentation:**  DeepSeekMoE divides experts into smaller, more specialized groups, leading to improved knowledge acquisition and potentially better understanding of specific tasks.  This is represented by the "Expert Routing" and the "Token-to-Expert Affinity" subgraphs.

* **Shared Expert Isolation:** DeepSeekMoE incorporates shared experts to reduce redundancy and potential conflicts between knowledge domains that routed experts may have. The shared experts are likely a set of general-purpose or foundation experts, while the routed experts are more specialized.

* **Token-to-Expert Affinity:** The model learns an affinity between each token and each expert. This affinity, denoted as *s<sub>i,t</sub>*, guides the selection of experts for a given token. The softmax calculation helps in selecting the most relevant expert from the pool of available experts. The *Top-K Selection* step prioritizes the most relevant experts.

* **Computational Details:**  The entire process of combining inputs from shared and routed experts to produce the final FFN output is illustrated.  The primary input is token *u<sub>t</sub>*.


**Important Notes:**

* **N<sub>s</sub>:** Number of shared experts.
* **N<sub>r</sub>:** Number of routed experts.
* **K<sub>r</sub>:** Number of activated routed experts per token.
* **FFN<sup>(s)</sup><sub>i</sub>(u<sub>t</sub>) & FFN<sup>(r)</sup><sub>i</sub>(u<sub>t</sub>):** FFN operations for shared and routed experts, respectively.  The particular implementation may not be fully specified but is likely standard Feed-Forward Network layers.
* **g<sub>i,t</sub>:** The gate value for the i-th expert, determining how much the output of the i-th expert contributes to the overall token output.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---