---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---



# Generative Models
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
title: Generative Models
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
    subgraph Generative_Models["Generative Models"]
        A["Generative Models (LLMs)"] --> B(Decoder-only Transformers)
        B --> C(Architecture)
        C --> C1(Input Sequence)
        C --> C2(Token Embeddings)
        C --> C3(Positional Embeddings)
        C --> C4(Transformer Blocks)
        C --> C5(Self-Attention)
        C --> C6(Feed-Forward Networks)
        C --> C7(Output Layer)
        C --> C8(Softmax Function)
        
        B --> D(Training)
        D --> D1(Maximum Likelihood Estimation)
        D --> D2(Gradient Descent)
        D --> D3(Large-Scale Training)
        
        B --> E(Application)
        E --> E1(Token Prediction)
        E --> E2(Text Generation)
        E --> E3(Prompting)
        
        A --> F(Other Architectures)
        F --> F1(Encoder-only)
        F --> F2(Encoder-Decoder)
        F --> F3(Comparison)
        F --> F4(Pre-training Tasks)

        subgraph Training_Details["Training Details"]
            D1 --> D1a(Log-likelihood maximization)
            D --> D2a(Gradient descent algorithms)
            D --> D3a(Distributed Training)
            D --> D3b(Data Parallelism)
            D --> D3c(Model Parallelism)
            D --> D3d(Tensor Parallelism)
            D --> D3e(Pipeline Parallelism)
        end

        subgraph Application_Details["Application Details"]
            E1 --> E1a(Inference)
            E1 --> E1b(Autoregressive Process)
            E1 --> E1c(Templates)
            E1 --> E1d(Prompt Engineering)
            E1 --> E1e(Instruction Following)
            E1 --> E1f(Zero-shot, One-shot, Few-shot Learning)
        end
        
        subgraph Model_Architecture_Details["Model Architecture Details"]
            F1 --> F1a(Input Sequence Encoding)
            F2 --> F2a(Input and Output Encoding)
            F2 --> F2b(Sequence-to-Sequence Tasks)
        end
        
        subgraph Model_Architecture_Tasks["Model Architecture Tasks"]
            F4 --> F4a(Language Modeling)
            F4 --> F4b(Masked Language Modeling)
            F4 --> F4c(Permuted Language Modeling)
            F4 --> F4d(Discriminative Training)
            F4 --> F4e(Denoising Autoencoding)
        end

        A --> G(Scaling Issues)
        G --> G1(Training at Scale)
        G --> G2(Long Sequence Modeling)
        G --> G3(Optimization from HPC Perspectives)
        G --> G4(Cache and Memory)
        G --> G5(Sharing Across Heads and Layers)
        G --> G6(Position Extrapolation and Interpolation)

        subgraph Scaling_Issues_Details["Scaling Issues Details"]
            G1 --> G1a(Data Preparation)
            G1 --> G1b(Data Quality)
            G1 --> G1c(Data Diversity)
            G1 --> G1d(Data Bias)
            G1 --> G1e(Privacy Concerns)

            G2 --> G2a(Context Length)
            G2 --> G2b(Text Generation based on Long Context)
            G2 --> G2c(Long Text Generation)
            G2 --> G2d(Long Text Generation with Long Context)
            
            G3 --> G3a(Low Precision Implementations)
            G3 --> G3b(Hardware-Aware Techniques)
            G3 --> G3c(Sequence Parallelism)
            G3 --> G3d(Mixed Precision Training)
            G3 --> G3e(Gradient Accumulation)

            G4 --> G4a(Fixed-size KV Cache)
            G4 --> G4b(Window-based Cache)
            G4 --> G4c(Moving Average-based Cache)
            G4 --> G4d(Recurrent Networks as Cache)
            G4 --> G4e(Hybrid Cache)
            G4 --> G4f(Memory Capacity)
            
            G5 --> G5a(Sharing across Heads)
            G5 --> G5b(Multi-Query Attention)
            G5 --> G5c(Grouped Query Attention)
            G5 --> G5d(Cross-layer Multi-head Attention)

            G6 --> G6a(Positional Embedding)
            G6 --> G6b(Extrapolation)
            G6 --> G6c(Interpolation)
            G6 --> G6d(Learnable Biases)
            G6 --> G6e(Rotary Positional Embedding)
            G6 --> G6f(Position Interpolation)
        end
    end
    
```

----

### Explaination
This Mermaid graph provides a more detailed representation of the "Generative Models" concept, including subgraphs for training, application, model architectures, scaling issues, and long sequence modeling.  Each subgraph is further broken down into specific concepts, such as various training methods (MLE, gradient descent), attention mechanisms, and positional encoding strategies. This level of detail allows for a more comprehensive understanding of the different facets of generative models within the context of the original document.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---