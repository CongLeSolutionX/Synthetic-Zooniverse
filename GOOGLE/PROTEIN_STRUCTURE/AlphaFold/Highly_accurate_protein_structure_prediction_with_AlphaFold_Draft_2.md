---
created: 2025-03-05 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://www.nature.com/articles/s41586-021-03819-2.pdf"
---



# Highly accurate protein structure prediction with AlphaFold
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## AlphaFold Model Paper Overview - A Diagrammatic Guide 



```mermaid
---
title: "Highly accurate protein structure prediction with AlphaFold"
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
    A[AlphaFold Architecture] --> B{Core Components}
    
    B --> C[Evoformer]:::detail
    C --> CA[Processes Inputs: MSAs & Pairwise Features.]
    CA --> CA1[Purpose: To produce a refined MSA representation and residue pair representation.]
    C --> CB[Iterative Refinement]
    CB --> CB1[Mechanism: Exchanges information within the MSA and pair representations]
    CB --> CB2[Impact: Direct Reasoning about Spatial and Evolutionary Relationships]
    C --> CC[Key Innovations]:::detail
    CC --> CC1[Outer Product Mean]
    CC --> CC2[Triangle Multiplicative Update]
    CC --> CC3[Axial Attention Variant]

    B --> D[Structure Module]:::detail
    D --> DA[Operates on: Concrete 3D Backbone Structure]
    DA --> DA1[Inputs: Pair representation & Single representation from Evoformer]
    D --> DB[Explicit 3D Structure]
    DB --> DB1["Representation: Rotations and Translations for each residue (global rigid body frames)"]
    DB --> DB2[Purpose: Prioritize orientation of protein backbone]
    D --> DC[Key Innovations]:::detail
    DC --> DC1[Breaking the chain structure]
    DC --> DC2[Equivariant Transformer]
    DC --> DC3[FAPE Loss Term]

    A --> E{Training}
    E --> F[Data]:::detail
    F --> FA["Labeled Data (PDB)"]
    F --> FB["Unlabeled Data (Uniclust30): Used for self-distillation"]
    E --> G[Self-Distillation]:::detail
    G --> GA[Mechanism: Trained network predicts structure of Uniclust30 sequences]
    G --> GB[Impact: Improves accuracy]
    E --> H[Masked MSA Loss]:::detail
    H --> HA["Objective: Predict masked elements of MSA sequences (BERT-style)"]
    H --> HB[Encourages: Learning phylogenetic and covariation relationships]
    
    E --> I[Loss Functions]:::detail
    I --> IA["Frame Aligned Point Error (FAPE)"]
    IA --> IA1[Compares predicted and true atom positions under different alignments]
    IA --> IA2[Creates Bias: For Atoms to be correct relative to local frame]
    I --> IB[Auxiliary Losses]
    IB --> IB1["Distogram prediction (binned distance distribution) with cross-entropy loss"]
    IB --> IB2[Per-residue lDDT-Cα prediction]
    IB --> IB3[Side-chain loss and Structure violation loss]

    A --> J{Inference}
    J --> K[Ensemble of Models]:::detail
    K --> KA[Use multiple trained models with different random seeds]
    K --> KB[Select Best: Use predicted confidence score to select best model per target]
    
    J --> L[Efficiency]:::detail
    L --> LA[Times: ~1 GPU minute for 384 residues]
    L --> LB[Faster Implementation: XLA Compiler]

    A --> M{Evaluation}
    M --> N[Metrics]:::detail
    N --> NA[lDDT-Cα: Backbone Accuracy]
    N --> NB["GDT: Domain Accuracy (CASP)"]
    N --> NC[TM-score: Global Superposition]
    N --> ND[r.m.s.d.95: Cα r.m.s.d. at 95% Coverage - Robust to Crystal Artifacts]

    A --> O{Limitations}
    O --> P[MSA Depth]:::detail
    P --> PA[Accuracy Decreases: Below ~30 sequences in MSA]
    P --> PB[Plateau: Little Gain Beyond ~100 Sequences]
    O --> Q[Inter-Chain Contacts]:::detail
    Q --> QA[Weaker for proteins with few intra-chain contacts compared to hetero-contacts]
    Q --> QB[High-Accuracy: Homomers, even intertwined chains]

    A --> R{Underpinning Principles}
    R --> S[Inductive Bias]:::detail
    S --> SA[Physical & Geometric: Build components that learn from PDB data]
    S --> SB[Minimal Handcrafted Features]
    S --> SC[Handle Missing Physical Context]
    S --> SD[Trained to produce the most likely protein structure to appear in the PDB]


    style A fill:#a2da,stroke:#333,stroke-width:1px
    style C fill:#c5cf,stroke:#333,stroke-width:1px
    style D fill:#c5cf,stroke:#333,stroke-width:1px
    style F fill:#a2fa,stroke:#333,stroke-width:1px
    style G fill:#f2aa,stroke:#333,stroke-width:1px
    style H fill:#f2aa,stroke:#333,stroke-width:1px
    style I fill:#f2aa,stroke:#333,stroke-width:1px
    style K fill:#a2bf,stroke:#333,stroke-width:1px
    style L fill:#a2bf,stroke:#333,stroke-width:1px
    style M fill:#a2fa,stroke:#333,stroke-width:1px
    style N fill:#c5cf,stroke:#333,stroke-width:1px
    style O fill:#a2fa,stroke:#333,stroke-width:1px
    style P fill:#f2bf,stroke:#333,stroke-width:1px
    style Q fill:#f2bf,stroke:#333,stroke-width:1px
    style R fill:#a2fa,stroke:#333,stroke-width:1px
    style S fill:#c5cf,stroke:#333,stroke-width:1px
    
```






---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---