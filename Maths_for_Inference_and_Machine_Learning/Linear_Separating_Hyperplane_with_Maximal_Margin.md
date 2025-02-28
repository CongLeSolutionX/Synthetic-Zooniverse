---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Linear Separating Hyperplane with Maximal Margin
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Linear Separating Hyperplane with Maximal Margin - A Diagram Structure


```mermaid
---
title: Linear Separating Hyperplane with Maximal Margin
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
    A[Linear Separating Hyperplane] --> B(Maximal Margin)
    B --> C{Concept}
    C --> CA[Finding a hyperplane that maximizes the distance between the closest data points of different classes]
    C --> CB[This distance is called the margin]
    
    subgraph Data_Representation["Data Representation"]
    C -- Data: x<sub>i</sub>, y<sub>i</sub> --> D
        D -- x<sub>i</sub> --> E[x<sub>1</sub>]
        D -- x<sub>i</sub> --> F[x<sub>2</sub>]
        D -- y<sub>i</sub> --> G[y<sub>1</sub>]
        D -- y<sub>i</sub> --> H[y<sub>2</sub>]
        D -- ... --> I[x<sub>N</sub>]
        D -- ... --> J[y<sub>N</sub>]
    end
    
    subgraph Hyperplane_Definition["Hyperplane Definition"]
    C -- Hyperplane: w<sup>T</sup>x + b = 0 --> K
        K -- w --> L[w]
        K -- b --> M[b]
    end
    
    subgraph Margin_Calculation["Margin Calculation"]
    C -- Margin: Distance between w<sup>T</sup>x + b = ±1 --> N
        N -- w<sup>T</sup>x<sub>i</sub> + b ≥ 1  --> O[Positive Class]
        N -- w<sup>T</sup>x<sub>i</sub> + b ≤ -1 --> P[Negative Class]
        N -- Distance --> Q["Maximizing 2/||w||<sub>2</sub>"]
    end
    
    subgraph Optimization_Problem["Optimization Problem"]
    C -- Optimization Problem --> R
        R -- Minimize ||w||<sub>2</sub> --> S[Minimize w<sup>T</sup>w / 2]
        R -- Subject to --> T
        T -- y<sub>i</sub>(w<sup>T</sup>x<sub>i</sub> + b) ≥ 1 (for all i) --> U[Constraints]
    end

```

---

### Explanation

This Mermaid diagram visualizes the "Linear Separating Hyperplane with Maximal Margin" concept.

* **Nodes:**  Represent key elements like data points, the hyperplane, the margin, and the optimization problem.
* **Subgraphs:**  Organize related concepts, like data representation and the hyperplane definition.
* **Edges:**  Illustrate the relationships between concepts and the steps in finding the optimal hyperplane.

The diagram shows the core idea:  finding the hyperplane (`w<sup>T</sup>x + b = 0`) that maximizes the margin between the closest data points from different classes.  The margin is calculated as the distance between the planes `w<sup>T</sup>x + b = ±1`. The optimization problem is formally presented as minimizing the squared norm of `w` (a proxy for the margin) subject to the constraint that all data points are correctly classified, ensuring a maximum margin. This diagram directly reflects the mathematical and conceptual structure described in the original text.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---