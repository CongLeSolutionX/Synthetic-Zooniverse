---
created: 2025-03-05 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://www.biorxiv.org/content/10.1101/2021.10.04.463034v1.full.pdf"
---



# Protein complex prediction with AlphaFold-Multimer
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## AlphaFold-Multimer - A Diagrammatic Guide 



### 1. High-Level Model Overview (Mind Map)

This will provide a bird's-eye view of AlphaFold-Multimer and its components.

```mermaid
---
title: "High-Level Model Overview"
config:
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "mindmap": { "htmlLabels": false },
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
mindmap
  root((AlphaFold-Multimer))
    Inputs
      Amino_Acid_Sequence
      Multiple_Sequence_Alignment(MSA)
      Template_Structures
      Chain_Stoichiometry
      Chain_Relative_Positional_Encoding
    Architecture
      Evoformer
      Pair_Representation
      MSA_Representation
      Template_Stack
    Training
      Training_Dataset(PDB)
        Sampling
        Chain_Clusters
      Multi_Chain_Cropping
        Contiguous_Cropping
        Spatial_Cropping
      Mixed_FAPE_Clamping
      Multi_Chain_Permutation_Alignment
    Outputs
      Predicted_Structure
      Model_Confidence(ipTM, pTM)
      DockQ_Score
      RMSD
    Comparisons
      AlphaFold_Linker
      AlphaFold_Gap(ColabFold)
      ClusPro
      
```

**Explanation:**

*   **Root:** The central node, "AlphaFold-Multimer".
*   **Branches:**  The main categories: Inputs, Architecture, Training, Outputs, Comparisons.
*   **Sub-branches:** More detailed components within each category.
*   **Style:** A mind map is good for outlining relationships in a non-linear way.

---


### 2. Data Flow Diagram (Directed Graph)

This diagram visualizes the flow of data and processes within the AlphaFold-Multimer system.

```mermaid
---
title: "Data Flow Diagram"
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
    A["Amino Acid Sequence(s)"] --> B(MSA Generation)
    B --> C{MSA + Chain Stoichiometry}
    D[Template Structures] --> E{MSA + C}
    G[Chain Relative Positional Encoding] --> E
    E --> F(Evoformer)
    F --> H{Mixed FAPE Clamping}
    H --> I(Multi-Chain Permutation Alignment)
    I --> J[Predicted Structure]
    J --> K{"Scoring (DockQ, ipTM, pTM)"}
    K --> L[Model Evaluation]

    style A fill:#ccf3,stroke:#333,stroke-width:1px
    style D fill:#ccf3,stroke:#333,stroke-width:1px
    style G fill:#ccf3,stroke:#333,stroke-width:1px
    
```

**Explanation:**

*   **Nodes:** Processes or data stores (MSA generation, Evoformer, datasets, etc.).
*   **Edges:** Represent the flow of information between components.
*   **Style:** Directed graph emphasizes the sequence of steps.

----


### 3. Training Process (Flowchart)

Illustrates the key steps in training the AlphaFold-Multimer model.

```mermaid
---
title: "Training Process for the AlphaFold-Multimer Model "
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
flowchart LR
    A["Start Training"] --> B{"Random Crop to 384 Residues"}
    B --> C{"Train on 128 TPUv3 Cores<br>(2 Weeks)"}
    C --> D{"Halve Learning Rate, Double MSA Sequences"}
    D --> E{"Fine-Tune<br>(pLDDT Heads)"}
    E --> F{"Fine-Tune<br>(Violation Losses)"}
    F --> G{"Train 3 Models<br>(Stage 1)"}
    G --> H{"Select Best Model on Validation Set"}
    H --> I{"Fine tune with 5 different random seeds<br>(producing 5 models in total)"}
    I --> J[End Training]
```

**Explanation:**

*   **Nodes:** Steps in the training process.
*   **Edges:**  Flow of execution.
*   **Style:**  Flowchart provides a sequential view of the training procedure.

---


### 4. Model Evaluation (Decision Tree/Flowchart)

Illustrates the steps in model evaluation and selection.

```mermaid
---
title: "Model Evaluation"
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
flowchart LR
    A["Start Evaluation"] --> B{"Predict Structures with 5 Models"}
    B --> C{"Calculate Model Confidence<br>(ipTM + pTM)"}
    C --> D{"Select Model with Highest Confidence"}
    D --> E["Evaluate on Benchmark Datasets"]
    E --> F{"Report Metrics<br>(DockQ, RMSD, etc.)"}
    
```

**Explanation:**

*   **Nodes:** Steps in the model evaluation process.
*   **Edges:**  Flow of execution.
*   **Diamond Node:** represents a selection or decision.
*   **Style:** A flowchart provides a sequential view of the evaluation and selection procedure.

-----


### 5. Components and processes (Diagram)

Illustrates key process and components

```mermaid
---
title: "Components and processes"
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
    A[AlphaFold-Multimer] --> B{Input Data}
    B --> C[Amino Acid Sequences]
    B --> D[Template Structures]
    B --> E[Paired MSA]
    A --> F{Core Processing}
    F --> G[Modified Evoformer]
    F --> H[Multi-chain Symmetry Handling]
    F --> I[Interface-Aware Loss]
    A --> J{Output Structure and Metrics}
    J --> K[Structure Coordinates]
    J --> L[ipTM/pTM]
    J --> M[DockQ]

    style A fill:#ccf3,stroke:#333,stroke-width:1px
    
```

**Explanation:**

*   **Nodes:** Processes or data stores (MSA generation, Evoformer, datasets, etc.).
*   **Edges:** Represent the flow of information between components.
*   **Style:** Directed graph emphasizes the relationships between the main concepts.


----


### 6. Metrics and Definitions (Table)

Provides a structured overview of the evaluation metrics used.

```mermaid
---
title: "Metrics and Definitions"
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
graph TD
    A["Evaluation Metrics"] --> B{DockQ}
    B --> B1("Range:<br> [0, 1]")
    B --> B2("Measures the quality of the interface")
    B --> B3("Cutoffs:<br> Incorrect < 0.23, Acceptable 0.23-0.49, Medium 0.49-0.80, High > 0.80")
    A --> C{"ipTM<br>(Interface pTM)"}
    C --> C1("Predicted Interface TM-score")
    C --> C2("Estimates model accuracy on interfaces")
    A --> D{"pTM<br>(Predicted TM-score)"}
    D --> D1("Predicted TM-score")
    D --> D2("Estimates overall model accuracy")
    A --> E{"RMSD<br>(Root Mean Square Deviation)"}
    E --> E1("Measures difference between predicted and ground truth structures")
    
```

**Explanation:**

*   **Nodes:** Represent each metric.
*   **Edges:** Connect metrics to their descriptions and properties.
*   **Style:** A structured graph provides a clear summary of metrics.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---