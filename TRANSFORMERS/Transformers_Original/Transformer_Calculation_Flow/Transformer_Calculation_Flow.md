---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

# Transformer Calculation Flow
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide with Equations


Below are a collection of Mermaid diagrams that incorporate key math equations at each step and block. These illustrations trace the calculation process inside the Transformer—from the processing of inputs to the generation of final outputs.

────────────────────────────

### Diagram 1. Input Processing (Embeddings & Positional Encoding)

────────────────────────────
```mermaid
---
title: "Input Processing (Embeddings & Positional Encoding)"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{init: {
  "flowchart": { "htmlLabels": false, "curve": "linear" },
  "theme": "dark",
  "fontFamily": "Fantasy",
  "themeVariables": {
      "primaryColor": "#BB2528",
      "primaryTextColor": "#f529",
      "primaryBorderColor": "#7C0000",
      "lineColor": "#F8B229",
      "secondaryColor": "#006100",
      "tertiaryColor": "#fff"
    }
}}%%
flowchart LR
    subgraph Input_Processing["Input Processing for 10k Tokens"]
    style Input_Processing fill:#23c5,stroke:#333,stroke-width:2px
        A["Token Sequence:<br>X = [x₁, x₂, …, x₁₀ₖ]"]
        B["Embedding Layer:<br>E = X · Wₑ<br>(Wₑ ∈ ℝ^(V×d₍model₎))"]
        C["Add Positional Encoding:<br>Eᵢ = Eᵢ + PE(i)<br>where:<br>PE(i, 2j) = sin(i/10000^(2j/d₍model₎))<br>and<br>PE(i, 2j+1) = cos(i/10000^(2j/d₍model₎))"]
    end
    
    A -->|Step 1| B
    B -->|Step 2| C
    
```
---


────────────────────────────

### Diagram 2. Encoder Block (Single Block Calculations)

────────────────────────────
```mermaid
---
title: "Encoder Block (Single Block Calculations)"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{init: {
  "flowchart": { "htmlLabels": false, "curve": "linear" },
  "theme": "dark",
  "fontFamily": "Fantasy",
  "themeVariables": {
      "primaryColor": "#BB2528",
      "primaryTextColor": "#f529",
      "primaryBorderColor": "#7C0000",
      "lineColor": "#F8B229",
      "secondaryColor": "#006100",
      "tertiaryColor": "#fff"
    }
}}%%
flowchart TD
    subgraph Encoder_Block["Encoder Block"]
    style Encoder_Block fill:#c332,stroke:#333,stroke-width:2px
        E1["Input:<br> Hᵢ ∈ ℝ^(10k×d₍model₎)"]
        Attn["Multi-Head Self-Attention:<br>• Q = Hᵢ · Wᵩ,<br>  K = Hᵢ · Wₖ,<br>  V = Hᵢ · Wᵥ<br>• Attention(Q,K,V) = softmax( QKᵀ/√(dₖ) ) · V"]
        AddNorm1["Residual & LayerNorm:<br>H' = LayerNorm(Hᵢ + Attention Output)"]
        FFN["Feed-Forward Network:<br>FFN(x) = max(0, x · W₁ + b₁) · W₂ + b₂"]
        AddNorm2["Residual & LayerNorm:<br>Output = LayerNorm(H' + FFN(H'))"]
    end
    E1 -->|Step 3| Attn
    Attn -->|Step 4| AddNorm1
    AddNorm1 -->|Step 5| FFN
    FFN -->|Step 6| AddNorm2
    
```

