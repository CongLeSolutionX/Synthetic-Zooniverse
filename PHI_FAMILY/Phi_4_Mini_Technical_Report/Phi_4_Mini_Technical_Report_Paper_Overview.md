---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://huggingface.co/microsoft/Phi-4-multimodal-instruct/blob/main/phi_4_mm.tech_report.02252025.pdf"
---



# Phi-4-Mini Technical Report - Compact yet Powerful Multimodal Language Models via Mixture-of-LoRAs
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Phi-4-Mini Technical Report - Paper Overview



```mermaid
---
title: "Phi-4-Mini Technical Report - Compact yet Powerful Multimodal Language Models via Mixture-of-LoRAs"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false, 'curve': 'linear' },
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
    subgraph Phi_4_Mini_Overview["Phi-4-Mini Overview"]
        A[Phi-4-Mini] --> B(Language Model)
        B --> B1(Transformer Architecture)
        B1 --> B2(32 Layers)
        B2 --> B3(Hidden State Size: 3072)
        B1 --> B4(Tied Input/Output Embeddings)
        B1 --> B5(200,064 Vocabulary Size)
        B1 --> B6(128K Context Length)
        B1 --> B7(LongRoPE)
        B1 --> B8("Group Query Attention<br>(GQA)")
        B1 --> B9(RoPE Configuration - Fractional Dimension)
    end

    subgraph Training_Details["Training Details"]
        C[Training] --> D(Pre-training Data)
        D --> D1(High-Quality Web Data)
        D --> D2(Synthetic Data - Emphasis on Math/Coding)
        D --> D3(Improved Data Filtering)
        D --> D4(Enhanced Math/Coding Data)
        D --> D5(Phi-4 Synthetic Data)
        D --> D6(Better Data Mixture - Reasoning Data Increased)
        C --> E(Post-training Data)
        E --> E1(Function Calling/Summarization Data)
        E --> E2(Instruction Following Data)
        E --> E3(Code Completion Data)
        C --> F(Reasoning Training)
        F --> F1(Pre-training on Reasoning CoT Tokens)
        F --> F2(Rejection Sampling for Incorrect Outputs)
        F --> F3(Fine-tuning on Curated CoT Samples)
        F --> F4(DPO Data Creation - Preferred/Dispreferred Output)
    end

    subgraph Key_Capabilities["Key Capabilities"]
        G[Capabilities] --> H(Strong Language Performance)
        H --> H1(Natural Language Understanding)
        H --> H2(Natural Language Generation)
        H --> H3(Complex Reasoning)
        H --> H4(Math Capabilities)
        H --> H5(Coding Capabilities)
        G --> I(Instruction Following)
        I --> I1(Function Calling)
        I --> I2(Code Generation/Synthesis)
        G --> J(Multilingual Support)
        J --> J1(200,064 Vocabulary Size)
        G --> K(Robustness to harmful content)
        K --> K1(Safe Alignment Methods)
        K --> K2(Red Teaming)
        K --> K3(Automated Safety Evaluations)
    end

    style B fill:#ccf3,stroke:#333,stroke-width:1px
    style C fill:#ccf3,stroke:#333,stroke-width:1px
    style D fill:#ccf3,stroke:#333,stroke-width:1px
    style E fill:#ccf3,stroke:#333,stroke-width:1px
    style F fill:#ccf3,stroke:#333,stroke-width:1px
    style G fill:#ccf3,stroke:#333,stroke-width:1px
    
```


----


**Explanation:**

This Mermaid graph provides a more focused and detailed visualization of Phi-4-Mini, incorporating the training data and key capabilities mentioned in the original text.

*   **Subgraphs:**  Logical grouping of related information (Overview, Training, Key Capabilities).
*   **Relationships:** Clear arrows show how different components and training stages relate to each other.
*   **Specificity:**  More detailed nodes (e.g., "Hidden State Size: 3072," "128K Context Length") convey the key architectural choices of Phi-4-Mini.
*   **Training Details:** Explicitly shows the importance of curated synthetic data, particularly for math/coding, and the multi-stage approach to reasoning training.
*   **Key Capabilities:**  Highlights the model's core strengths, including strong language performance, instruction following, coding, multilingual support, and safety alignment efforts.

**Further Refinements:**

To enhance this diagram even further, you could:

*   **Quantify Data:** Add size estimates for the different training datasets (e.g., "5 trillion pre-training data corpus").
*   **Benchmark Scores:**  Include benchmark scores for Phi-4-Mini on relevant tasks (e.g., "Strong performance on MMLU").
*   **Specific Techniques:** Specify details like the type of synthetic data generated, specific filtering methods, or exact types of post-training data.
*   **Visual Cues:** Use different colors or shapes for different types of data or model components (e.g., synthetic data in a different shade, different shapes for different stages of training).



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---