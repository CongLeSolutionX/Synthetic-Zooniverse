---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2412.19419"
---


# Graph Neural Networks Architecture
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Graph Neural Networks Architecture - A Diagrammatic Guide 



```mermaid
---
title: "Introduction to Graph Neural Networks"
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
    subgraph GNN_Architecture["Graph Neural Network Architecture"]
        A["Graph Neural Network Encoder"] --> B("Pre-processing Layers")
        B --> B1("Input Node Attributes")
        B1 -- "xi" --> B2("Feedforward Neural Networks")
        B2 -- "σ(Wxi + b)" --> B3("Node Features")
        B3 -- "˜xi" --> C("Message-Passing Layers")


        C --> C1["Message Passing Function"]
        C1 --  "h(k)i" --> C2
        C1 -- "Aggregation Function<br>(cid:76)" --> C3
        C1 -- "Neighbor Nodes<br>(Ni)" --> C4
        C1 -- "Node-to-Node Interactions<br>(µij)" --> C5
        C2 -- "(cid:94)" --> C6("h(k+1)i")
        C6 -- "h(k+1)i" --> D("Post-processing Layers")
        D -- "hi" --> D1("Feedforward Neural Networks")
        D1 -- "σ(W hi + b)" --> D2("Node Embeddings")
        D2 -- "zi" --> E["Output Node Embeddings"]
        
        C1 --> C6["Update Function<br>(ϕ)"]
    
        subgraph Aggregation_Function["Aggregation Function"]
            C3 --> C7("Sum")
            C3 --> C8("Mean")
            C3 --> C9("Max")
            C3 --> C10("Concatenation")
        end
        
        subgraph Node_to_Node_Interactions["Node-to-Node Interactions"]
            C5 --> C11("Convolutional")
            C11 -- "wijψ(h(k)j)" --> C12
            C11 -- "wij" --> C13["Learned or Fixed Weights"]
            C11 -- "ψ(h(k)j)" --> C14["Transformation Function"]
            
            C5 --> C15("Message Passing")
            C15 -- "ψ(h(k)i, h(k)j)" --> C16
            
            C5 --> C17("Attentional")
            C17 -- "a(h(k)i, h(k)j)ψ(h(k)j)" --> C18
            C17 -- "αij" --> C19["Learned Attention Weights"]

        end

    end
    
```

DOI:[10.13140/RG.2.2.29692.45441](http://dx.doi.org/10.13140/RG.2.2.29692.45441)


----


### Explanation

This diagram visualizes a typical Graph Neural Network (GNN) encoder architecture, focusing on the message-passing mechanism.  Key elements are:

* **Pre-processing Layers (B):**  These are optional layers that operate on the input node attributes (`xi`) to produce a new set of node features (`˜xi`).  These layers are usually simple feedforward neural networks.

* **Message-Passing Layers (C):**  This is the core of the GNN.  It takes the processed node features (`h(k)i`) and information about the node's neighbors (`Ni`) and their interactions (`µij`) to update the node's features for the next layer (`h(k+1)i`).  The message-passing function (`ϕ`) is crucial for aggregating information.

    * **Aggregation Functions (C3-C10):**  Various ways to aggregate information from neighbors.  Common choices are sum, mean, max, and concatenation.  The diagram shows these as separate branches to highlight their distinct roles.

    * **Node-to-Node Interactions (C5, C11-C18):** How the features of a node interact with the aggregated features of its neighbors.  Different GNN architectures use different types of interactions:
        * **Convolutional (C11):**  Fixed or learned weights (`wij`) are used to modulate the contribution of each neighbor. A transformation function (`ψ`) may be applied to the neighbor's features.
        * **Message Passing (C15):**  A function (`ψ`) directly takes the features of both the current node and its neighbor to determine the interaction.
        * **Attentional (C17):** Learns scalar-valued attention weights (`αij`) to focus on relevant neighbors.  A transformation function (`ψ`) may also be involved.

* **Post-processing Layers (D):**  These layers are also optional and refine the node features (`hi`) produced by the message-passing layers to generate the final node embeddings (`zi`).  They also use feedforward neural networks.

* **Output Node Embeddings (E):** The final representation of each node. These embeddings are used as input for the decoder in downstream tasks.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---