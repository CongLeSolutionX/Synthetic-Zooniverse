---
created: 2025-03-10 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2103.00020"
---



# Transformer Encoder
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 



```mermaid
---
title: "CLIP - Learning Transferable Visual Models From Natural Language Supervision"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Transformer Encoder"] --> B{"Core Components"}

    subgraph Input_Embedding["Input Embedding"]
    style Input_Embedding fill:#f2b3,stroke:#333,stroke-width:1px
        B --> C["Text Input<br>(T)"]
        C --> CA["Lower-cased Byte Pair Encoding<br>(BPE)"]
        CA --> CAA["49,152 Vocabulary Size"]
        C --> CB["Max Sequence Length: 76"]
        CB --> CBA["[SOS] and [EOS] Tokens"]
    end

    subgraph Core_Architecture["Core Architecture"]
    style Core_Architecture fill:#a2f3,stroke:#333,stroke-width:1px
        B --> D["Transformer Layers"]
        D --> DA["12 Layers"]
        D --> DB["512-Wide Model"]
        D --> DC["8 Attention Heads"]
        D --> DD["Layer Normalization<br>(Before Transformer)"]
        D --> DE["Layer Normalization at the [EOS] token"]
        D --> DF["Linear Projection to Joint Embedding Space"]
        D --> DG["Masked Self-Attention<br>(Preserves LM Capability)"]
    end

    subgraph Output_Representation["Output Representation"]
    style Output_Representation fill:#f2a3,stroke:#333,stroke-width:1px
        B --> E["Feature Representation"]
        E --> EA["Activations of Highest Layer at [EOS] Token"]
        E --> EB["Layer Normalized"]
        E --> EC["Linearly Projected into Multi-Modal Embedding Space"]
    end

    subgraph Key_Properties["Key Properties & Functionality"]
    style Key_Properties fill:#f2f3,stroke:#333,stroke-width:1px
        B --> F["Role"]
        F --> FA["Text Encoder in CLIP"]
        F --> FB["Creates Text Embeddings for Cosine Similarity"]
        F --> FC["Synthesizes Zero-Shot Linear Classiﬁer Weights"]
        B --> G["Potential"]
        G --> GA["Initialization with Pre-trained Language Model"]
        G --> GB["Adding Language Modeling as an Auxiliary Objective"]
    end
    
```


DOI: [10.13140/RG.2.2.17996.73608](http://dx.doi.org/10.13140/RG.2.2.17996.73608)



---

### Explanation and Key Considerations

*   **Input Embedding:** It was specifically designed for CLIP's text encoding process. The BPE vocabulary size and sequence length are key architectural details.
*   **Core Architecture:** All specific details of Transformer Architecture were mentioned from the document.
*   **Output Representation:** Clearly specifies how to extract feature representation from the text encoder.
*   **Key Properties & Functionality:**  Highlights the role and utility of the transformer encoder in CLIP.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---