---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---


# Few-shot In-context Learning
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
title: Few-shot In-context Learning
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
    subgraph Few_shot_In_Context_Learning["Few-shot In-context Learning"]
        A[In-Context Learning] --> B(Few-shot Learning)
        B --> C{Key Characteristics}
        C --> CA[No Model Parameter Updates]
        C --> CB[Leveraging Demonstrations]
        C --> CC[Effective for Adapting LLMs]
        
        subgraph Learning_From_Demonstrations["Learning From Demonstrations"]
            B -- Few-shot Examples --> D(Input-Output Pairs)
            D --> DA[Instructions]
            D --> DB[Demonstrations]
            D --> DC[Expected Outputs]
            
            subgraph Demonstration_Types["Demonstration Types"]
                D --> DE(Zero-shot)
                DE -- No Demonstrations --> DE1[Direct Application of LLM]
                D --> DF(One-shot)
                DF -- Single Demonstration --> DF1[Adapting with a single example]
                D --> DG(Few-shot)
                DG -- Multiple Demonstrations --> DG1[Learning from patterns]
            end
        end
        
        subgraph Specific_Application_Examples["Specific Application Examples"]
            B -- Example: Sentiment Analysis --> E(Text Classification)
            E --> EA[Positive, Negative, Neutral]
            E --> EB[Classifying new texts based on demonstrated examples]

            B -- Example: Translation --> F(Language Translation)
            F --> FA[Chinese-English Translation]
            F --> FB[Adapting to new phrases with demonstrated examples]

            B -- Example: Arithmetic Reasoning --> G(Mathematical Reasoning)
            G --> GA[Step-by-step reasoning demonstrations]
            G --> GB[Solving new problems based on demonstrated solutions]

        end
        
        subgraph Limitations["Limitations"]
            B --> H{Potential Limitations}
            H --> HA[Prompt Quality Critical]
            H --> HB[Overreliance on Demonstrations]
            H --> HC[Generalization Challenges]
            H --> HD[Dependence on Pre-training Quality]
            H --> HE[Limited Scope of Demonstrations]
            H --> HF[Limited Number of Demonstrations for Complex Tasks]
        end
    end
    
```


---

### Explanation

*   **Few-shot Learning:**  A central concept.
*   **Key Characteristics:** Highlights the core features: No parameter updates, leveraging demonstrations, and adapting LLMs efﬁciently.
*   **Learning from Demonstrations:**  This subgraph delves into the idea of providing input-output pairs (demonstrations) to guide the LLM. It further breaks down demonstration types (zero-shot, one-shot, few-shot).
*   **Specific Application Examples:** Shows how few-shot in-context learning can be applied to different NLP tasks like sentiment analysis, translation, and mathematical reasoning, illustrating the different types of input-output demonstrations required for each.
*   **Potential Limitations:**  This subgraph acknowledges the potential challenges, such as prompt quality, overreliance on demonstrations, generalization to new scenarios, and the dependence on the quality of the pre-trained LLM.  It also emphasizes that the number and complexity of demonstrations matter when handling complex tasks.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---