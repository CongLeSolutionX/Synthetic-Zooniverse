---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Decomposition of Probabilistic Models
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Decomposition of Probabilistic Models - A Diagram Structure


```mermaid
---
title: Decomposition of Probabilistic Models
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
    A[Decomposition of Probabilistic Models] --> B(Directed Acyclic Graphs)
    B --> C(Bayesian Networks)
    C --> D{Nodes and Directed Edges}

    subgraph Bayesian_Network_Example["Bayesian Network Example"]
        D -- Example: p(X, Y, Z) = p(Z|X, Y)p(Y|X)p(X) --> E
        E -- X --> F[X]
        E -- Y --> G[Y]
        E -- Z --> H[Z]
        E -- X --> I("p(X)")
        E -- Y --> J("p(Y|X)")
        E -- Z --> K("p(Z|X, Y)")
    end
    
    subgraph Decomposition_Breakdown["Decomposition Breakdown"]
        B --> BA(Conditional Independence)
        BA -- Example:<br>X ⊥⊥ Y | Z --> BB
        BB -- p(X, Y | Z) = p(X | Z) p(Y | Z) --> BC
            %% BC -- Implications: Inference & computation become simpler;
            %% BC -- Example:  x influences y, but only if z is known.
    end

    A --> B1(Undirected Graphs)
    B1 --> C1(Markov Random Fields)
    C1 --> D1{Nodes and Undirected Edges}
    
    subgraph Markov_Random_Field_Example["Markov Random Field Example"]
    D1 -- Example:<br>p(X, Y, Z) = p(X|Y)p(Y|Z)p(Z|X) --> E1
        E1 -- X --> F1[X]
        E1 -- Y --> G1[Y]
        E1 -- Z --> H1[Z]
        E1 -- X --> I1("p(X|Y)")
        E1 -- Y --> J1("p(Y|Z)")
        E1 -- Z --> K1("p(Z|X)")
    end
    
    subgraph Factor_Graph_Example["Factor Graph Example"]
        B2 --> C2(Factor Graphs)
        C2 --> D2{Nodes for Variables and Factors}
        D2 -- Example:<br>p(X, Y, Z) = f(X, Y)f(Y, Z)f(Z, X) --> E2
        E2 -- X --> F2[X]
        E2 -- Y --> G2[Y]
        E2 -- Z --> H2[Z]
        E2 -- X --> I2["f(X, Y)"]
        E2 -- Y --> J2["f(Y, Z)"]
        E2 -- Z --> K2["f(Z, X)"]
    end
    
    subgraph Summary["Summary"]
        C --> CC[Joint Distribution]
        CC --> CC1["p(x1, ..., xK) =  ∏ p(xk|pak)"]
        CC --> CC2[pak: Parent nodes of xk]
        CC --> CC3[xk: Random Variables]

        CC --> CC4[Visualizing dependencies]
        CC --> CC5[Simplifying inference and learning]
        CC --> CC6[Motivation for new statistical models]

        C1 --> CC7[Visualizing dependencies]
        C1 --> CC8[Simplifying inference and learning]
        C1 --> CC9[Motivation for new statistical models]
        C1 --> CC10[Conditional independence properties are revealed by the graph structure]

        C2 --> CC11[Visualizing dependencies]
        C2 --> CC12[Simplifying inference and learning]
        C2 --> CC13[Motivation for new statistical models]
        C2 --> CC14[Handling both directed and undirected relationships]
    end

```

----


### Explanation

This Mermaid diagram visually decomposes probabilistic models into three primary types (Bayesian Networks, Markov Random Fields, and Factor Graphs).  Each subgraph focuses on a different aspect of model decomposition, making the diagram a more focused and structured representation of the topic.

*   **Subgraphs:** The diagram uses subgraphs to organize related concepts (e.g., Bayesian Networks, Markov Random Fields, Factor Graphs), making the overall structure more digestible.

*   **Clear Examples:** Each subgraph provides concrete examples of how joint probability distributions (`p(X, Y, Z)`) are factorized, demonstrating how variables depend on each other (in the case of Directed Acyclic Graphs) or mutually (in the case of Markov Random Fields).

*   **Conditional Independence:** The diagram highlights the importance of conditional independence as a critical concept in these models. The decomposition into factors based on conditional independence simplifies the complexity of the models and facilitates inference and computation.

*   **Summary subgraph:** This provides a concise summary of how the decomposition impacts inference, model learning, and visualization. This shows how the graph structure provides a direct representation of the model's dependencies.

----

### Key improvements over the previous diagram

*   **Focus:**  This diagram focuses more specifically on the decomposition aspect.
*   **Clarity:** The use of subgraphs improves clarity by grouping similar model types.
*   **Conciseness:** It avoids redundant information.
*   **Context:** The addition of implications and examples provides more context.


This updated diagram offers a more comprehensive and focused view of the decomposition of probabilistic models, suitable for understanding their structure and application in various contexts. Remember to adapt these nodes and edges according to the specific elements of the probabilistic models you wish to represent. Remember to include relevant equations and annotations to enhance clarity and context.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---