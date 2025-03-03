---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# DeepSeek V3 Training
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## DeepSeek V3 Training - A Diagrammatic Guide


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
    subgraph DeepSeek_V3_Training["DeepSeek V3 Training"]
        A[DeepSeek-V3 Training] --> B(Pre-Training)
        A --> C(Context Extension)
        A --> D(Post-Training)
        B --> B1(Data Construction)
        B --> B2(Hyperparameters)
        B --> B3(Training Process)
        C --> C1(YaRN)
        D --> D1(SFT)
        D --> D2(RL)
        
    end
    
    subgraph PreTraining["Pre-Training"]
        B1(Data Construction) --> B1a(Multilingual Corpus)
        B1a --> B1b(English/Chinese Emphasis)
        B1a --> B1c(Data Diversity/Redundancy Reduction)
        B1a --> B1d(Document Packing)
        B1a --> B1e("Fill-in-the-Middle (FIM)")
        B1e --> B1f("Prefix-Suffix-Middle (PSM) Framework")
        B1a --> B1g(Byte-level BPE Tokenizer)
        B1a --> B1h(Multilingual Compression)
        B1a --> B1i(Token Boundary Bias Mitigation)

        B2(Hyperparameters) --> B2a("Transformer Layers (61)")
        B2a --> B2b("Hidden Dimension (7168)")
        B2a --> B2c("Random Initialization (σ = 0.006)")
        B2a --> B2d(MLA Heads/Dimensions)
        B2a --> B2e("DeepSeekMoE Experts")
        B2a --> B2f("MTP Depth (D=1)")
        B2a --> B2g(RMSNorm Layers)
        B2a --> B2h(Scaling Factors)

        B3(Training Process) --> B3a(AdamW Optimizer)
        B3a --> B3b("Optimizer Hyperparameters<br>(β1, β2, weight_decay)")
        B3a --> B3c(Learning Rate Scheduling)
        B3a --> B3d(Batch Size Scheduling)
        B3a --> B3e(Gradient Clipping)
        B3a --> B3f("Node-Limited Routing<br>(M=4)")
        B3a --> B3g("Auxiliary-Loss-Free Load Balancing<br>(γ)")
        B3a --> B3h("Balance Loss<br>(α)")
        B3a --> B3i("MTP Loss Weight<br>(λ)")
        B3a --> B3j("Training Tokens<br>(14.8T)")
        B3a --> B3k("Training Duration/Stability")
    end

    subgraph ContextExtension["Context Extension"]
        C1("YaRN") --> C1a("Context Window Extension<br>(4K -> 32K -> 128K)")
        C1 --> C1b("YaRN Configuration")
        C1 --> C1c("Steps/Hyperparameters")
        C1 --> C1d("Sequence Length/Batch Size Adjustment")
        C1 --> C1e("Learning Rate")
    end
   

    subgraph PostTraining["Post-Training"]
        D1("SFT") --> D1a("Instruction Tuning Data")
        D1 --> D1b("Epochs")
        D1 --> D1c("Learning Rate Decay")
        D1 --> D1d("Sequence Packing")
        D1 --> D1e("Sample Masking")

        D2("RL") --> D2a("Reward Models")
        D2a --> D2b("Rule-Based")
        D2a --> D2c("Model-Based")
        D2a --> D2d("Data Generation Sources")
        D2 --> D2e("Group Relative Policy Optimization<br>(GRPO)")
        D2e --> D2f("Hyperparameters<br>(ε, β)")
        D2e --> D2g("Prompt Diversity")

    end

```

DOI:[10.13140/RG.2.2.36036.33921](http://dx.doi.org/10.13140/RG.2.2.36036.33921)


---


### Explanation

This Mermaid graph provides a more detailed representation of the DeepSeek-V3 training process, breaking down the pre-training, context extension, and post-training stages.  The graph now includes more specific details about the data construction, hyperparameters, and the various training steps involved in each stage.

* **Subgraphs:**  Organize training stages (Pre-training, Context Extension, Post-training) for better readability and comprehension.
* **Nodes and Relationships:** Explicitly show the connections between the different components of the training pipeline.
* **Detailed Components:**  Break down hyperparameters (e.g., learning rate scheduling) and training steps (e.g., document packing, sample masking).
* **Data Flow:**  The graph visually represents how data flows through the different stages of the training process.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---