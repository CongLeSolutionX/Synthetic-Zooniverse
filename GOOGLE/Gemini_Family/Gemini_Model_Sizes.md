---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2312.11805"
---



# Gemini Model Sizes
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---


## Gemini Model Sizes - A Diagrammatic Guide 



```mermaid
---
title: "Gemini: A Family of Highly Capable Multimodal Models - Google DeepMind"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
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
graph TD
    A[Gemini Model Sizes] --> FA[Ultra]:::detail
    style A fill:#a3ae,stroke:#333,stroke-width:1px
        style FA fill:#f2fa,stroke:#333,stroke-width:1px
        FA --> FAA[Highly-complex tasks, reasoning, multimodal]:::takeaway
        FA --> FAB[Efficiently serveable on TPUs]:::takeaway
    A --> FB[Pro]:::detail
        style FB fill:#f2fa,stroke:#333,stroke-width:1px
        FB --> FBA[Performance-optimized for cost and latency]:::takeaway
        FB --> FBB[Strong reasoning, broad multimodal capabilities]:::takeaway
    A --> FC[Nano]:::detail
        style FC fill:#f2fa,stroke:#333,stroke-width:1px
        FC --> FCA["On-device deployment<br>(1.8B and 3.25B parameters)"]:::takeaway
        FC --> FCB[Summarization, reading comprehension, etc.]:::takeaway
        FC --> FCC[Distilled from larger Gemini models]:::takeaway
        FC --> FCD[4-bit quantized]:::takeaway
    
 classDef takeaway fill:#f2b3,stroke:#333,stroke-width:1px
 classDef detail fill:#f2ff,stroke:#333,stroke-width:1px
 class FA,FB,FC detail
 class FAA,FAB,FBA,FBB,FCA,FCB,FCC,FCD takeaway
 
```

---


### Key improvements and explanations

*   **Focus on Model Sizes:**  The root node is now specifically "Gemini Model Sizes," making the diagram's purpose immediately clear.
*   **Styled Subnodes:** The Ultra, Pro, and Nano variants are represented as subnodes connected to the root.
*   **`:::detail` Styling:** Applied the `detail` class to Ultra, Pro, and Nano.
*   **`:::takeaway` Styling:** Used the `takeaway` class to format their attributes
*   **Concise and Clear Labels:** Maintained concise and descriptive labels for each subnode and attribute.
*   **Visual Organization:** Prioritized a clean and logical visual flow.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---