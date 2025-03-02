---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://huggingface.co/microsoft/Phi-4-multimodal-instruct/blob/main/phi_4_mm.tech_report.02252025.pdf"
---


# Data Details
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## Data Details - A Diagrammatic Guide


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
    subgraph Language_Data["Language Data"]
        A[Language] --> A1(Web Data)
        A1 --> A1a(High-Quality Web Text)
        A --> A2(Synthetic Data)
        A2 --> A2a(Phi-4 Synthetic Data)
        A2 --> A2b(Curated Math & Coding Data)
        A2 --> A2c(Reasoning CoT Data)
        A --> A3(Post-training Data)
        A3 --> A3a(Function Calling & Summarization Data)
        A3 --> A3b(Instruction Following Data)
        A3 --> A3c(Code Completion Data)

        A2c -- Data Generation --> A2c1(Frontier Reasoning LLMs)
        A2c -- Data Filtering --> A2c2(Rejection Sampling, Incorrect Output Filtering, DPO Data)
    end
    
    subgraph Vision_Language_Data["Vision-Language Data"]
        B[Vision-Language] --> B1(Image-Text Documents)
        B --> B2(Image-Text Pairs)
        B --> B3(Image Grounding Data)
        B --> B4(Synthetic OCR of PDFs)
        B --> B5(Synthetic Datasets for Chart Comprehension)

        B1 --> B1a(Interleaved Image-Text)
        B2 --> B2a(Pairs with Diverse Domains)
        B3 --> B3a(Alignment of Images and Descriptions)
        B4 --> B4a(Extraction from Diverse Sources)
        B5 --> B5a(Data for Chart Analysis)


        B -- Data Size --> B6(0.5T Tokens)
        B -- Max Image Resolution --> B7(1344x1344)
        B -- Supervised Fine-tuning --> B8(Text SFT, Public Multimodal, Internal Multimodal)
        B8 --> B8a(General Image Understanding)
        B8 --> B8b(Chart, Table, Diagram Comprehension)
        B8 --> B8c(PowerPoint Analysis)
        B8 --> B8d(OCR)
        B8 --> B8e(Multi-Image Comparison)
        B8 --> B8f(Video Summarization)
        B8 --> B8g(Model Safety)

        B -- Data Size --> B9(0.3T Tokens)
        
    end
    
    subgraph Vision_Speech_Data["Vision-Speech Data"]
        C[Vision-Speech] --> C1(Synthetic Data)
        C1 --> C1a(Single-Frame & Multi-Frame Scenarios)
        C1 --> C1b(Conversion from Text to Audio via Internal TTS)
        C1 --> C1c(Filtering by WER)
    end
    
    subgraph Speech_Audio_Data["Speech/Audio Data"]
        D[Speech/Audio] --> D1(Pre-training Data)
        D1 --> D1a(ASR Transcriptions)
        D1 --> D1b(Alignment with Text Modality)
        D1 --> D1c(Anonymized in-house Speech-Text Pairs)

        D --> D2(Post-training Data)
        D2 --> D2a(SFT Data for Speech Tasks)
        D2 --> D2b(Real & Synthetic Speech Data)
        D2 --> D2c(ASR, AST, SQA, SQQA, SSUM, AU)

        D2c --> D2c1("ASR Training Data (20k hours)")
        D2c --> D2c2("ASR, AST, SQA, SQQA, SSUM, AU")
        D2c1 --> D2c1a("Multilingual Coverage (8 languages)")
        D2c --> D2c3(ASR + Translation CoT)
        D2c --> D2c4(Speech-Transcript Pairs, Synthetic QA Pairs)
        D2c --> D2c5(Audio Queries, Internal Zero-Shot TTS, ASR Transcripts)
        D2c --> D2c6(Summarization Queries, GPT-4 Generated Summaries)
        D2c --> D2c7(Audio, Question, Answer Tuples, Public Dataset)
        D2c --> D2c8(Audio Safety Data)
        D2c --> D2c9(Azure PII Detection)
    end

    style A fill:#ccf3,stroke:#333,stroke-width:1px
    style B fill:#ccf3,stroke:#333,stroke-width:1px
    style C fill:#ccf3,stroke:#333,stroke-width:1px
    style D fill:#ccf3,stroke:#333,stroke-width:1px
    
```

----

### Explanation of Improvements and Data Detailing

* **Clearer Categorization:** The subgraphs now more accurately reflect the categories of data.  Instead of just "Data," we now have subgraphs for "Language Data," "Vision-Language Data," "Vision-Speech Data," and "Speech/Audio Data."
* **Data Source Specificity:**  The arrows now lead to more specific data sources (e.g., "High-Quality Web Text," "Curated Math & Coding Data," "Rejection Sampling").  This makes the data sources more concrete.
* **Data Characteristics:**  Added details about data characteristics (e.g., data size in tokens, maximum image resolution, and multilingual coverage).
* **Explicit Data Relationships:** The arrows show *how* the data is generated (e.g., reasoning CoT data is generated by frontier models).
* **Safety Considerations:** The data used for safety alignment is also categorized and shows how these are connected to the main model training.
* **Emphasis on Synthesis:**  The diagram now more prominently displays how synthetic data plays a crucial role in training, especially for reasoning and coding tasks.
* **Data Preprocessing:**  The role of data filtering, rejection sampling, and PII detection is more apparent.


This revised diagram provides a much more detailed and accurate representation of the data utilized in training Phi-4-Mini and Phi-4-Multimodal. Remember that this diagram is a simplification; real-world datasets often have more complex structures and relationships.  You can further enhance the diagram with specific dataset names and sizes for each component.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---