---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2405.04324"
---



# Granite Code Models: A Family of Open Foundation Models for Code Intelligence
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Granite Code Models - A Diagrammatic Guide 

Below is a structured extraction of the concepts, framed for visualization as directed or undirected graphs, or factor graphs.



### 1. Training Data Pipeline

```mermaid
---
title: "IBM - Granite Code Models - Training Data Pipeline"
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
    "graph": { "htmlLabels": true, 'curve': 'linear' },
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
    A[Publicly Available Datasets] --> B(Language Filtering);
    B --> C(Quality Filtering);
    C --> D(Exact Deduplication);
    D --> E(Fuzzy Deduplication);
    E --> F(HAP/PII/Malware Filtering);
    A --> G(Natural Language Datasets);
    F --> H(Training Data);
    G --> H;
    style H fill:#ccf3,stroke:#333,stroke-width:2px
    A -- Github Code Clean, StarCoderData, GitHub Repos --> B
    B -- 116 Programming Languages --> C
    C --  25% alphabetic chars, XML/HTML Filters, JSON/YAML Filters --> D
    D -- SHA256 Hash --> E
    E -- MinHash, LSH, Jaccard Similarity (0.7) --> F
    F -- HAP Keywords, StarPII, ClamAV --> H
    G -- StackExchange, Arxiv, Wikipedia --> H
    
```

---


### 2. Model Architecture

```mermaid
---
title: "IBM - Granite Code Models - Model Architecture"
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
    "graph": { "htmlLabels": true, 'curve': 'linear' },
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
    A[Transformer Decoder] --> B{Granite Code Models}
    B --> C[Granite-3B-Code]
    B --> D[Granite-8B-Code]
    B --> E[Granite-20B-Code]
    B --> F[Granite-34B-Code]

    C --> C1[RoPE Embedding]
    C --> C2[Multi-Head Attention]
    C --> C3[RMSNorm]
    C --> C4[SwiGLU]

    C -- Context Length: 2048 --> C1
    C -- Hidden Size: 2560 --> C1
    C -- FFN Hidden Size: 10240 --> C1
    C -- Attention Heads: 32 --> C1
    C -- Layers: 32 --> C1

    D --> D1[GQA]
    D --> D2[RMSNorm]
    D --> D3[SwiGLU]

     D -- Context Length: 4096 --> D1
     D -- Hidden Size: 4096 --> D1
     D -- FFN Hidden Size: 14336 --> D1
     D -- Attention Heads: 32 --> D1
     D -- Key Value Heads: 8 --> D1
     D -- Layers: 36 --> D1

    E --> E1[MQA]
    E --> E2[LayerNorm]
    E --> E3[GELU]

     E -- Context Length: 8192 --> E1
     E -- Hidden Size: 6144 --> E1
     E -- FFN Hidden Size: 24576 --> E1
     E -- Attention Heads: 48 --> E1
     E -- Key Value Heads: 1 --> E1
     E -- Layers: 52 --> E1

   F --> F1[MQA]
    F --> F2[LayerNorm]
    F --> F3[GELU]
    
     F -- Context Length: 8192 --> F1
     F -- Hidden Size: 6144 --> F1
     F -- FFN Hidden Size: 24576 --> F1
     F -- Attention Heads: 48 --> F1
     F -- Key Value Heads: 1 --> F1
     F -- Layers: 88 --> F1

    style B fill:#ccf3,stroke:#333,stroke-width:2px
    
```

----


### 3. Training Process

```mermaid
---
title: "IBM - Granite Code Models - Training Process"
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
    "graph": { "htmlLabels": true, 'curve': 'linear' },
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
    A[Code Data] --> B("Phase 1:<br>Code Only Training")
    B --> C{Tokenizer}
    B --> D{Training Objective}
    D --> E[Causal Language Modeling Objective]
     D --> F[Fill-In-The-Middle Objective]
    C --> G["Byte Pair Encoding<br>(BPE)"]
    B --> H["Phase 2:<br>Code + Language Training"]
    H --> C
    H --> D
    E --> I[Trained Models]
    F --> I
    
    style I fill:#ccf3,stroke:#333,stroke-width:2px
    
    A -- "3.5-4.5 Trillion Tokens" --> B
    H -- "500 Billion Tokens (80% Code, 20% Lang)" --> C
    D -- "L = αL<sub>CLM</sub> + (1 − α)L<sub>FIM</sub>, α=0.5" --> E
    
```

-----


### 4. Instruction Tuning Process

```mermaid
---
title: "IBM - Granite Code Models - Instruction Tuning Process"
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
    "graph": { "htmlLabels": true, 'curve': 'linear' },
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
    A[Code Commits Dataset] --> E(Instruction Tuning);
    B[Math Datasets] --> E;
    C[Code Instruction Datasets] --> E;
    D[Language Instruction Datasets] --> E;
    
    E --> F[Noise Injection];
    E --> G[FlashAttention 2];
    E --> H[Cosine Scheduler];
    F --> I[Instruction Models];
    G --> I;
    H --> I;

    style I fill:#ccf3,stroke:#333,stroke-width:2px

    A -- "CommitPackFT" --> E
    B -- "MathInstruct, MetaMathQA" --> E
    C -- "Glaive, Self-OSS, NL2SQL" --> E
    D -- "HelpSteer, Platypus" --> E
    E -- "LR 10<sup>-5</sup>, 3 Epochs" --> H
    E -- "Noise Magnitude: 5*sqrt(Nh)" --> F
    
```

----


### 5. Evaluation Benchmarks

```mermaid
---
title: "IBM - Granite Code Models - Evaluation Benchmarks"
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
    "graph": { "htmlLabels": true, 'curve': 'linear' },
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
    A[Evaluation Tasks] --> B{Benchmarks}
    B --> C[HumanEvalSynthesize]
    B --> D[MultiPL-E]
    B --> E[MBPP/MBPP+]
    B --> F[DS1000]
    B --> G[RepoBench]
    B --> H[CrossCodeEval]
    B --> I[HumanEvalExplain]
    B --> J[HumanEvalFix]
    B --> K[CodeLingua]
    B --> L[CRUXEval]
    B --> M[MATH]
    B --> N[GSM8K]
    B --> O[SAT]
    B --> P[OCW]
     B --> Q[BFCL]
    B --> R[ReCode]
    
    style B fill:#ccf3,stroke:#333,stroke-width:2px
    A -- Code Generation --> C
    A -- Code Generation --> D
    A -- Code Generation --> E
    A -- Code Generation --> F
    A -- Code Generation --> G
    A -- Code Generation --> H
    A -- Code Explaination --> I
    A -- Code Fixing --> J
    A -- Code Translation --> K
    A -- Code Execution --> L
    A -- Math Reasoning --> M
    A -- Math Reasoning --> N
    A -- Math Reasoning --> O
    A -- Math Reasoning --> P
    A -- Function Calling --> Q
    A -- Model Robustness --> R
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---