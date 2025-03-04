---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# Communication Optimization During Training for DeepSeek V3
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Communication Optimization DeepSeek V3 - A Diagrammatic Guide


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
    subgraph Communication_Optimization_DeepSeek_V3["Communication Optimization DeepSeek V3"]
        A[DeepSeek-V3 Communication] --> B(DualPipe)
        B --> B1(Computation-Communication Overlap)
        B --> B2(Cross-Node All-to-All Communication)
        B --> B3(Warp Specialization)
        
        B1 --> B1a(Forward and Backward Chunk Division)
        B1 --> B1b(Attention, MLP, Dispatch, Combine)
        B1 --> B1c(Dynamic SM Allocation)
        
        B2 --> B2a(IB/NVLink Overlap)
        B2 --> B2b(Node-Limited Routing)
        B2 --> B2c(Warp Specialization)
        B2 --> B2d(Dynamic Communication Chunk Size)
        
        B3 --> B3a(Warp Specialization for IB/NVLink)
        B3 --> B3b(Dynamic Warp Allocation)

    end
    
    B1a --> B1a1("Dividing each chunk into four components: attention, all-to-all dispatch, MLP, and all-to-all combine.")
    B1a --> B1a2("Forward and backward chunks are processed in a way to overlap computations and communication.")
    B1a --> B1a3("Forward and backward chunks have their own specific scheduling<br>(Figure 4)")
    
    B1b --> B1b1("Attention and MLP are further split in the backward chunk (backward for input and backward for weights).")
    B1b --> B1b2("Micro-batches are processed in both forward and backward directions simultaneously.")
    B1b --> B1b3("The overlapping strategy ensures that both all-to-all and pipeline parallelism communication can be fully hidden during execution.")
    
    B2a --> B2a1("Data dispatched across nodes first via InfiniBand (IB).")
    B2a --> B2a2("Then forwarded within the node via NVLink.")
    B2a --> B2a3("Tokens are limited to at most 4 nodes per destination to reduce IB traffic.")
    
    B2b --> B2b1("Each token is only sent to a maximum number of nodes.")
    B2b --> B2b2("Nodes are selected based on highest affinity scores among experts.")
    
    B2c --> B2c1("Warps specialize in different communication tasks<br>(IB sending, NVLink forwarding, NVLink receiving).")
    B2c --> B2c2("Dynamic allocation of warps based on workload across SMs.")
    
    B2d --> B2d1("Customized PTX (Parallel Thread Execution) instructions are employed.")
    B2d --> B2d2("Auto-tuning of communication chunk size to minimize L2 cache usage and interference with other SMs.")
    
```


----


### Explanation


This Mermaid graph focuses on DeepSeek-V3's communication optimization during training.

* **Subgraph:**  Organizes the communication aspects into a distinct section.
* **Key Concepts:**  Highlights core elements like DualPipe, computation-communication overlap, and cross-node all-to-all communication.  It also emphasizes warp specialization and dynamic chunk size adjustments.
* **Relationships:**  Clearly illustrates how different optimization techniques (e.g., DualPipe) relate to the overall communication strategy (e.g., using both IB and NVLink).
* **Details:**  Provides more specifics about the methodology: division of chunks, component separation (attention, MLP, dispatch, combine), and dynamic resource allocation.

This is a high-level representation.  To be even more comprehensive, you would need to include specific details from the figures (e.g., Figure 4, which shows the overlapping execution) within the graph and potentially use different diagram types (like flowcharts) to show the precise scheduling details.  Also consider including specific performance metrics and comparisons with other methods.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---