---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2412.08905"
---


# Phi-4 Technical Report
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## Phi-4 Technical Report Paper Overview - A Diagrammatic Guide


```mermaid
---
title: "Phi-4 Technical Report"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false, 'curve': 'natual' },
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
    subgraph Phi4_Development_Overview["Phi-4 Development Overview"]
        A["Phi-4 Development"] --> B{"Data Quality Focus"}
        B --> C("Synthetic Data Generation")
        B --> D("Organic Data Curation")
        B --> E("Post-Training Refinement")
        C --> F["Multi-Agent Prompting"]
        C --> G["Self-Revision"]
        C --> H["Instruction Reversal"]
        C --> I["Question Generation<br>(Plurality)"]
        C --> J["Question-Answer Extraction"]
        D --> K["Targeted Acquisition"]
        D --> L["Web Data Filtering"]
        D --> M["Multilingual Data"]
        D --> N["Custom Extraction and Cleaning"]
        E --> O["Supervised Fine-Tuning<br>(SFT)"]
        E --> P["Direct Preference Optimization<br>(DPO)"]
        E --> Q["Pivotal Token Search<br>(PTS)"]
        
        E -- "Judge-Guided DPO" --> R["GPT-4o Evaluation"]
    
        B --> S("Model Architecture and Training")
        S --> T["Decoder-only Transformer<br>(14B params)"]
        S --> U["Context Length Increase<br>(4K -> 16K)"]
        S --> V["Training Data Mixture<br>(Allocation)"]
        S --> W["Hyperparameters<br>(Learning Rate, Batch Size)"]
        S --> X["Training Epochs"]
    
        B --> Y("Benchmarking and Evaluation")
        Y --> Z["Academic Benchmarks<br>(MMLU, GPQA, MATH)"]
        Y --> AA["Internal Benchmark<br>(PhiBench)"]
        Y --> AB["Evaluation Metrics<br>(RMSE, F1-score)"]
        Y --> AC["Comparison to Other Models"]
        
    end
    
    subgraph Data_Sources["Data Sources"]
        C --> CC("Synthetic Data")
        D --> DD("Organic Data")
        
        CC --> CCC("Web Data")
        CC --> CCCC("Code Repositories")
        CC --> CCCCC("Books & Papers")
        CC --> CCCCCC("Question-Answer")
        DD --> DDDD("Web Data")
        DD --> DDDDD("Code")
        DD --> DDDDDD("Books")
        DD --> DDDDDDD("Academic Papers")
        DD --> DDDDDDDD("Q&A Data")
        
    end
    
    subgraph Data_Quality_Mitigation["Data Quality Mitigation"]
        B -- Overfitting --> BB("Data Decontamination")
        BB --> BBB["N-gram Filtering<br>(13-gram, 7-gram)"]
        BB --> BBBB["Benchmark Deduplication"]
        
    end

    subgraph PostTraining_Details["Post-Training Details"]
        E --> EE["Hallucination Mitigation"]
        EE --> EEE["SFT Data<br>(Refusal/Correct Answer Pairs)"]
        EE --> EEEE["DPO Data<br>(Pivotal Tokens/Judge Guided)"]
        
        EE --> EEEEE["SimpleQA Analysis<br>(F1-score vs. Practical Behavior)"]
    
    end

    subgraph Model_Evaluation["Model Evaluation"]
        Y --> ZZZ["Benchmark Performance<br>(Table 1, 10)"]
        Y --> ZZZZ["Table 9<br>(Post-Training Impact on Benchmarks)"]
        Y --> ZZZZZ["Figure 1 (Overfitting Analysis),<br>Figure 2 (Phase 2 Pretraining)"]

    end

    subgraph Training_Details["Training Details"]
        S --> TTT["Table 5<br>(Data Mixture Allocation)"]
        S --> TTTT["Table 2<br>(Pretraining Benchmarks)"]
        S --> TTTTT["Figure 2<br>(Synthetic Data Impact on Benchmarks)"]

    end

```

---


### Explanation

This Mermaid diagram visually represents the key concepts and their relationships in the phi-4 development.  It uses subgraphs for better organization and clarity.  The nodes represent key concepts (e.g., "Synthetic Data Generation," "Model Architecture").  The edges show the relationships between them (e.g., "Synthetic Data Generation" influences "Post-Training Refinement"). The diagram also explicitly links to tables and figures for detailed analysis of specific aspects.  This improved structure is more complex and comprehensive than a simple list and helps highlight the interdependencies and processes in the model's development.  Note that due to the document's extensive detail, some concepts have been combined for better diagram clarity.  For instance, "Web Data Filtering" is a sub-concept of "Organic Data Curation." Remember that specific nodes can be further expanded or connected based on the user's request for more detail.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---