---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2412.08905"
---


# Post-Training Details
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## Post-Training Details - A Diagrammatic Guide


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
    subgraph PostTraining_Details["Post-Training Details"]
        E("Post-Training Refinement")
        E --> EE["Hallucination Mitigation"]
        EE --> EEE["SFT Data<br>(Refusal/Correct Answer Pairs)"]
    
        EEE --> EEEE1["Generating Bogus Questions<br>(GPT-4o)"]
        EEE --> EEEE2["Generating Refusals<br>(GPT-4o)"]
        EEE --> EEEE3["Answer Checking<br>(GPT-4o)"]

        EE --> EEEE["DPO Data<br>(Pivotal Tokens/Judge Guided)"]
    
        EEEE --> EEEEE1["Pivotal Token Search (PTS) - Data Generation"]
        EEEE1 --> EEEEEE1["Identifying Pivotal Tokens in Math/QA/Coding"]
        EEEE1 --> EEEEEE2["Generating Preference Data<br>(DPO Pairs)"]
    
        EEEE --> EEEEE2["Judge-Guided DPO - Data Generation"]
        EEEEEE2 --> EEEEEE3["GPT-4o Evaluation of Model Responses"]
        EEEEEE2 --> EEEEEE4["Rating Responses<br>(Accuracy, Style, Detail)"]
        EEEEEE2 --> EEEEEE5["Generating Desired/Undesired Output Pairs"]
            
        EE --> EEEEEE["Safety & Responsible AI Data"]

        EE --> EFFFF["Post-Training Ablation<br>(Table 9)"]
        EFFFF --> EFFFFF1["Evaluation of DPO Stage 1 Impact"]
        EFFFF --> EFFFFF2["Evaluation of DPO Stage 2 (Judge Guided) Impact"]
        EFFFF --> EFFFFF3["Combined DPO Impact"]

        EE --> EGGGG["Figure 6<br>(SimpleQA Performance Evolution)"]
        
    end

```

---

### Explanation of Changes and Additions

*   **More Detailed Data Generation Processes:** The original subgraph was too general.  This version breaks down the data generation for SFT and DPO into more specific processes, reflecting the different types of prompts used for each task (e.g., generating bogus questions, generating refusals, answer checking).
*   **Explicit Connections to GPT-4o's Role:** The diagram clarifies that GPT-4o plays a crucial role in generating and evaluating the post-training data.  This is highlighted with specific nodes like `EEEE1`, `EEEE2`, `EEEE3`, and `EEEEEE2`.
*   **Emphasis on Data Types:** Explicitly shows that safety and Responsible AI (RAI) data are part of the post-training process under the `EE` and `EEEE` nodes. This aligns with the report's focus on safety-related data for DPO and SFT.
*   **Clearer Representation of Ablation Studies:** The `Post-Training Ablation` node now directly connects to the specific evaluation of different post-training strategies, which helps organize the key findings from the ablation studies.
*   **Visual Link to Figure 6:**  The inclusion of `Figure 6` explicitly connects the diagram to the visual representation of SimpleQA performance evolution during post-training, providing a visual aid to understand the concept.

This revised subgraph provides a more detailed and accurate representation of the post-training process, better reflecting the intricacies described in the original text. Note that this diagram is still simplified to fit the diagram structure, and some details (such as exact prompts and grading criteria) are omitted for better readability.  Specifics can be expanded upon if needed.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---