---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://techcommunity.microsoft.com/blog/educatordeveloperblog/welcome-to-the-new-phi-4-models---microsoft-phi-4-mini--phi-4-multimodal/4386037"
---




# The New Phi-4 Models
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## The New Phi-4 Models - A Diagrammatic Guide - Simple Version




```mermaid
---
title: "Microsoft Tech Community - The Content on the Webpage"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
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
graph TD
    A[Microsoft Phi-4 Models] --> B{Phi-4-mini}
    B -- Multilingual Support --> C[Multilingual Processing]
    B -- Reasoning --> D[Reasoning and Problem Solving]
    B -- Function Calling --> E[External Data Integration]
    B -- Optimized for Edge --> F[Edge Device Deployment]

    A --> G{Phi-4-multimodal}
    G -- Multimodal Inputs --> H[Text, Vision, Audio]
    G -- Advanced Reasoning --> I[Image-to-Code Generation]
    G -- Optimized for Edge --> F

    subgraph Deployment
        F -- Hugging Face --> K[Hugging Face]
        F -- Azure --> L[Azure]
        F -- GitHub --> M[GitHub]
        F -- Ollama --> N[Ollama]
    end
    
    A --> O[Resources]
    O -- Phi Cookbook --> P[Documentation and Examples]
    O -- Technical Reports --> Q[Detailed Technical Analysis]
    
```

---


This example uses a simplified approach, focusing on the key features of each model.  A more detailed diagram would include specific examples (e.g., code generation from images) as nodes and elaborate on the technical aspects like quantized model deployment.  Furthermore, the diagram could incorporate information about the models' performance comparisons to other LLMs.


-----

## The New Phi-4 Models - A Diagrammatic Guide


```mermaid
---
title: "Microsoft Tech Community - The Content on the Webpage"
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
    subgraph Phi4_Models["Phi4 Models"]
        A["Microsoft Phi-4 Models"] --> B("Phi-4-mini")
        B -- Multilingual Support --> C["Multilingual Processing"]
        B -- Reasoning --> D["Reasoning & Problem Solving"]
        B -- Function Calling --> E["External Data Integration"]
        B -- Edge Optimized --> F["Edge Deployment<br>(Mobile, IoT)"]
        
        A --> G("Phi-4-multimodal")
        G -- Multimodal Inputs --> H["Text, Vision, Audio"]
        G -- Advanced Reasoning --> I["Image-to-Code Generation"]
        G -- Audio Functions --> J["Audio Processing<br>(Translation, Interaction)"]
        G -- Edge Optimized --> F
        
        F --> K["Edge Device Platforms"]
        K -- iPhone --> L["iOS"]
        K -- Android --> M["Android"]
        K -- Windows --> N["Windows"]
        K -- IoT --> O["IoT Devices"]
    end
    
    subgraph Model_Deployment["Model Deployment"]
        F --> P["Model Quantization"]
        P --> Q["Microsoft Olive"]
        P --> R["ONNX Runtime"]
    end
    
    subgraph Model_Availability["Model Availability"]
        A --> S["Model Availability"]
        S -- Hugging Face --> T["Hugging Face"]
        S -- Azure AI Foundry --> U["Azure"]
        S -- GitHub Models --> V["GitHub Marketplace"]
        S -- Ollama --> W["Ollama"]
    end

    subgraph Resources["Resources"]
        A --> X["Resources"]
        X -- Phi Cookbook --> Y["Documentation & Examples"]
        X -- Technical Reports --> Z["Technical Analysis"]
    end
    
    style A fill:#ccf3,stroke:#333,stroke-width:2px
    style B fill:#ccf3,stroke:#333,stroke-width:1px
    style G fill:#ccf3,stroke:#333,stroke-width:1px
    
    classDef edge fill:#e33,stroke:#33,stroke-width:0.5px
    class K,S,X edge
    
```

---


### Explanation of Diagram

This Mermaid code generates a more structured and visually appealing diagram illustrating the key features and relationships described in the previous response.

*   **Subgraphs:** The diagram uses subgraphs to group related concepts, making it easier to understand the overall structure.
*   **Nodes:** Each node represents a key concept (e.g., Phi-4-mini, Multilingual Processing, External Data Integration, etc.).
*   **Edges:** Edges (arrows) depict the relationships between concepts, highlighting how features relate to the models and their deployment.
*   **Coloring:**  Consistent colors for model types and resource categories aid in visual clarity.
*   **Focus on Deployment:** The diagram emphasizes the edge-optimized deployment aspects by connecting the models to specific device platforms and tools like Microsoft Olive and ONNX Runtime.
*   **Accessibility:** The diagram shows where to access the models through various platforms like Hugging Face, Azure, GitHub, and Ollama.


This diagram effectively visualizes the relationships between the different elements of Microsoft Phi-4 models, emphasizing their core features, deployment targets, and associated resources.  It's designed to be easily understood and readily convey the essential information from the text.  Further refinement might include adding more specific details or examples as nodes. Remember to replace placeholder URLs with actual URLs.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---