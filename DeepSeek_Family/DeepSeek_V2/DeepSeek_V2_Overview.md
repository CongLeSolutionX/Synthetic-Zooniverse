---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2405.04434"
---



# DeepSeek-V2: A Strong, Economical, and Efficient Mixture-of-Experts Language Model
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## An Overview of the Paper

```mermaid
---
title: DeepSeek-V2 Overview
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
graph TD
    subgraph "DeepSeek-V2 Overview"
        A[DeepSeek-V2] --> B{Key Concepts}
        B --> C[Strong Performance]
        B --> D[Economical Training]
        B --> E[Efficient Inference]
        B --> F["Long Context Length (128K)"]
        B --> G["Mixture-of-Experts (MoE)"]
        B --> H["Parameter Efficiency (21B/236B)"]
        B --> I["Pre-training Corpus (8.1T tokens)"]
        B --> J["Supervised Fine-Tuning (SFT) & Reinforcement Learning (RL)"]
    end
    
    subgraph "Architecture Details"
        K[Architecture] --> L["Multi-Head Latent Attention (MLA)"]
        L --> M{Low-Rank Key-Value Compression}
        L --> N[Reduced KV Cache]
        L --> O[Improved Inference Efficiency]
        
        K --> P[DeepSeekMoE]
        P --> Q{Expert Segmentation & Specialization}
        P --> R{Shared Expert Isolation}
        P --> S[Economical Training Costs]
        
        L --> T["Decoupled Rotary Position Embedding (RoPE)"]
        T --> U[Reduced Activation Memory]
        T --> V[Maintaining Inference Efficiency]
        
    end
    
    subgraph "Pre-training & Evaluation"
        W[Pre-training] --> X[Data Construction]
        X --> Y[High-quality, Multi-source Corpus]
        X --> Z[Emphasis on Chinese Data]
        
        W --> AA[Hyperparameter Settings]
        AA --> AB[Transformer Layers, Hidden Dimension, etc.]
        AA --> AC["Optimizer (AdamW), Learning Rates"]

        W --> AD[Infrastructure]
        AD --> AE["Hardware (NVIDIA H800 GPUs)"]
        AD --> AF["Parallelism (Pipeline, Expert, Data)"]
        
        W --> AG["Long Context Extension (YaRN)"]
        AG --> AH[Support for 128K Context]

        W --> AI[Evaluations]
        AI --> AJ["Benchmarks (MMLU, BBH, etc.)"]
        AI --> AK[English & Chinese Benchmarks]
        AI --> AL[Perplexity & Generation Based Metrics]

    end

    subgraph "Alignment & Optimization"
        AM[Alignment] --> AN["Supervised Fine-tuning (SFT)"]
        AN --> AO["onversational Data (1.5M instances)"]
        AN --> AP[Improved Instruction Following & Safety]
        
        AM --> AQ["Reinforcement Learning (RL)"]
        AQ --> AR["Group Relative Policy Optimization (GRPO)"]
        AQ --> AS["Multi-reward Framework (Helpful, Safety, Rule-based)"]

        AM --> AT[Training Efficiency Optimizations]
        AT --> AU[Hybrid Engine, vLLM, Scheduling Strategy]
    end

    subgraph "Evaluation Summary"
        AV[Evaluation Results] --> AW[Strong Performance Across Benchmarks]
        AW --> AX["Competitive Performance vs. Other Models"]
        AW --> AY["DeepSeek-V2 Chat (SFT) & DeepSeek-V2 Chat (RL)"]
        AW --> AZ[Strongest Open-source MoE Model]
    
    end
    

    subgraph "Limitations & Future Work"
        BA[Limitations] --> BB[Lack of Continual Learning]
        BA --> BC[Potential for Hallucinations & Inaccuracies]
        BA --> BD["Language Limitations (Chinese & English)"]
    
        BE[Future Work] --> BF[Scaling up MoE Models]
        BE --> BG[GPT-4 Level Performance]
        BE --> BH["Enhanced Model Alignment (Values)"]
        BE --> BI[Support for Multiple Modalities]
    end

```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---