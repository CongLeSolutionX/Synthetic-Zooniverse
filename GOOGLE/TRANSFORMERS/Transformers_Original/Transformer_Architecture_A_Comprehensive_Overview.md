---
created: 2025-03-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Transformer Architecture - A Comprehensive Overview
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
title: Transformer Architecture - A Comprehensive Overview
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%{
  init: {
    'fontFamily': 'JetBrains Mono',
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
%%%%%%%% Mermaid version v11.4.1-b.14
graph LR
    subgraph Transformer["Transformer Architecture"]
        style Transformer fill:#2252,stroke:#005a9e,stroke-width:2px

        A["Input Tokens<br>(x<sub>1</sub>, ..., x<sub>n</sub>)"] --> B["Input Embeddings"]
        B --> C["Positional Encoding<br>(PE)"]
        C --> D["N Encoder Layers<br>(Typically 6)"]

        subgraph Encoder["Encoder Layer"]
            style Encoder fill:#22ff,stroke:#005a9e,stroke-width:2px
            E["Multi-Head<br>Self-Attention"] --> F["Add & Norm"]
            F --> G["Feed-Forward<br>Network"]
            G --> H["Add & Norm"]

            B --> E
            C --> E
            H -->|To Next Layer| D
        end

        D --> I["N Decoder Layers<br>(Typically 6)"]

        subgraph Decoder["Decoder Layer"]
            style Decoder fill:#d8e3,stroke:#005a9e,stroke-width:2px
            J["Masked Multi-Head<br>Self-Attention"] --> K["Add & Norm"]
            K --> L["Encoder-Decoder<br>Attention"]
            L --> M["Add & Norm"]
            M --> N["Feed-Forward<br>Network"]
            N --> O["Add & Norm"]

            S --> J
            T --> J
            H --> L
            O -->|To Next Layer| I
        end

        I --> P["Linear"]
        P --> Q["Softmax"]
        Q --> R["Output Probabilities<br>(y<sub>1</sub>, ..., y<sub>m</sub>)"]

        A --> S["Target Tokens<br>(y<sub>1</sub>, ..., y<sub>m-1</sub>)"]
        S --> T["Target Embeddings"]
        T --> U["Positional Encoding<br>(PE)"]
        U --> J
      
        subgraph Scaled_Dot_Product["Scaled Dot-Product Attention"]
            style Scaled_Dot_Product fill:#c8e9,stroke:#43a047,stroke-width:2px
            V["Inputs<br>(Q, K, V)"] --> W["QK<sup>T</sup> / √d<sub>k</sub>"]
            W --> X["Softmax"]
            X --> Y["Output"]
            V --> Y
        end
    end

    %% Connections to Scaled Dot-Product Attention
    E -- "Q, K, V" --> V;
    J -- "Q, K, V" --> V;
    L -- "Q from Decoder,<br>K, V from Encoder" --> V;

    %% Equations outside the flow
    %% Using a separate text object for better formatting and positioning
    classDef equationClass fill:#ffcc,stroke:#000,color:#000
    
    EQ1("<b>Positional Encoding (PE):</b><br>PE<sub>pos,2i</sub> = sin(pos/10000<sup>2i/d<sub>model</sub></sup>)<br>PE<sub>pos,2i+1</sub> = cos(pos/10000<sup>2i/d<sub>model</sub></sup>)"):::equationClass
    EQ2("<b>Multi-Head Attention:</b><br>MultiHead(Q, K, V) = Concat(head<sub>1</sub>, ..., head<sub>h</sub>)W<sup>O</sup><br>head<sub>i</sub> = Attention(QW<sub>i</sub><sup>Q</sup>, KW<sub>i</sub><sup>K</sup>, VW<sub>i</sub><sup>V</sup>)"):::equationClass
    EQ3("<b>Feed-Forward Network (FFN):</b><br>FFN(x) = max(0, xW<sub>1</sub> + b<sub>1</sub>)W<sub>2</sub> + b<sub>2</sub>"):::equationClass
    EQ4("<b>Softmax:</b><br>softmax(z<sub>i</sub>) = e<sup>z<sub>i</sub></sup> / Σ<sub>j</sub>e<sup>z<sub>j</sub></sup>"):::equationClass
    EQ5("<b>Scaled Dot-Product Attention:</b><br>Attention(Q, K, V) = softmax(QK<sup>T</sup> / √d<sub>k</sub>)V"):::equationClass

    %% Positioning the equations - Adjust coordinates (x,y) as needed to get the desired layout
    EQ1 -.-> C
    EQ2 -.-> E
    EQ3 -.-> G
    EQ4 -.-> Q
    EQ5 -.-> Scaled_Dot_Product

classDef notes fill:#ef59,stroke:#333,color:#000
N1("The diagram shows standard Transformer from 'Attention is all you need' paper"):::notes

linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37 stroke:#55,stroke-width:1px,stroke-dasharray: 2 2;
 
%% TODO: Update each node with related resources or further math calculation worksheet
%% Below are example syntax:
%% click B "https://en.wikipedia.org/wiki/Transformer_(machine_learning_model)" "Go to Enoclper WikiPage"
%% click D "https://en.wikipedia.org/wiki/Transformer_(machine_learning_model)" "Go to Decoder WikiPage"


```

DOI: [10.13140/RG.2.2.36429.55525](http://dx.doi.org/10.13140/RG.2.2.36429.55525)


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---