DOI: [10.13140/RG.2.2.24095.68002](http://dx.doi.org/10.13140/RG.2.2.24095.68002)


---


────────────────────────────

### Diagram 3. Encoder Stack Over Multiple Blocks

────────────────────────────
```mermaid
---
title: "Encoder Stack Over Multiple Blocks"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{init: {
  "flowchart": { "htmlLabels": false, "curve": "linear" },
  "theme": "dark",
  "fontFamily": "Fantasy",
  "themeVariables": {
      "primaryColor": "#BB2528",
      "primaryTextColor": "#f529",
      "primaryBorderColor": "#7C0000",
      "lineColor": "#F8B229",
      "secondaryColor": "#006100",
      "tertiaryColor": "#fff"
    }
}}%%
flowchart TD
    subgraph Encoder_Stack["Encoder Stack<br>(N Blocks)"]
    style Encoder_Stack fill:#c332,stroke:#333,stroke-width:2px
        A1["Positional-Encoded Embeddings:<br>E* ∈ ℝ^(10k×d₍model₎)"]
        B1["Encoder Block 1<br>(H₁ from Block 1)"]
        B2["Encoder Block 2<br>(H₂ from Block 2)"]
        B3["..."]
        BN["Encoder Block N<br>(H_N: Final Encoder Output)"]
    end
    A1 -->|Input to Block 1| B1
    B1 --> B2
    B2 --> B3
    B3 --> BN
    BN --> EO["Encoder Output:<br>EO = H_N ∈ ℝ^(10k×d₍model₎)"]
    
```

DOI: [10.13140/RG.2.2.10673.90721](http://dx.doi.org/10.13140/RG.2.2.10673.90721)


---


────────────────────────────

### Diagram 4. Decoder Block (Masked Self-Attention & Cross-Attention)

────────────────────────────
```mermaid
---
title: "Decoder Block (Masked Self-Attention & Cross-Attention)"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{init: {
  "flowchart": { "htmlLabels": false, "curve": "linear" },
  "theme": "dark",
  "fontFamily": "Fantasy",
  "themeVariables": {
      "primaryColor": "#BB2528",
      "primaryTextColor": "#f529",
      "primaryBorderColor": "#7C0000",
      "lineColor": "#F8B229",
      "secondaryColor": "#006100",
      "tertiaryColor": "#fff"
    }
}}%%
flowchart TD
    subgraph Decoder_Block["Decoder Block"]
    style Decoder_Block fill:#2ff2,stroke:#333,stroke-width:2px
        D1["Input:<br> Zᵢ <br>(Target Embeddings with PE)"]
        MaskedAttn["Masked Self-Attention:<br>• Q = Zᵢ·Wᶻ_Q,<br>  K = Zᵢ·Wᶻ_K,<br>  V = Zᵢ·Wᶻ_V<br>• Z_self = softmax( QKᵀ/√(dₖ) + M ) · V<br>(M: Causal Mask)"]
        LNormD1["Residual + LayerNorm:<br>Z' = LayerNorm(Zᵢ + Z_self)"]
        CrossAttn["Cross-Attention:<br>• Q' = Z'·Wᶻ'_Q<br>• Kₑ = EO·Wₑ_K,<br>  Vₑ = EO·Wₑ_V<br>• Z_cross = softmax( Q'Kₑᵀ/√(dₖ) ) · Vₑ"]
        LNormD2["Residual + LayerNorm:<br>Z'' = LayerNorm(Z' + Z_cross)"]
        FFN_D["Feed-Forward Network:<br>FFN(Z'') = max(0, Z''·W₁ + b₁)·W₂ + b₂"]
        LNormD3["Residual + LayerNorm:<br>Output = LayerNorm(Z'' + FFN(Z''))"]
    end
    
    D1 -->|Step A| MaskedAttn
    MaskedAttn -->|Step B| LNormD1
    LNormD1 -->|Step C| CrossAttn
    CrossAttn -->|Step D| LNormD2
    LNormD2 -->|Step E| FFN_D
    FFN_D -->|Step F| LNormD3
    
```

DOI: [10.13140/RG.2.2.29548.27522](http://dx.doi.org/10.13140/RG.2.2.29548.27522)

---


────────────────────────────

### Diagram 5. Decoder Stack & Final Output Projection

────────────────────────────
```mermaid
---
title: "Decoder Stack & Final Output Projection"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{init: {
  "flowchart": { "htmlLabels": false, "curve": "linear" },
  "theme": "dark",
  "fontFamily": "Fantasy",
  "themeVariables": {
      "primaryColor": "#BB2528",
      "primaryTextColor": "#f529",
      "primaryBorderColor": "#7C0000",
      "lineColor": "#F8B229",
      "secondaryColor": "#006100",
      "tertiaryColor": "#fff"
    }
}}%%
flowchart TD
    subgraph Decoder_Stack["Decoder Stack<br>(Multiple Blocks)"]
    style Decoder_Stack fill:#2ff2,stroke:#333,stroke-width:2px
        Dinit["Target Embeddings with PE:<br>Z* ∈ ℝ^(T×d₍model₎)"]
        DB1["Decoder Block 1"]
        DB2["Decoder Block 2"]
        DB3["..."]
        DBN["Decoder Block N<br>Z_final: Final Decoder Output"]
    end
    Dinit -->|Pass through Blocks| DB1
    DB1 --> DB2
    DB2 --> DB3
    DB3 --> DBN
    DBN --> FD["Final Decoder Representation:<br> Z_final"]
    FD -->|"Linear Transformation:<br> Logits = Z_final·Wₗ + bₗ"| LP["Linear Projection"]
    LP -->|"Softmax:<br> Probabilities = softmax(Logits)"| SM["Softmax Output:<br>ŷ = [ŷ₁, ŷ₂, …, ŷ_V]"]
    
```

DOI: [10.13140/RG.2.2.19481.94569](http://dx.doi.org/10.13140/RG.2.2.19481.94569)

---


────────────────────────────

### Diagram 6. Full Transformer Architecture Flow Overview

────────────────────────────
```mermaid
---
title: "Full Transformer Architecture Flow Overview"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{init: {
  "flowchart": { "htmlLabels": false, "curve": "linear" },
  "theme": "dark",
  "fontFamily": "Fantasy",
  "themeVariables": {
      "primaryColor": "#BB2528",
      "primaryTextColor": "#f529",
      "primaryBorderColor": "#7C0000",
      "lineColor": "#F8B229",
      "secondaryColor": "#006100",
      "tertiaryColor": "#fff"
    }
}}%%
flowchart LR
    Inputs["Input Sequence:<br>X = [x₁, …, x₁₀ₖ]"]
    Embeddings["Embedding + Positional Encoding:<br>E = X·Wₑ + PE"]
    Encoder["Encoder Stack:<br>EO = TransformerEncoder(E)"]
    Target["Target Sequence (for decoder):<br>Y = [y₁, …, yₜ₋₁]"]
    Decoder["Decoder Stack:<br>Z_final = TransformerDecoder(Y, EO)"]
    Projection["Final Output Projection:<br>Logits = Z_final·Wₗ + bₗ<br>ŷ = softmax(Logits)"]

    Inputs --> Embeddings
    Embeddings --> Encoder
    Encoder --> EO
    Target --> Decoder
    EO ---|Cross-Attention| Decoder
    Decoder --> Projection
    
```

DOI: [10.13140/RG.2.2.26192.83203](http://dx.doi.org/10.13140/RG.2.2.26192.83203)

----


These diagrams, with embedded equations, illustrate the following:

• The input tokens X are converted into embeddings using a weight matrix Wₑ and then enhanced with positional encodings PE.  
• In each encoder block, the self‑attention mechanism computes queries, keys, and values (using learned matrices Wᵩ, Wₖ, and Wᵥ) and applies the scaled dot-product attention formula. A residual connection and layer normalization follow; then, an FFN is applied with its own residual connection and normalization.  
• The encoder stack applies these blocks sequentially to produce an encoder output EO.  
• In the decoder block, target embeddings (with PE) first undergo masked self‑attention (ensuring autoregressive behavior) and then attend to the encoder outputs via cross‑attention. Residual connections and layer normals accompany each sub-layer, and an FFN is again applied.  
• Finally, the decoder’s output is projected via a linear layer followed by a softmax to yield the final probability distribution ŷ over the vocabulary.

Together, these diagrams with math equations provide a step-by-step reference to the calculations that occur in a standard Transformer architecture.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---