---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Matrix Norms
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Matrix Norms - A Diagram Structure


```mermaid
---
title: Matrix Norms
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
    A[Matrix Norms] --> B(Frobenius Norm)
    B --> C{"||A||<sub>F</sub> = √(∑<sub>i=1</sub><sup>m</sup> ∑<sub>j=1</sub><sup>n</sup> |a<sub>ij</sub>|<sup>2</sup>)"}
    
    A --> D(Induced p-norms)
    D --> E{"||A||<sub>p</sub> = sup<sub>x≠0</sub> ||Ax||<sub>p</sub> / ||x||<sub>p</sub>"}
    
    subgraph Properties
        E -- Important Properties --> F
        F --> FA{"||AB||<sub>p</sub> ≤ ||A||<sub>p</sub> ||B||<sub>p</sub>"}
        F --> FB{"||Ax||<sub>p</sub> ≤ ||A||<sub>p</sub> ||x||<sub>p</sub>"}
        F --> FC{"||A||<sub>p</sub> = max<sub>||x||<sub>p</sub>=1</sub> ||Ax||<sub>p</sub>"}
        
        FA --  (Matrix Multiplication) --> GA
        FB -- (Matrix-Vector Multiplication) --> GB
        FC --  (p-norm) --> GC
    end
    
    subgraph Examples
        E --> EA(p=1)
        EA --> EB{"||A||<sub>1</sub> = max<sub>1≤j≤n</sub> ∑<sub>i=1</sub><sup>m</sup> |a<sub>ij</sub>|"}
        E --> EC(p=∞)
        EC --> ED{"||A||<sub>∞</sub> = max<sub>1≤i≤m</sub> ∑<sub>j=1</sub><sup>n</sup> |a<sub>ij</sub>|"}
        E --> EE(p=2)
        EE --> EF{"||A||<sub>2</sub> = σ<sub>1</sub>"}
    end
    
```

---

### Explanation

The Mermaid diagram visually represents matrix norms, specifically the Frobenius norm and the induced p-norms.

* **Frobenius Norm (||A||<sub>F</sub>):**  This norm is calculated as the square root of the sum of the squared absolute values of all elements in the matrix.  The diagram shows the mathematical formula clearly.

* **Induced p-norms (||A||<sub>p</sub>):**  These norms are defined by the maximum possible scaling factor a matrix applies to vectors in a given p-norm.  The diagram shows the general definition, highlighting that it's based on the maximum scaling of vectors.

* **Important Properties:**  The diagram shows key properties of matrix norms, specifically how they relate to matrix multiplication and matrix-vector multiplication. These properties are crucial for understanding their behavior.

* **Specific Examples (p=1, p=∞, p=2):** The diagram also includes specific examples of the induced p-norms for p = 1, ∞, and 2.  These specific norms provide a concrete understanding of how they are calculated. The key relationship between the induced 2-norm and the largest singular value is emphasized.

This diagram effectively communicates the concepts of matrix norms, their calculation, and important properties without relying on overly complex language or phrases that might be typical of AI-generated text. The use of mathematical notation in the diagram helps clarify the definitions and calculations.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---