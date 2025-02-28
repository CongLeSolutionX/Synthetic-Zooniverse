---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Reconstruction Perspective
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Reconstruction Perspective - A Diagram Structure


```mermaid
---
title: Reconstruction Perspective
config:
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
    subgraph Reconstruction_Perspective["Reconstruction Perspective"]
        A[PCA] --> B{Reconstruction}
        B --> C(Optimal Linear Reconstruction)
        C --> D(Minimizing Least Squares Error)
        
        D --> E(Reconstructing Data)
        E --> F(Finding Optimal Vectors)

        F --> G(Defining Objective Function)
        G --> H["||X - ˜X||<sub>F</sub><sup>2</sup>"]
        style H fill:#f2f5,stroke:#333,stroke-width:1px
        
        G --> I(Reconstruction Operator)
        I --> J["˜x<sub>i</sub> = W(W<sup>T</sup>W)<sup>-1</sup>W<sup>T</sup>x<sub>i</sub>"]
        style J fill:#f2f5,stroke:#333,stroke-width:1px
        
        I --> K(Data Centering)
        K --> L["X = [x<sub>1</sub>, ..., x<sub>n</sub>]"]
        style L fill:#f2f5,stroke:#333,stroke-width:1px
        
        K --> M(Orthogonal Projections)
        M --> N(Maximizing Reconstruction)

        N --> O["tr(W<sup>T</sup>XX<sup>T</sup>W)"]
        style O fill:#f2f5,stroke:#333,stroke-width:1px
        
        N --> P(Principal Directions)
        P --> Q["w<sub>1</sub>, ..., w<sub>d</sub>"]
        style Q fill:#f2f5,stroke:#333,stroke-width:1px
    end

```


---

### Explanation

This Mermaid diagram visually depicts the "Reconstruction Perspective" of Principal Component Analysis (PCA).

*   **Subgraph:**  The `Reconstruction_Perspective` subgraph encapsulates the core concepts related to this perspective.
*   **Nodes:**  The diagram uses nodes to represent key concepts like "Optimal Linear Reconstruction," "Minimizing Least Squares Error," and "Finding Optimal Vectors."
*   **Edges:**  Edges connect related concepts, showing the flow of ideas.  For example, the "Minimizing Least Squares Error" concept leads directly to the "Reconstructing Data" and "Finding Optimal Vectors" stages.
*   **Key Equations:**  Crucially, the diagram incorporates the key equation "||X - ˜X||<sub>F</sub><sup>2</sup>" (Frobenius norm of the difference between the original and reconstructed data), representing the core objective of the reconstruction.  Similarly, other key mathematical expressions (e.g., the reconstruction operator equation) are highlighted for clarity.
*   **Contextual Information:**  The diagram includes nodes like "Data Centering," "Orthogonal Projections," and "Maximizing Reconstruction" to provide a comprehensive view of the reconstruction process within PCA, reflecting the mathematical underpinnings discussed in the lecture notes.

This diagram, using the provided structure, effectively illustrates the "Reconstruction Perspective" by showing the steps involved in reconstructing data using principal components and the mathematical principles that drive this process. Remember that the exact detail within each node could be expanded further to match the specific aspects of the original document.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---