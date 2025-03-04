---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://azure.microsoft.com/en-us/blog/empowering-innovation-the-next-generation-of-the-phi-family/"
---




# Phi-4 Multimodal
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## Phi-4 Multimodal - A Diagrammatic Guide


```mermaid
---
title: "The Next Generation of the Phi Family by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false, 'curve': 'linear' },
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
%%%%%%%% Mermaid version v11.4.1-b.14
graph LR
    subgraph Phi_4_Multimodal["Phi-4 Multimodal"]
        A[Phi-4-Multimodal] --> B{Multimodality}
        B --> C[Speech Input]
        B --> D[Vision Input]
        B --> E[Text Input]
        
        A --> F[Unified Architecture]
        F --> G[Mixture-of-LoRAs]
        G --> C
        G --> D
        G --> E
        
        A --> H[Core Capabilities]
        H --> I[Speech Recognition]
        I --> IA["Word Error Rate (6.14%) - Outperforms WhisperV3"]
        H --> J[Speech Translation]
        H --> K[Speech Summarization]
        H --> L[Visual Reasoning]
        L --> LA[Document Understanding]
        L --> LB[Chart/Table Understanding]
        L --> LC[Mathematical/Scientific Reasoning]

        A --> M[Deployment]
        M --> N[On-Device Inference]
        M --> O[Edge Computing]

        A --> P[Model Size]
        P --> PA[5.6 Billion Parameters]
        
        A --> Q[Vocabulary]
        Q --> QA[Large Vocabulary - Improved Processing]
        
        A --> R[Multilingual Support]
        R --> RA[Multilingual Capabilities]
        
        A --> S[Benchmark Comparisons]
        S --> SA["Table: Phi-4-Multimodal vs. Other Models<br>(Speech, Vision)"]
        SA --> SB["Benchmark comparisons against other models<br>(e.g. WhisperV3, Gemini)"]
    
        A --> T[Latency & Efficiency]
        T --> TA[Low Latency]
        T --> TB[Optimized for On-device Execution]
        
        A --> U[Limitations]
        U --> UA["Fewer Capabilities for Speech Question Answering (QA)"]

    end

```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---