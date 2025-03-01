---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---


# Long Sequence Modeling
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


```mermaid
---
title: Long Sequence Modeling
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
    subgraph Long_Sequence_Modeling["Long Sequence Modeling"]
        A[Long Sequence Modeling] --> B(Efficient Attention Mechanisms)
        B --> C(Sparse Attention)
        B --> D(Linear Attention)
        B --> E(Other Efficient Attention Variants)
        
        subgraph Sparse_Attention["Sparse Attention"]
            C --> C1(Identifying Important Tokens)
            C --> C2(Pruning Attention Weights)
            C --> C3(Fixed-Size Window)
        end
        
        subgraph Linear_Attention["Linear Attention"]
            D --> D1(Replacing Softmax)
            D --> D2(Recursive State Updates)
            D --> D3(Fixed Computational Cost per Step)
        end

        A --> F(Memory-Based Models)
        F --> G(Fixed-Size KV Cache)
        F --> H(External Memories)

        subgraph Fixed_Size_KV_Cache["Fixed-Size KV Cache"]
            G --> G1(Window-based Cache)
            G --> G2(Moving Average Cache)
            G --> G3(Cumulative Average Cache)
            G --> G4(Neural Network as Cache)
            G --> G5(Hybrid Cache)
        end

        subgraph External_Memories["External Memories"]
            H --> H1(k-Nearest Neighbors)
            H --> H2(Retrieval Augmented Generation)
            H --> H3(Other External Memory Methods)
        end

        A --> I(Positional Encodings)
        I --> J(Learnable Biases)
        I --> K(Fixed Biases)
        I --> L(Rotary Positional Embedding)
        
        subgraph Positional_Encodings["Positional Encodings"]
            J --> J1(Relative Positional Embedding)
            J --> J2(T5 Bias)
            J --> J3(ALiBi)
            K --> K1(Linear Biases)
            K --> K2(Pre-computed Values)
        end

        A --> M(Memory Capacity)
        M --> M1(Storage Requirements)
        M --> M2(Model Complexity)
        M --> M3(Fixed-Size vs. Retrieval-Based Methods)
        M --> M4(Dynamic Context)
        
        A --> N(Sharing across Heads and Layers)
        N --> N1(Multi-Head Attention Sharing)
        N --> N2(Multi-Query Attention)
        N --> N3(Grouped Query Attention)
        N --> N4(Cross-Layer Attention)
        
        A --> O(Optimization from HPC Perspectives)
        O --> O1(Low-Precision Implementations)
        O --> O2(Hardware-Aware Techniques)
        O --> O3(Sequence Parallelism)
        O --> O4(Mixed-Precision Training)

        A --> S(Evaluating Long-Context LLMs)
        S --> S1(Perplexity Metric)
        S --> S2(Synthetic Tasks)
        S --> S3(Evaluation Benchmarks)
        S --> S4(Context Length Restrictions)
    end
    
```


----


### Explanation



This Mermaid graph provides a more detailed breakdown of "Long Sequence Modeling" incorporating concepts from the original source text.  It now explicitly shows how various methods for efficient attention, memory, positional encoding, and optimization techniques relate to handling long input sequences in LLMs.  It also includes the evaluation aspects.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---