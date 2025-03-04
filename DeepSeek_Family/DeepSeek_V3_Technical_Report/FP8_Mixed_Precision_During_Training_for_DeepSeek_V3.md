---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# FP8 Mixed Precision During Training for DeepSeek V3
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## FP8 Mixed Precision During Training - A Diagrammatic Guide



```mermaid
---
title: "DeepSeek-V3 Technical Report"
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
    subgraph FP8_Mixed_Precision["FP8 Mixed Precision"]
        A[FP8 Mixed Precision Training] --> B(Overview)
        A --> C(Fine-grained Quantization)
        A --> D(Increased Accumulation Precision)
        A --> E("Low-Precision Storage and Communication")
    end

    subgraph Overview["Overview"]
        B(Overview) --> B1(FP8 Data Format)
        B --> B2(Mixed Precision Framework)
        B --> B3(Targeted High Precision Operators)
        B --> B4(Numerical Stability Measures)
    end
    
    subgraph Fine_grained_Quantization["Fine-grained Quantization"]
        C("Fine-grained Quantization") --> C1(Tile-wise Scaling)
        C --> C2("Block-wise Scaling")
        C1 --> C1a("1x128 Tiles")
        C2 --> C2a("128x128 Blocks")
        C --> C3("Per-Group Scaling Factors")
    end

    subgraph Increased_Accumulation_Precision["Increased Accumulation Precision"]
        D("Increased Accumulation Precision") --> D1("Limited FP8 Accumulation")
        D --> D2("Promotion to CUDA Cores")
        D --> D3("FP32 Accumulation")
        D1 --> D1a("14-bit Precision")
        D2 --> D2a("Partial Results Copying")
        D2 --> D2b("Scaling Factors on CUDA Cores")
        D2 --> D2c("Minimizing Data Movements")
    end

    subgraph Low_Precision_Storage_Communication["Low-Precision Storage Communication"]
        E("Low-Precision Storage & Communication") --> E1("Low-Precision Optimizer States")
        E --> E2("Low-Precision Activations")
        E --> E3("Low-Precision Communication")
        E1 --> E1a("BF16 for AdamW")
        E2 --> E2a("E5M6 for Attention Outputs")
        E2 --> E2b("FP8 for other activations")
        E2 --> E2c("Integral Power-of-2 Scaling")
        E3 --> E3a("FP8 for MoE Up/Down Projections")
        E3 --> E3b("BF16 for Combine Components")
        E3 --> E3c("Warp-Level Casts")
    end
    
    B1 -- "FP8 Data Format<br>(4-bit exponent, 3-bit mantissa, and others if applicable)" --> B1
    B2 -- "Mixed Precision Framework<br>(FP8 for GEMM, BF16/FP32 for critical operations)" --> B2
    B3 -- "Targeted High Precision Operators<br>(Embedding, Output Head, Normalization, Attention, etc.)" --> B3
    B4 -- "Numerical Stability<br>(Master weights, weight gradients, and optimizer states in higher precision)" --> B4
    C1a -- "1x128 Tile<br>(Per token, per 128 channels)" --> C1
    C2a -- "128x128 Block<br>(Per 128 input channels, per 128 output channels)" --> C2
    C3 -- "Per-Group Scaling Factors<br>(Adapting scale for different element groups)" --> C3
    D1a -- "Limited 14-bit FP8 Accumulation" --> D1
    D2a -- "Intermediate Result Copying" --> D2
    D2b -- "Scaling Factors" --> D2
    D2c -- "Avoiding Data Movement Overhead" --> D2
    E1a -- "BF16 for AdamW" --> E1
    E2a -- "E5M6 for Attention Outputs" --> E2
    E2b -- "FP8 for Other Activations" --> E2
    E2c -- "Integral Power-of-2 Scaling" --> E2
    E3a -- "FP8 for MoE Up/Down Projections" --> E3
    E3b -- "BF16 for Combine Components" --> E3
    E3c -- "Warp-Level Casts" --> E3


```

---


### Explanation

This Mermaid graph provides a more focused view of FP8 mixed precision training in DeepSeek V3.  It builds upon the previous overview by diving deeper into the specific techniques and their interconnections.

*   **Subgraphs:** Organizes the components of FP8 training into logical groups, making the diagram easier to read and navigate.
*   **Arrows:** Connects different techniques to highlight their relationships and dependencies.
*   **Specific Details:** Includes detailed elements like "Tile-wise Scaling," "Block-wise Scaling," "FP32 Accumulation," and "Low-Precision Optimizer States."  This level of detail directly reflects the specific techniques described in the DeepSeek-V3 report.
*   **Relationships:**  Shows how the various FP8 techniques are integrated into the overall mixed precision framework and how they interact with other parts of the model (like the MoE architecture).


----

### How to use this as a starting point

This is a starting point; you would need to add more detail, using more sub-boxes and relationships, to fully represent the FP8 training details from the original document.  You could also add details of specific operators where FP8 is used or avoided, and figures and tables to enhance the clarity.  Remember to add labels, textual descriptions, and inline equations within the nodes to clarify the concepts and specific methods.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---