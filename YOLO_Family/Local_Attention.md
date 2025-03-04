---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2502.12524"
---



# Local Attention
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Local Attention - A Diagrammatic Guide 


```mermaid
---
title: Local Attention
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
subgraph Local_Attention["Local Attention"]
    A[Local Attention] --> B[Shift Window]
    A --> C[Criss-Cross Attention]
    A --> D[Axial Attention]
    
    B --> E[Spatial Locality]
    C --> F[Horizontal/Vertical Stripes]
    D --> G[Horizontal/Vertical Windows]

    
    A --> H[Reduced Computational Cost]
    H --> I["O(n<sup>2</sup>hd/2) or Lower"]
    
    A --> J[Receptive Field Considerations]
    J --> K[Potential Reduction or Overhead]

    A --> L[Global Dependency Trade-off]
    L --> M[Preservation of Local Relationships]
end

```

---

### Explanation

* **Local Attention (A):** This is the main concept, a node representing the overarching idea.

* **Specific Local Attention Methods (B, C, D):** These branches represent the different types of local attention mechanisms mentioned (Shift Window, Criss-Cross, Axial).

* **Characteristics (E, F, G):** These branches detail the characteristics of each local attention method.  For instance, Shift Window might focus on spatial locality within a grid.

* **Computational Efficiency (H, I):** This illustrates the key benefit of local attention: reduced computational complexity compared to global attention.  An equation like `O(n<sup>2</sup>hd/2)` (or similar) would be a very helpful addition to node `I`.

* **Receptive Field Considerations (J, K):**  This addresses a potential trade-off.  Local attention might reduce the receptive field, potentially impacting accuracy.

* **Global Dependency Trade-off (L, M):** This emphasizes the trade-off between capturing long-range dependencies and the efficiency gains of locality.  The result of the trade-off is preservation of local relationships (M).


This structure more accurately reflects the concepts associated with local attention, including the trade-offs and characteristics that distinguish it from global attention.  Adding specific details like the complexity equations or how window partitioning works would enhance the diagram.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---