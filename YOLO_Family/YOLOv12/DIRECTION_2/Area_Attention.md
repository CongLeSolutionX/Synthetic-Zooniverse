---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2502.12524"
---



# Area Attention
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Area Attention - A Diagrammatic Guide 



```mermaid
---
title: Area Attention A2
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
    subgraph Area_Attention_A2["Area Attention (A2)"]
        A["Area Attention<br>(A2)"] --> B{Local Attention Mechanism}
        B --> C[Feature Map Partitioning]
        C --> D[Division into l Areas]
        D --> E[Vertical or Horizontal Partitioning]
        E --> F["Receptive Field Reduction<br>(1/l)"]
        F --> G["Computational Cost Reduction<br>(O(n^2hd/2))"]
        G --> H[Maintains Large Receptive Field]
        H --> I[Simple Reshape Operation]
        I --> J[Speed Improvement]
        
        subgraph Example
            J -- "Example: (H, W)" <br>(H/l, W/l) --> K[Reshape]
            K --> L[Computation]
        end
    end
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---