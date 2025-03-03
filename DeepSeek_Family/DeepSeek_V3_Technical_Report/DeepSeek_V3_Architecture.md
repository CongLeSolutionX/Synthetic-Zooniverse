---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# DeepSeek V3 Architecture
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## DeepSeek V3 Architecture - A Diagrammatic Guide


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
    subgraph DeepSeek_V3_Architecture["DeepSeek V3 Architecture"]
        A[DeepSeek V3] --> B(Transformer Framework)
        B --> C("Multi-Head Latent Attention<br>(MLA)")
        B --> D(DeepSeekMoE)
        B --> E("Multi-Token Prediction<br>(MTP)")
        
        C --> C1(Input h<sub>t</sub>)
    
        C --> C2(Low-rank key/value compression)
        C2 --> C2a(Down-projection matrix W<sub>DKV</sub>)
        C2 --> C2b(Up-projection matrices W<sub>UK</sub>, W<sub>UV</sub>)
        C2 --> C2c("Rotary Position Embedding (RoPE) W<sub>KR</sub>")
    
        C --> C3("Concatenation<br>[q<sub>t,i</sub>; k<sub>t,i</sub>; v<sub>t,i</sub>]")
        C --> C4(Softmax Combination)
        C --> C5(Output u<sub>t</sub>)

        D --> D1(Shared Experts)
        D --> D2(Routed Experts)
    
        D --> D3(Gating Mechanism)
        D3 --> D3a(Token-to-expert affinity s<sub>i,t</sub>)
        D3 --> D3b(Sigmoid function)
        D3 --> D3c(Top-K selection)
    
        D --> D4(Auxiliary-loss-free load balancing)
        D4 --> D4a(Bias term b<sub>i</sub>)
        D4 --> D4b(Dynamic bias update)
    
        D --> D5(FFN Output h'<sub>t</sub>)
        D5 --> D5a(Sums of Shared & Routed FFN outputs)

        E --> E1(MTP Modules)
        E1 --> E1a("Shared embedding layer Emb(·)")
        E1 --> E1b("Shared output head OutHead(·)")
        E1 --> E1c("Transformer block TRM<sub>k</sub>(·)")
        E1 --> E1d("Projection matrix M<sub>k</sub>")
    
        E --> E2("Concatenation<br>[h<sub>k-1,i</sub>; Emb(t<sub>i+k</sub>)]")
        E --> E3("Transformer Block Input h'<sub>k,i</sub>")
        E --> E4("Output Representation h<sub>k,i</sub>")
        E --> E5("Softmax for Prediction Probabilities P<sub>k,i+k+1</sub>")

    end
    
```

DOI:[10.13140/RG.2.2.22614.56640](http://dx.doi.org/10.13140/RG.2.2.22614.56640)


---


### Explanation

This Mermaid diagram visualizes the DeepSeek V3 architecture. It's a high-level representation, with further details possible within each subgraph.

* **Transformer Framework:** The core foundation, represented by `B(Transformer Framework)`.
* **MLA (Multi-Head Latent Attention):**  The `C` subgraph details MLA's workings.  Nodes like `C2` and `C2a-c` show the low-rank compression and RoPE integration.  Key steps like concatenation and softmax are included.  There's an implicit relationship with the Transformer block, implied by its position in the overall architecture.
* **DeepSeekMoE:**  `D` subgraph details the MoE part.  Shows the separation of shared and routed experts.  The crucial gating mechanism is emphasized, with the use of affinity scores, sigmoid, and Top-K selection.  Also, the dynamic bias update is included as a critical part of load balancing.
* **Multi-Token Prediction (MTP):**  The `E` subgraph shows the MTP architecture, including the sequential prediction, shared layers, linear projection, and final softmax.  The sequential prediction of multiple tokens and the maintained causal chain is highlighted.

---


### Further Considerations

* **Relationships:** The arrows visually connect the different components and their flow.  For instance, the output of MLA (u<sub>t</sub>) feeds into the input of the DeepSeekMoE layer.
* **Hyperparameters:**  Adding labels to nodes (e.g., "d<sub>c</sub> = 512" for the compression dimension) or using a separate table will further enhance the diagram's detail and clarity.
* **Mathematical Equations:**  Incorporating the core equations (1-15, etc.) within the diagram as annotations will be very beneficial. This will create a more informative diagram.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---