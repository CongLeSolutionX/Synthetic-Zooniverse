---
created: 2025-03-02 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf"
---



# Safety Evaluation Details
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Safety Evaluation Details - A Diagrammatic Guide 


```mermaid
---
title: "OpenAI GPT-4.5 System Card"
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
    subgraph Safety_Evaluation_Details["Safety Evaluation Details"]
        I[Safety Evaluations] --> J(Disallowed Content)
        J --> J1(Harmful Content)
        J1 --> J1a[Hate Speech]
        J1 --> J1b[Illicit Advice]
        J1 --> J1c[Sexual Content]
        J1 --> J1d[Sexual Content Involving Minors]
        J1 --> J1e[Self-Harm]

        J --> J2(Jailbreak Robustness)
        J2 --> J2a[Adversarial Prompts]
        J2 --> J2b{Human Sourced Jailbreaks}
        J2 --> J2c{StrongReject}
        J2c -- "goodness@0.1" --> J2c_result

        J --> J3(Hallucinations)
        J3 --> J3a{PersonQA}
        J3a --> J3a_result[Accuracy/Hallucination Rate]

        J --> J4("Fairness & Bias")
        J4 --> J4a{BBQ Evaluation}
        J4a --> J4a_ambiguous[Ambiguous Questions]
        J4a --> J4a_unambiguous[Unambiguous Questions]

        J4a_ambiguous -- accuracy --> J4a_ambiguous_accuracy
        J4a_unambiguous -- accuracy --> J4a_unambiguous_accuracy
        J4a_ambiguous -- P(not-stereotype | not unknown) --> J4a_p_not_stereotype

        J --> J5(Instruction Hierarchy)
        J5 --> J5a{System <> User message conflict}
        J5a --> J5a_result[Accuracy]
    
        J5 --> J5b{Tutor Jailbreaks}
        J5b --> J5b_result[Accuracy]

        J5 --> J5c{Phrase and Password Protection}
        J5c --> J5c_result[Accuracy]

        J --> J6(Red Teaming)
        J6 --> J6a{"Challenging Red Teaming Evaluation 1<br>(o3-mini)"}
        J6a --> J6a_result[not_unsafe]

        J6 --> J6b{"Challenging Red Teaming Evaluation 2<br>(deep research)"}
        J6b --> J6b_result[not_unsafe]

        J --> J7(Apollo Research)
        J7 --> J7a[Scheming Reasoning]
        J7 --> J7b[In-Context Alignment Faking]
        J7 --> J7c[Sandbagging]
        J7 --> J7d[Self-Exfiltration]

        J --> J8(METR)
        J8 --> J8a[Model Performance on Tasks]
        J8a --> J8a_result[Time Horizon Score]

        J --> J9(Multilingual Evaluation)
        J9 --> J9a[MMLU Dataset]
        J9a --> J9a_result[Accuracy by Language]

        J --> J10(Preparedness Framework)
        J10 --> J10a[Overall Risk Rating]
        J10a --> J10a_result[Medium/Low Risk by Category]

        J1 --> J_summary[Summary of Safety Evaluation Results]
        J2 --> J_summary[Summary of Safety Evaluation Results]
        J3 --> J_summary[Summary of Safety Evaluation Results]
        J4 --> J_summary[Summary of Safety Evaluation Results]
        J5 --> J_summary[Summary of Safety Evaluation Results]
        J6 --> J_summary[Summary of Safety Evaluation Results]
        J7 --> J_summary[Summary of Safety Evaluation Results]
        J8 --> J_summary[Summary of Safety Evaluation Results]
        J9 --> J_summary[Summary of Safety Evaluation Results]
        J10 --> J_summary[Summary of Safety Evaluation Results]

    end
    
```


---


### Explanation

This subgraph, "Safety Evaluation Details," is a more comprehensive and detailed representation of the safety evaluation aspects of GPT-4.5.

* **Nodes:** Each node represents a specific evaluation type or dataset (e.g., "Disallowed Content," "Jailbreak Robustness").
* **Sub-nodes:**  Sub-nodes break down the broader evaluation categories into their specific components (e.g., "Hate Speech," "Illicit Advice").
* **Results:**  Key results from the tables (e.g., accuracy scores, hallucination rates) are represented by nodes like "J3a_result" and are linked to their parent evaluations.
* **Summary:** The summary node, "J_summary", consolidates the results across all safety evaluations.
* **Clarity and Structure:** The use of subgraphs and detailed connections enhances the clarity of the different evaluation methods and their relationships.
* **Preparedness Framework Integration:**  The node "J10" and its sub-nodes directly represent the risk assessment framework.

---

### Key Improvements

* **Explicit Categories:**  Clearly defines the different categories of safety concerns.
* **Linking to Results:**  Connects each evaluation to the relevant metrics and results (e.g., accuracy, rates).
* **Visual Hierarchy:**  The use of subgraphs and links creates a clear visual hierarchy, making the diagram easier to navigate and understand.
* **Readability:**  The diagram is more organized and readable, focusing on clarity and avoiding overwhelming the viewer with excessive detail.

---


### Important Considerations

* **Table Data Integration:** Replace placeholders like "J3a_result" with specific values from the original tables, as well as any confidence intervals reported.
* **Confidence Intervals:** Include the 95% confidence intervals for the results in the nodes. This reflects the inherent variability in the evaluation results.

This diagram provides a more structured and comprehensive view of the safety evaluation results for GPT-4.5, ready for detailed analysis. Remember to replace the placeholder values with the actual data from the original tables.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---