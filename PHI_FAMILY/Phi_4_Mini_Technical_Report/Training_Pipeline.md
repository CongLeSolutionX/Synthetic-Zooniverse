---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://huggingface.co/microsoft/Phi-4-multimodal-instruct/blob/main/phi_4_mm.tech_report.02252025.pdf"
---


# Training Pipeline
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## Training Pipeline - A Diagrammatic Guide

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
    subgraph Training_Pipeline["Training Pipeline"]
        A[Training Process] --> B{Language Model Training}
        B --> B1[Pre-training]
        B1 --> B1a[Web Data]
        B1 --> B1b[Synthetic Data]
        B1 --> B1c[Curated Math & Code Data]
        B1 --> B1d[Reasoning-Rich Text Data]
        B1 --> B1e[Improved Quality Filtering]
        B1 --> B1f["Data Mixture Tuning (Increased Reasoning Ratio)"]
        B --> B2[Post-training]
        B2 --> B2a[Function Calling & Summarization Data]
        B2 --> B2b[Instruction Following Data]
        B2 --> B2c[Code Completion Data]
        B --> C{Vision Modality Training}
        C --> C1[Projector Alignment]
        C1 --> C1a[Caption Data]
        C --> C2[Joint Vision Training]
        C2 --> C2a[Vision Pre-training Data]
        C --> C3[Generative Vision-Language Training]
        C3 --> C3a[Curated Single-Frame SFT Data]
        C --> C4[Multi-Frame Training]
        C4 --> C4a[Multi-frame SFT Data]
        B --> D{Speech/Audio Modality Training}
        D --> D1[Pre-training]
        D1 --> D1a[ASR Data]
        D1 --> D1b[Anonymized Speech-Text Pairs]
        D --> D2[Post-training]
        D2 --> D2a["100M Curated Speech/Audio SFT Data (Weighted)"]
        D2 --> D2b[Various Speech/Audio Tasks]
        D2 --> D2c[ASR, AST, SQA, SQQA, SSUM, AU]
        D --> D3[Vision-Speech Joint Training]
        D3 --> D3a[Vision-Speech SFT Data]
        D3 --> D3b[Language & Vision Post-training Data]
        
        B --> E[Reasoning Training]
        E --> E1[Pre-training on 60B Reasoning CoT Tokens]
        E --> E2[Rejection Sampling]
        E --> E3[Fine-tuning on 200K Curated CoT Samples]
        E --> E4[DPO Training on 300K Preference Samples]  
    end
    
```

---


### Explanation and Improvements over Previous Version

* **Explicit Data Sources:**  This version now explicitly shows the types of data used for each training stage. For example, "B1a[Web Data]," "B1b[Synthetic Data]," and "B1c[Curated Math & Code Data]" make it clear where the training data originates. This is a significant improvement for clarity.
* **Modality-Specific Stages:**  Training stages for vision and speech/audio are clearly delineated and linked to their respective pre-training, post-training, and joint training phases.  This improved structure makes the complex multimodal training pipeline more understandable.
* **Reasoning Training Stage:**  A dedicated stage for reasoning training, reflecting the specific pre-training, fine-tuning, and preference labeling processes.
* **Data Filtering and Tuning:**  Explicit nodes (B1e, B1f) highlight the crucial steps of data filtering and mixture tuning, which are crucial parts of the training process.
* **Weighted Data:**  Clarifies that speech/audio post-training uses weighted data.
* **Context Length:**  While not directly shown in the pipeline, consideration for the context length of different tasks (e.g., 64k for multi-image) could be added as annotations.

----

### Further Refinements (Not in the Diagram, But Crucial)

* **Dataset Sizes:**  Add annotations to specify the approximate sizes of the training datasets (e.g., "B1a [Web Data (trillions of tokens)]").
* **Parameter Counts:**  Add annotations to note the parameter counts of different models (e.g., Phi-4-Mini).
* **Specific Techniques:**  Consider adding annotations for specific techniques like "Rejection Sampling" (E2) or "weighted data" within the appropriate nodes.
* **Language Support:**  Include details about the number of supported languages within the respective nodes for language data.


This refined flowchart provides a more accurate and comprehensive visualization of the training pipeline.  It is now a more detailed and informative representation of the model training process described in the technical report. Remember to supplement this diagram with tables, charts, or other visual aids to present the evaluation results for a complete picture of the training process.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---