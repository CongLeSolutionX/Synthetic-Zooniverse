---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2405.04434"
---



# DeepSeek V2 Architecture Details
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
title: DeepSeek V2 Architecture
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
    subgraph DeepSeek_V2_Architecture["DeepSeek V2 Architecture"]
        A[DeepSeek V2] --> B{Overall Architecture}
        B -- Transformer-based --> C[Transformer Block]
        
        C --> D["Attention Module (MLA)"]
        D --> E{"Low-Rank Key-Value Compression"}
        D --> F["Reduced KV Cache (≪ 2nhdhL)"]
        D --> G["Efficient Inference"]

        C --> H["Feed-Forward Network (FFN)"]
        H --> I[DeepSeekMoE]
        I --> J{Expert Segmentation}
        I --> K{Shared Expert Isolation}
        I --> L[Economical Training]
        
        D --> M["Decoupled Rotary Position Embedding (RoPE)"]
        M --> N[Reduced Activation Memory]
        M --> O[Maintains Inference Efficiency]
    end
    
    subgraph MLA_Details["MLA Details"]
        E -- KV Compression Dimension (dc) --> P(dc << ndh)
        E -- Up-projection Matrices (WuK, WuV) --> Q(dhnh x dc)
        E -- Down-projection Matrix (WdKV) --> R(dc x d)
        E -- Compressed Latent Vector (c_t) --> S(dt)
        
        M -- Queries (qt) --> T["Compressed Query Vector (c_q)"]
        M -- Keys (kt) --> U["Compressed Key Vector (c_k)"]
        M -- Values (vt) --> V["Compressed Value Vector (c_v)"]
        
    end
    
    subgraph DeepSeek_MoE_Details["DeepSeek MoE Details"]
        J -- Fine-grained Segmentation --> AA[Expert Specialization]
        J -- Shared Experts --> BB[Reduces Knowledge Redundancy]
        K -- Routed Experts --> CC[Expert Parallelism]
        K -- Device-limited Routing --> DD[Bounded Communication Costs]
        
        I -- FFN Output (h_t') --> EE["h_t' = u_t + Σ(FFN^(s)_i (u_t) + Σ(FFN^(r)_i (u_t))"]
        EE -- Shared Experts (FFN^(s)_i) --> FF[FFN function applied to shared experts]
        EE -- Routed Experts (FFN^(r)_i) --> GG[FFN function applied to routed experts]
        EE -- Gate Values (g_it) --> HH["g_it =  softmax_i(u_t^e)"]
        EE -- Token-to-Expert Affinity (s_it) --> II[s_it = expert affinity]
        EE -- Top-K Selection (Kr) --> JJ[Select top Kr routed experts]

    end

    subgraph Further_Details["Further Details"]
       O -- Other Optimizations --> KK[Layer Normalization]
       O --> LL[Activation Function]
       O --> MM[RMS Norm Layers]

       
       P --> NNNN[Optimized FlashAttention-2]
       
       L -- Balance Losses --> OO[LExpBal, LDevBal, LCommBal]
       L -- Token Dropping --> PP[Device-level Token Dropping Strategy]
    
    end
    
```


----


### Explanation

This diagram details the architecture of DeepSeek V2, focusing on the key components and their interrelationships.  It uses subgraphs to organize the complexities of MLA and DeepSeekMoE, providing a clear visual representation of their individual parts and how they interact.  The use of `<<subgraph>>` allows for better visualization and hierarchical organization of the architecture.  The diagram includes various components and parameters (e.g., `dc`, `dh`, `n_h`, etc.) that are critical to the understanding of the model's design choices.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---