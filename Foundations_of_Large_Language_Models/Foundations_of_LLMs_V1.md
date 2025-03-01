---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---



# Foundations of Large Language Models
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
title: Foundations of Large Language Models
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
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    subgraph Foundations_of_LLMs["Foundations of Large Language Models"]
        A[Introduction] --> B(Pre-training)
        A --> Z[Key Concepts & Definitions]
        Z --> Z1[Tokenization]
        Z --> Z2[Embeddings]
        Z --> Z3[Attention Mechanism]
        Z --> Z4[Transformer Architecture]
        Z --> Z5[Generative vs. Discriminative Models]
        Z --> Z6[Parameters vs. Hyperparameters]
        Z --> Z7["Loss Functions<br>(e.g., Cross-Entropy)"]
        Z --> Z8["Evaluation Metrics<br>(e.g., Perplexity, BLEU, ROUGE)"]

        B --> B1[Unsupervised Pre-training];
        B1 --> B11["Masked Language Modeling (MLM) - BERT-style"]
        B1 --> B12["Causal Language Modeling (CLM) - GPT-style"]
        B1 --> B13["Next Sentence Prediction (NSP) - BERT"]
        B1 --> B14["Permutation Language Modeling (PLM) - XLNet"]
        B1 --> B15[Contrastive Learning]

        B --> B2[Supervised Pre-training]
        B2 --> B21["Task-Specific Pre-training<br>(e.g., on labeled datasets)"]
        B2 --> B22[Multi-Task Learning]

        B --> B3[Self-Supervised Pre-training]
        B3 --> B31[Definition: Learning from unlabeled data using inherent structure]
        B3 --> B32[Examples:<br>MLM, CLM are forms of self-supervision]

        B --> B4[Adapting Pre-trained Models]
        B4 --> B41[Fine-tuning]
        B41 --> B411["Full Fine-tuning<br>(all parameters updated)"]
        B41 --> B412["Parameter-Efficient Fine-tuning<br>(PEFT)"]
        B412 --> B4121[Adapters]
        B412 --> B4122["LoRA<br>(Low-Rank Adaptation)"]
        B412 --> B4123[Prefix Tuning]
        B412 --> B4124[Prompt Tuning]
        B412 --> B4125["(IA)³<br>(Infused Adapter by Inhibiting and Amplifying Inner Activations)"]

        B4 --> B42[Prompting]
        B42 --> B421[Zero-Shot Prompting]
        B42 --> B422[Few-Shot Prompting]
        B42 --> B423["Chain-of-Thought (CoT) Prompting"]
        B42 --> B424["Tree-of-Thoughts (ToT) Prompting"]
        B42 --> B425["Retrieval-Augmented Generation<br>(RAG)"]

        B --> C(Generative Models)
        C --> C1["LLMs (Large Language Models)"]
        C1 --> C11[Examples: GPT-3/4, LLaMA, PaLM, Claude]

        C --> C2[Training at Scale]
        C2 --> C21[Data Parallelism]
        C2 --> C22[Tensor Parallelism]
        C2 --> C23[Pipeline Parallelism]
        C2 --> C24["ZeRO<br>(Zero Redundancy Optimizer)"]
        C2 --> C25["Mixed Precision Training<br>(FP16, BF16)"]

        C --> C3[Long Sequence Modeling]
        C3 --> C31[Attention Mechanisms for Long Sequences]
        C31 --> C311[Sparse Attention]
        C31 --> C312[Linear Attention]
        C31 --> C313[Sliding Window Attention]
        C3 --> C32["Recurrent Models<br>(for comparison, not typically used in LLMs)"]

        C --> C4[Fine-tuning LLMs]
        C4 --> C41[See B41 - Fine-tuning Subtree]

        C --> C5[Aligning LLMs with the World]
        C5 --> C51[Instruction Alignment]
        C51 --> C511["Supervised Fine-tuning<br>(SFT)"]
        C511 --> C5111[Instruction Tuning Methods]
        C5111 --> C51111["FLAN<br>(Finetuned Language Net)"]
        C5111 --> C51112["T0<br>(Cross-Task Generalization via Natural Language Instruction Tuning)"]

        C5 --> C52[Human Preference Alignment]
        C52 --> C521["RLHF (Reinforcement Learning from Human Feedback)"]
        C521 --> C5211[Reward Model Training]
        C5211 --> C52111[Collecting Human Preference Data]
        C5211 --> C52112["Training a Reward Model<br>(RM)"]
        C521 --> C5212[Policy Training]
        C5212 --> C52121["PPO (Proximal Policy Optimization)"]
        C5212 --> C52122["Other RL Algorithms<br>(e.g., A2C, TRPO)"]
        C52 --> C522["Direct Preference Optimization<br>(DPO)"]
        C52 --> C523[Constitutional AI]
        C52 --> C524["Kahneman-Tversky Optimization<br>(KTO)"]

        %% // Duplicate, can be merged with C5
        B --> E(Alignment)
        %%// See C51
        E --> E1[Instruction Alignment]
        %% // See C52
        E --> E2[Human Preference Alignment]

        C --> F(Prompting)
        F --> F1[Prompt Design]
        F1 --> F11[Best Practices for Prompt Engineering]
        F1 --> F12[Prompt Templates]

        F --> F2[In-Context Learning]
        F2 --> F21[Zero-Shot Learning]
        F2 --> F22[Few-Shot Learning]

        F --> F3[Advanced Prompting Methods]
        F3 --> F31["Chain-of-Thought (CoT)"]
        F3 --> F32[Self-Consistency]
        F3 --> F33["Tree of Thoughts (ToT)"]
        F3 --> F34["ReAct (Reasoning and Acting)"]

        F --> F4[Learning to Prompt]
        F4 --> F41[Meta-Learning for Prompting]

        F --> F5[RAG and Tool Use]
        F5 --> F51["Retrieval-Augmented Generation<br>(RAG)"]
        F5 --> F52[Toolformer]
        F5 --> F53[API Calls]

        F --> F6[Prompt Optimization]
        F6 --> F61[Automated Prompt Engineering]

        F --> F7[Soft Prompts]
        F7 --> F71[Continuous Prompt Tuning]

        F --> F8[Prompt Length Reduction]
        F8 --> F81[Techniques for Concise Prompts]
        
        C --> G[Evaluation and Benchmarking]
        G --> G1[Intrinsic Evaluation]
          G1 --> G11[Perplexity]
          G1 --> G12[Next Token Prediction Accuracy]
        G --> G2[Extrinsic Evaluation]
          G2 --> G21["Task-Specific Benchmarks<br>(e.g., GLUE, SuperGLUE)"]
          G2 --> G22[Human Evaluation]
        G --> G3[Bias and Fairness Evaluation]
        G --> G4[Robustness and Adversarial Testing]

        C --> H[Challenges and Future Directions]
        H --> H1[Hallucination]
        H --> H2[Bias and Toxicity]
        H --> H3[Interpretability and Explainability]
        H --> H4[Computational Efficiency]
        H --> H5[Multimodality]
        H --> H6[Continual Learning]
        H --> H7[Safety and Security]
        H --> H8[Data Scarcity]
        H --> H9[Generalization]
        H --> H10[Reasoning and Common Sense]
    end

```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---