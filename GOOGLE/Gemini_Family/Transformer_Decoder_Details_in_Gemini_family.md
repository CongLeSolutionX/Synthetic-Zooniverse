---
created: 2025-03-04 05:31:26
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
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExejAxYTMzZnJzczlxaDZjZXFoaTFldG5zbXJubHR6cnB5a3V4MmRyZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/gjwtQp1N5B0EU7TfVs/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# Transformer Decoder Details in Gemini family
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


## Transformer Decoder Details in Gemini family - A Diagrammatic Guide 


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
    A[Transformer Decoders in Gemini] --> B{Core Architecture}
    style A fill:#a3ae,stroke:#333,stroke-width:1px
    B --> C[Decoder-Only Transformers]:::detail
    style C fill:#a2da,stroke:#333,stroke-width:1px
    C --> CA[Builds on standard Transformer decoder architecture]:::takeaway

    B --> D{Enhancements}
    style D fill:#a3ae,stroke:#333,stroke-width:1px
    D --> DA[Improvements in Architecture & Model Optimization]:::detail
    style DA fill:#a2fa,stroke:#333,stroke-width:1px
    DA --> DAA[Enable stable training at scale]:::takeaway
    DA --> DAB[Optimized inference on Google's TPUs]:::takeaway

    D --> E{Context Length & Attention}
    style E fill:#a3ae,stroke:#333,stroke-width:1px
    E --> EA[32k Context Length Support]:::detail
        style EA fill:#f2fa,stroke:#333,stroke-width:1px
        EA --> EAA[Allows processing longer sequences of text, image, audio, and video]:::takeaway
    E --> EB[Efficient Attention Mechanisms]:::detail
        style EB fill:#f2fa,stroke:#333,stroke-width:1px
        EB --> EBA["Multi-Query Attention (MQA)"]:::takeaway
        EB --> EBB[Potential for other efficient attention variants]:::takeaway

    A --> F{Multimodal Input Handling}
    style F fill:#a3ae,stroke:#333,stroke-width:1px
    F --> FA[Interleaved Input]:::detail
        style FA fill:#a2da,stroke:#333,stroke-width:1px
        FA --> FAA["Text interleaved with audio and visual data (images, charts, screenshots, PDFs, videos)"]:::takeaway
    F --> FB[Image Output]:::detail
        style FB fill:#a2da,stroke:#333,stroke-width:1px
        FB --> FBA[Can natively output images using discrete image tokens]:::takeaway
        FB --> FBB[Based on techniques from VQ-VAE, etc.]:::takeaway

    A --> G{Video & Audio Processing}
    style G fill:#a3ae,stroke:#333,stroke-width:1px
    G --> GA[Video Encoding]:::detail
        style GA fill:#a2da,stroke:#333,stroke-width:1px
        GA --> GAA[Video encoded as a sequence of frames within the context window]:::takeaway
        GA --> GAB[Handles variable input resolution to focus compute]:::takeaway
    G --> GB[Audio Encoding]:::detail
        style GB fill:#a2da,stroke:#333,stroke-width:1px
        GB --> GBA[Directly ingests audio signals at 16kHz from USM features]:::takeaway
        GB --> GBB[Captures nuances often lost in text-based audio representations]:::takeaway

    A --> H{Inspiration & Foundations}
        style H fill:#a3ae,stroke:#333,stroke-width:1px
        H --> HA[Flamingo]:::detail
        style HA fill:#a2fa,stroke:#333,stroke-width:1px
        HA --> HAA[Visual encoding inspired by Flamingo]:::takeaway
    H --> HB[CoCa]:::detail
        style HB fill:#a2fa,stroke:#333,stroke-width:1px
        HB --> HBA[Visual encoding inspired by CoCa]:::takeaway
    H --> HC[PaLI]:::detail
        style HC fill:#a2fa,stroke:#333,stroke-width:1px
        HC --> HCA[Visual encoding inspired by PaLI]:::takeaway
        
    classDef takeaway fill:#f2b2,stroke:#333,stroke-width:1px
    classDef detail fill:#f2ff,stroke:#333,stroke-width:1px
    class C,D,E,F,G,H detail
    class CA,DA,EA,EB,FB,GA,GB,HA,HB,HC takeaway
    class DAA,DAB,DAC,DBA,DBB,DBC,DCA,DCB,DCC,DCD,EAA,EAB,EAC,EBA,EBB,FBA,FBB,GAA,GAB,GBA,GBB,HAA,HBA,HCA takeaway
    
```

---


### Key elements

*   **Root Node:** "Transformer Decoders in Gemini"
*   **Core Architecture:** Highlights the foundational use of Transformer decoders.
*   **Enhancements:** Details improvements made to the architecture for training stability and optimized inference.
*   **Context Length & Attention:** Focuses on the 32k context length and efficient attention mechanisms.
*   **Multimodal Input Handling:**  Details how the models handle various input modalities.
*   **Video & Audio Processing:** Details how the models encode videos and audio to ingest and process.
*   **Inspiration & Foundations:** Acknowledges inspiration from previous works (Flamingo, CoCa, PaLI).
*   **Styling:** Used `fill` and `stroke` to visually distinguish nodes and relationships, making the diagram easy to read and digest.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
