---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2312.11805"
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMDNleGtrM256OGd4MjczdDgzcjB6Y2ltMHV3bXd3MmQ2OHh5a3plcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/PfR64JndE2DhS/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# Pre-Training Datasets for Gemini Model Family
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


## Pre-Training Datasets for Gemini Model Family - A Diagrammatic Guide 


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
graph LR
    A[Pre-Training Datasets for Gemini Model Family] --> B{Data Sources}
    style A fill:#a3ae,stroke:#333,stroke-width:1px
    B --> C[Web Documents]:::detail
    style C fill:#a2fa,stroke:#333,stroke-width:1px
    C --> CA[Broad coverage of topics and languages]:::takeaway
    B --> D[Books]:::detail
    style D fill:#a2fa,stroke:#333,stroke-width:1px
    D --> DA[Extensive knowledge base]:::takeaway
    B --> E[Code]:::detail
    style E fill:#a2fa,stroke:#333,stroke-width:1px
    E --> EA[Diverse programming languages and styles]:::takeaway
    B --> F[Image Data]:::detail
    style F fill:#a2fa,stroke:#333,stroke-width:1px
    F --> FA[Natural Images, Charts, Screenshots, PDFs]:::takeaway
    F --> FB[Variety of visual content]:::takeaway
    B --> G[Audio Data]:::detail
    style G fill:#a2fa,stroke:#333,stroke-width:1px
    G --> GA["16kHz audio from Universal Speech Model (USM)"]:::takeaway
    G --> GB[Captures nuances lost in text translation]:::takeaway
    B --> H[Video Data]:::detail
    style H fill:#a2fa,stroke:#333,stroke-width:1px
    H --> HA[Sequence of frames]:::takeaway
    H --> HB[Handles variable input resolution]:::takeaway
    
    A --> I{Data Processing}
    style I fill:#a3ae,stroke:#333,stroke-width:1px
    I --> J[SentencePiece Tokenizer]:::detail
    style J fill:#a2da,stroke:#333,stroke-width:1px
    J --> JA[Trained on large sample of entire training corpus]:::takeaway
    J --> JB[Improves vocabulary and model performance]:::takeaway
    J --> JC[Efficiently tokenizes non-Latin scripts]:::takeaway
    I --> K[Dataset Scaling]:::detail
    style K fill:#a2da,stroke:#333,stroke-width:1px
    K --> KA[Token count for largest models based on compute-optimality]:::takeaway
    K --> KB[Smaller models trained for more tokens to improve inference]:::takeaway
    I --> L[Quality and Safety Filters]:::detail
    style L fill:#a2da,stroke:#333,stroke-width:1px
    L --> LA[Heuristic rules and model-based classifiers]:::takeaway
    L --> LB[Removes harmful content based on Google's policies]:::takeaway
    L --> LC[Searches for and removes evaluation data from training corpus]:::takeaway
    I --> M[Data Mixtures and Weights]:::detail
    style M fill:#a2da,stroke:#333,stroke-width:1px
    M --> MA[Final mixtures and weights determined through ablations]:::takeaway
    M --> MB[Staged training: Increases weight of domain-relevant data towards end]:::takeaway

 classDef takeaway fill:#f2b2,stroke:#333,stroke-width:1px
 classDef detail fill:#f2f3,stroke:#333,stroke-width:1px
 class C,D,E,F,G,H,I,J,K,L,M detail
 class CA,CB,DA,DB,EA,EB,FA,FB,GA,GB,HA,HB,JA,JB,JC,KA,KB,LA,LB,LC,MA,MB takeaway
 
```

---


### Key points

*   **Data Sources:** The model is trained on a diverse set of data, visualized as branches stemming from the root node.
*   **Data Processing:** Steps involved in preparing the data for training, such as tokenization and filtering, are detailed to provide a complete picture.
*   **Emphasis on Filtering:** Data curation and quality control are highlighted with a dedicated branch and specific steps.
*   **Takeaways:** Key properties and benefits of each data component are marked as "takeaway," drawing attention to the most important information.




---


```mermaid
---
title: "❓...CongLeSolutionX....❓"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'flowchart': { 'htmlLabels': false },
    'fontFamily': 'Bradley Hand',
    'themeVariables': {
      'primaryColor': '#fc82',
      'primaryTextColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#5229',
      'secondaryTextColor': '#6C3483',
      'lineColor': '#F8B229',
      'fontSize': '20px'
    }
  }
}%%
flowchart LR
    My_Meme@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-and-question-marks-open-book-old-characters-background.png", label: "..🙉..👀..📖..", pos: "b", w: 200, h: 150, constraint: "off" }
   
    Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote@{ shape: braces, label: "..👀..<br/>'Unfortunately,<br/>no one can be told<br/> what the Matrix is.<br/>You have to see it<br/>for yourself'<br/>...📚..<br/>-<ins>Morpheus,<br/>a character from the movie The Matrix 1999</ins>"}

   Closing_quote ~~~ My_Meme

    My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
