---
created: 2025-03-02 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://arxiv.org/pdf/2205.14135"
---




# Flash Attention
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

### Flash Attention Overview
```mermaid
---
title: "FlashAttention - Fast and Memory-Eﬃcient Exact Attention with IO-Awareness"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false, 'curve': 'cardinal' },
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
    subgraph FlashAttention Overview
        A[FlashAttention] --> B{Core Idea};
        B -- IO-Aware Exact Attention --> C["Reduced Memory Accesses (HBM)"]
        B -- Tiling --> D[Divide Input into Blocks];
        B -- Recomputation --> E["Avoid Storing Intermediate Matrices"]
        C --> F["Faster Runtime (compared to standard attention)"]
        D --> G[Computation in Fast SRAM];
        E --> H[Recompute in Backward Pass];
        
        style A fill:#ccf3,stroke:#333,stroke-width:1px;
        style B fill:#ccf3,stroke:#333,stroke-width:1px;
    end
    
```



----

## Flash Attention

```mermaid
---
title: "FlashAttention - Fast and Memory-Eﬃcient Exact Attention with IO-Awareness"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false, 'curve': 'cardinal' },
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
    subgraph FlashAttention Overview
        A[FlashAttention] --> B{Core Idea}
        B -- IO-Aware Exact Attention --> C[Reduced HBM Accesses]
        B -- Linear Memory Footprint --> D[Efficient Memory]
        C --> E[Faster Runtime]
        D --> F[Reduced Memory Usage]
        C --> G[Optimized for Modern GPUs]
    end
    
    subgraph Memory Hierarchy
        H[GPU Memory Hierarchy] --> I["(SRAM){Fast, Small}"]
        I --> J["(HBM){High Bandwidth, Larger}"]
        J --> K["(DRAM){Slow, Large}"]
        style I fill:#ccf3,stroke:#333,stroke-width:1px
        style J fill:#ccf3,stroke:#333,stroke-width:1px
        style K fill:#ccf3,stroke:#333,stroke-width:1px
    end

    subgraph Standard Attention
        L[Standard Attention] --> M(Q)
        L --> N(K)
        L --> O(V)
        M --> P["(QK<sup>T</sup>){Matrix Multiplication}"]
        P --> Q["(S){Matrix S}"]
        Q --> R["(softmax(S)){Softmax}"]
        R --> S["(P){Matrix P}"]
        S --> T["(PV){Matrix Multiplication}"]
        T --> U["(O){Matrix O}"]
        U --> V["O(N<sup>2</sup>) Memory Footprint"]
        U --> W["O(N<sup>2</sup>) HBM Accesses"]
        U --> X["Slow Runtime"]
        style L fill:#ccf3,stroke:#333,stroke-width:1px
    end
    
    subgraph FlashAttention Algorithm
        Y[FlashAttention Algorithm] --> Z(Tiling)
        Z --> AA(Blocks of Q, K, V)
        AA -- Loaded into SRAM --> BB(Softmax Computations)
        BB -- Incremental Updates --> CC(O)
        CC -- Output --> DD["O(N log N) HBM Accesses"]
        CC -- Linear Memory Footprint --> EE[Efficient Memory]
        style Y fill:#ccf3,stroke:#333,stroke-width:1px
    end
    
    subgraph Block-Sparse FlashAttention
        FF[Block-Sparse FlashAttention] --> GG(Sparsity Mask)
        GG -- Mask Non-Zero Blocks --> HH(Reduced Computation)
        HH -- Reduced HBM Accesses --> II["O(N) HBM Accesses"]
        style FF fill:#ccf3,stroke:#333,stroke-width:1px
    end

    subgraph Experimental Results
        JJ[Experiments] --> KK(Runtime Comparisons)
        KK --> LL(FlashAttention vs Standard Attention)
        KK --> MM(FlashAttention vs Approximate Attention)
        KK -- Significant Speedups --> NN[Faster Training]
        
        JJ --> OO(Memory Footprint Comparisons)
        OO --> PP(FlashAttention vs Standard Attention)
        OO --> QQ(FlashAttention vs Approximate Attention)
        OO -- Linear Memory Scaling --> RR[Efficient Memory]
        style JJ fill:#ccf3,stroke:#333,stroke-width:1px
    end
    
    subgraph Limitations & Extensions
        SS[Limitations & Extensions] --> TT(CUDA Dependency)
        TT -- Limited Portability --> UU[Future Research]
        SS --> VV(IO-Aware Deep Learning Modules)
        SS --> WW(Multi-GPU Attention)
        SS --> XX(Sparse MLP Layers)
        SS --> YY(Kernel Methods)
        style SS fill:#ccf3,stroke:#333,stroke-width:1px
    end
```


----


### Explanation

This revised Mermaid diagram uses a more concise and focused representation of FlashAttention. It retains the subgraph structure for organizing related concepts but emphasizes the key aspects of FlashAttention's design and its experimental validation.  Color coding is used to distinguish different components.

* **Conciseness:**  The diagram eliminates unnecessary detail, focusing on the core concepts.
* **Emphasis:**  Key phrases like "Reduced HBM Accesses" and "Faster Runtime" are highlighted directly in the diagram.
* **Focus on Scaling:**  The scaling behavior (e.g., O(N log N) vs. O(N<sup>2</sup>)) is explicitly shown.
* **Clarity:**  Nodes and relationships are labeled clearly, making it easier to understand the different components.

Remember, for practical use, you should replace the placeholder names (e.g., "Blocks of Q, K, V") with more specific labels that accurately reflect the content of the original document.  Add inline equations and other visual cues as needed for clarity and quantitative insight.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---