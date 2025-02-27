---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Matrix Transposition
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagram Structure



```mermaid
---
title: Matrix Transposition
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
    A[Matrix Transposition] --> B{Definition}
    B --> C[Operation]
    C --> D[Rows become columns, columns become rows]
    
    subgraph Example
        D --> DA[Original Matrix]
        DA --> DAB["A = (a<sub>ij</sub>)"]
        
        DAB --> DAB1[
            a<sub>11</sub>  a<sub>12</sub>  a<sub>13</sub>
            a<sub>21</sub>  a<sub>22</sub>  a<sub>23</sub>
            a<sub>31</sub>  a<sub>32</sub>  a<sub>33</sub>
        ]
    
        DA --> DABB["Resulting Transpose Matrix"]
        
        DABB --> DABB1[
            a<sub>11</sub>  a<sub>21</sub>  a<sub>31</sub>
            a<sub>12</sub>  a<sub>22</sub>  a<sub>32</sub>
            a<sub>13</sub>  a<sub>23</sub>  a<sub>33</sub>
        ]
    end

    C --> E["Notation"]
    E --> EA["A<sup>T</sup> (or A')"]
    
    subgraph Properties
        E --> EB["Important for calculation"]
        EB --> EBB["(AB)<sup>T</sup> = B<sup>T</sup>A<sup>T</sup>"]
        EB --> EBB1["A<sup>T</sup>A = symmetric"]
        EB --> EBB2["Key for algorithms like QR, SVD"]
    end
    
```

----

### Explanation

The diagram uses a combination of shapes and annotations to clearly define matrix transposition.

*   **A[Matrix Transposition]:** The main topic.
*   **B{Definition}:** Highlighting the core definition.
*   **C[Operation]:** Emphasizing the action performed.
*   **D[Rows become columns, columns become rows]:**  A concise description of the transposition process.
*   **Example subgraph:** This visually demonstrates the transformation.  It shows the original matrix and the resultant transposed matrix with clear notation for the elements (e.g., a<sub>11</sub>, a<sub>22</sub>). This is a crucial part for understanding the concept.
*   **E[Notation]:** Shows how the transpose is denoted mathematically.
*   **Properties subgraph:** This illustrates the importance of transposition for calculations. The properties listed demonstrate how transposition affects matrix operations and why it's useful in algorithms.

This diagram effectively summarizes the concept of matrix transposition using a visual representation that incorporates the core definition, a clear example, and important mathematical notation. It also highlights why the concept is essential in various linear algebra applications. Remember that these diagrams are adaptable to other matrix sizes (3x3 or n x m) as needed.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---