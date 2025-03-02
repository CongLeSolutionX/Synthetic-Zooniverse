---
created: 2025-03-01 05:31:26
author: Cong Le
version: "2.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Transformer Architecture - Simplified Main Flow with Detailed Layer Subgraphs
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
title: Transformer Architecture - Parallel Processing of Encoder and Decoder
author: "Cong Le"
version: "2.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%{
  init: {
    "flowchart": { "htmlLabels": true, 'curve': 'stepBefore' },
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
    subgraph Transformer["Transformer Architecture"]
    style Transformer fill:#e834,stroke:#005a9e,stroke-width:2px

        A["Input Sequence<br>(x₁, ..., xₙ)"] --> B["Input Embeddings"]
        B --> C["Positional Encoding"]

        %% Encoder Stack
        C --> D1["Encoder Block 1<br>Input (from Pos. Encoding)"]
        D1 --> D2["Encoder Block 2<br>Input (from Block 1)<br>Output (to Block 3)"]
        D2 --> D3["..."]
        D3 --> DN["Encoder Block N<br>Input (from prev. layer)<br>Output (to Decoder)"]

        %% Decoder Stack (Placed horizontally beside Encoder)
        A -.-> S["Target Sequence<br>(y₁, ..., yₘ₋₁)"]
        S --> T["Target Embeddings"]
        T --> U["Positional Encoding"]
        U --> I1["Decoder Block 1<br>Input (from Pos. Encoding)"]

        I1 --> I2["Decoder Block 2<br>Input (from Block 1)<br>Output (to Block 3)"]
        I2 --> I3["..."]
        I3 --> IN["Decoder Block N<br>Input (from prev. layer)<br>Output (to Linear)"]


        %% Parallel Time/Step Arrow (Below Encoder and Decoder)
        TimeArrow[( )] == "Time/Step" ==> TimeArrowEnd[( )]

        %% Ghosted Connections (Conceptual Parallelism)
        D1 -.->|Conceptual Connection| I1
        D2 -.->|Conceptual Connection| I2
        D3 -.->|Conceptual Connection| I3
        DN -.->|Conceptual Connection| IN


        %% Final Stages (after parallel processing)
        IN --> P["Linear Layer"]
        P --> Q["Softmax"]
        Q --> R["Output Sequence<br>(y₁, ..., yₘ)"]

        %% Connections to show layer details (referencing side subgraphs)
        D1 -- "See Encoder Layer Detail" --> Encoder_Layer
        DN -- "See Encoder Layer Detail" --> Encoder_Layer
        I1 -- "See Decoder Layer Detail" --> Decoder_Layer
        IN -- "See Decoder Layer Detail" --> Decoder_Layer


     %% Position Nodes for Parallel Layout
        subgraph EncoderFlow
        %% direction LR
            D1
            D2
            D3
            DN
        end

        subgraph DecoderFlow
        %% direction LR
            I1
            I2
            I3
            IN
        end

        EncoderFlow --> TimeArrow
        DecoderFlow --> TimeArrow
    
        subgraph Encoder_Layer["Encoder Layer Detail"]
            style Encoder_Layer fill:#ccff2,stroke:#005a9e,stroke-width:1px
            En_MultiHead["Multi-Head<br>Self-Attention"] --> En_AddNorm1["Add & Norm"]
            En_AddNorm1 --> En_FFN["Feed-Forward<br>Network"]
            En_FFN --> En_AddNorm2["Add & Norm"]

            %% Input connections (Conceptual - not directly drawn in main flow)
            En_Input --> En_MultiHead

            %% Output connection (Conceptual - represented by layer stacking in main flow)
            En_AddNorm2 --> En_Output
        end

        subgraph Decoder_Layer["Decoder Layer Detail"]
        style Decoder_Layer fill:#ddf2,stroke:#005a9e,stroke-width:1px

            De_MaskedMultiHead["Masked<br>Multi-Head<br>Self-Attention"] --> De_AddNorm1["Add & Norm"]
            De_AddNorm1 --> De_EncDecAttn["Multi-Head<br>Encoder-Decoder<br>Attention"]
            De_EncDecAttn --> De_AddNorm2["Add & Norm"]
            De_AddNorm2 --> De_FFN["Feed-Forward<br>Network"]
            De_FFN --> De_AddNorm3["Add & Norm"]

            %% Input Connections (Conceptual)
            De_Input --> De_MaskedMultiHead
            De_EncoderOutput --> De_EncDecAttn

            %% Output Connection (Conceptual)
            De_AddNorm3--> De_Output
        end

        subgraph Scaled_Dot_Product_Attention["Scaled Dot-Product Attention"]
        style Scaled_Dot_Product_Attention fill:#c8e4,stroke:#43a047,stroke-width:2px
            Attn_Input["Input<br>(Q, K, V)"] --> Attn_ScaledDotProduct["Scaled<br>Dot-Product"]
            Attn_ScaledDotProduct --> Attn_Softmax["Softmax"]
            Attn_Softmax --> Attn_Output["Output"]
            Attn_Input --> Attn_Output
        end

        En_MultiHead -- "Q, K, V" --> Attn_Input
        De_MaskedMultiHead -- "Q, K, V" --> Attn_Input
        De_EncDecAttn -- "Q from Decoder,<br>K, V from Encoder" --> Attn_Input

        %% Formulas

        classDef formulaStyle fill:none,stroke:none,font-size:14px
        classDef formulaStyleSubText fill:none,stroke:none,font-size:10px

        PE_Formula1:::formulaStyle
        PE_Formula2:::formulaStyle

        MultiHead_Formula:::formulaStyle
        FFN_Formula:::formulaStyle
        SoftmaxFormula:::formulaStyle
        ScaledDotProduct_Formula:::formulaStyle

        C -.-> PE_Formula1("PE(pos, 2i) = sin(pos/10000<sup>2i/d<sub>model</sub></sup>)")
        C -.-> PE_Formula2("PE(pos, 2i+1) = cos(pos/10000<sup>2i/d<sub>model</sub></sup>)")
        U -.-> PE_Formula1
        U -.-> PE_Formula2

        En_MultiHead -.-> MultiHead_Formula("MultiHead(Q, K, V) = Concat(head<sub>1</sub>, ..., head<sub>h</sub>)W<sup>O</sup>")
        MultiHead_Formula -.-> head_i_sub:::formulaStyleSubText
        head_i_sub("head<sub>i</sub> = Attention(QW<sub>i</sub><sup>Q</sup>, KW<sub>i</sub><sup>K</sup>, VW<sub>i</sub><sup>V</sup>)")

        En_FFN -.- FFN_Formula("FFN(x) = max(0, xW<sub>1</sub> + b<sub>1</sub>)W<sub>2</sub> + b<sub>2</sub>")
        De_FFN -.- FFN_Formula
        Q -.-> SoftmaxFormula("softmax<br>(z<sub>i</sub>)<br>= e<sup>z<sub>i</sub></sup> / Σ<sub>j</sub>e<sup>z<sub>j</sub></sup>")

        Scaled_Dot_Product_Attention -.- ScaledDotProduct_Formula("Attention(Q, K, V) = softmax(QK<sup>T</sup> / √d<sub>k</sub>)V")

        En_AddNorm1 -.-> En_AddNorm1_Sub:::formulaStyleSubText
        En_AddNorm1_Sub("LayerNorm(x + Attention(x))")
        En_AddNorm2 -.-> En_AddNorm2_Sub:::formulaStyleSubText
        En_AddNorm2_Sub("LayerNorm(x + FFN(x))")

        De_AddNorm1 -.-> De_AddNorm1_Sub:::formulaStyleSubText
        De_AddNorm1_Sub("LayerNorm(x + MaskedAttention(x))")
        De_AddNorm2 -.-> De_AddNorm2_Sub:::formulaStyleSubText
        De_AddNorm2_Sub("LayerNorm(x + Attention(x))")
        De_AddNorm3 -.-> De_AddNorm3_Sub:::formulaStyleSubText
        De_AddNorm3_Sub("LayerNorm(x + FFN(x))")
        Attn_ScaledDotProduct -.-> Attn_ScaledDotProduct_Sub:::formulaStyleSubText
        Attn_ScaledDotProduct_Sub("QK<sup>T</sup> / √d<sub>k</sub>")
        Attn_Softmax -.-> Attn_Softmax_sub:::formulaStyleSubText
        Attn_Softmax_sub("softmax(QK<sup>T</sup> / √d<sub>k</sub>)")
        Attn_Output -.-> Attn_Output_sub:::formulaStyleSubText
        Attn_Output_sub("softmax(QK<sup>T</sup> / √d<sub>k</sub>)V")

        linkStyle 51,52,53,54 stroke:#ccc,stroke-width:1px,stroke-dasharray: 2 2
        linkStyle 56,59 stroke:#aaa,stroke-width:1px,stroke-dasharray: 5 5
    end

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---