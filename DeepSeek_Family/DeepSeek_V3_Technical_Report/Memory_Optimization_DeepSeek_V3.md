---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# Memory Optimization During Training for DeepSeek V3s
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Memory Optimization DeepSeek V3 - A Diagrammatic Guide


```mermaid
---
title: "DeepSeek-V3 Technical Report"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'cardinal' },
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
    subgraph Memory_Optimization_DeepSeek_V3["Memory Optimization DeepSeek V3"]

        style A fill:#ccf3,stroke:#333,stroke-width:2px
        A[DeepSeek V3 Memory Optimization] --> B(Recomputation)
        A --> C(EMA)
        A --> D(Shared Embedding/Output)
        A --> E(Low-Precision Activation)
        A --> F(Low-Precision Communication)
    end
    
    subgraph Recomputation["Recomputation"]
        B(Recomputation) --> B1(RMSNorm)
        B --> B2(MLA Up-projections)
        B1 --> B1a("Recompute RMSNorm operations during backpropagation")
        B2 --> B2a("Recompute MLA up-projections during backpropagation")
        
    end
    
    subgraph EMA["EMA"]
        C(EMA) --> C1("Exponential Moving Average (EMA) of model parameters")
        C1 --> C1a("Stored in CPU memory")
        C1 --> C1b("Updated asynchronously")
        C1 --> C1c("Used for early performance estimation")
    end
    
    subgraph Shared_Embedding_Output["Shared Embedding Output"]
        D(Shared Embedding/Output) --> D1("Shallowest (embedding) and deepest (output) layers on same PP rank")
        D1 --> D1a("Physical sharing of parameters and gradients")
        D1 --> D1b("Reduces memory overhead")
    end
    
    subgraph Low_Precision_Activation["Low Precisio Activation"]
        E(Low-Precision Activation) --> E1("Activations in FP8 format")
        E --> E2("Fine-grained quantization (1x128 tiles)")
        E --> E3("Special E5M6 format for activations after attention")
        E --> E4("Recomputation of SwiGLU operator inputs in FP8")
    end
    
    subgraph Low_Precision_Communication["Low Precision Communication"]
        F(Low-Precision Communication) --> F1("Quantize activations before MoE up-projections")
        F --> F2("FP8 compatibility with FP8 Fprop in MoE up-projections")
        F --> F3("Special considerations for scaling factors (integer powers of 2)")
        F --> F4("BF16 for forward and backward combine components")
        F --> F5("Quantize activation gradients before MoE down-projections")
    end

```


---


### Explanation

This Mermaid graph outlines the key memory optimization strategies used during DeepSeek V3 training, based on the provided text.

*   **Subgraphs:** Organize related optimization techniques into distinct sections.
*   **Nodes:** Each box represents a specific technique or concept related to memory optimization.
*   **Arrows:** Show the relationships between the optimization strategies.  For example, the arrow from "Recomputation" to "Shared Embedding/Output" indicates that recomputation reduces the need for storing intermediate results, freeing up memory.
*   **Details:** Each node includes a brief description of the technique or a quote directly from the text for clarity.

---

### Key Enhancements

*   **Recomputation:**  The model recomputes intermediate activations during backpropagation, eliminating the need to store them in memory. This is a major memory-saving technique.
*   **EMA in CPU:**  Storing the Exponential Moving Average (EMA) of parameters in CPU memory reduces GPU memory footprint.
*   **Shared Embedding/Output:** Sharing the shallowest and deepest layers of the model within a single pipeline rank minimizes memory usage.
*   **Low-Precision Activation:**  The model quantizes activations and inputs to the SwiGLU operator to FP8, reducing the memory consumption of activations in the model.  Special cases, like activations after attention operators, use a customized E5M6 format to maintain high-precision training.
*   **Low-Precision Communication:** Quantizing activations before MoE up-projections, and activation gradients before MoE down-projections to FP8, reduces the memory and communication overhead in the MoE training process, while keeping critical components in BF16 to ensure numerical stability.

---


### Further Considerations

*   **Visual Enhancements:** You can use different colors or shapes to highlight different parts of the memory optimization process.
*   **Relationships to Other Parts:** Add edges to connect this optimization strategy to the overall DeepSeek-V3 architecture and training framework. For example, add an edge from "Recomputation" to "DualPipe" to show how the recomputation strategy aligns with the DualPipe algorithm's use of pipeline parallelism.
*   **Quantitative Data:** Include specific memory reduction percentages (if available) or approximate values in the nodes to make the diagram even more informative.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---