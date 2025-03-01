---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Byte Pair Encoding (BPE)
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Byte Pair Encoding - A Diagram Structure




```mermaid
---
title: Byte Pair Encoding (BPE)
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
    A["Byte Pair Encoding<br>(BPE)"] --> B{Core Concepts}
    B --> C[Vocabulary Building]
    C --> CA[Start with individual bytes]
    CA --> CB[Frequency Counting]
    CB --> CC[Identify the most frequent byte pairs]
    CC --> CD[Merge frequent pairs]
    CD --> CE[Update vocabulary]
    CE --> CF[Repeat steps until convergence or a maximum number of merges]

    B --> D[Encoding Process]
    D --> DA[Tokenize input text into bytes]
    DA --> DB[Look up bytes in the vocabulary]
    DB --> DC[If byte pair found, replace with merged pair; otherwise, keep as byte]
    DC --> DD[Repeat for all bytes]
    DD --> DE[Output the encoded tokens]

    B --> E[Decoding Process]
    E --> EA[Break down each token into constituent bytes]
    EA --> EB[Look up bytes in the reversed vocabulary]
    EB --> EC[If a merged pair found, replace with its constituent bytes; otherwise, keep as byte]
    EC --> ED[Repeat for all bytes in a token]
    ED --> EE[Output the decoded tokens]

    B --> F[Vocabulary Structure]
    F --> FA[Initial Vocabulary]
    FA --> FB[Byte Pairs]
    FB --> FC[Merged Pairs]
    FC --> FD[Reversed Vocabulary]
    FD --> FE[Mapping between bytes and tokens]
    
    B --> G{Example}
    G --> GA["Input:<br>'low', 'lower', 'newest', 'newest'"]
    GA --> GB[Initial Vocabulary:<br>low, lower, newest, new]
    GB --> GC[Frequent Byte Pairs:<br>low-lower, new-newest]
    GC --> GD[Updated Vocabulary:<br>low, lower, new, newest]
    GD --> GE[Encoding:<br>low -> low, lower -> lower, newest -> new-est, new -> new]
    GE --> GF[Decoding:<br>new-est -> newest, new -> new, low -> low, lower -> lower]

    B --> H[Training Process]
    H --> HA[Training Dataset]
    HA --> HB[Tokenize Data]
    HB --> HC[Frequency Counting]
    HC --> HD[Merge Byte Pairs]
    HD --> HE[Vocabulary Construction]
    HE --> HF[Repeat until Convergence]
    
```

---


### Explanation

* **Core Concepts:**  This subgraph encompasses the fundamental ideas behind BPE. It breaks down the process into key phases.

* **Vocabulary Building:** This section illustrates how the vocabulary is created. The initial vocabulary starts with individual bytes.  Frequency counting is crucial. Byte pairs are merged iteratively until convergence (or a predefined limit).

* **Encoding Process:** This describes how the BPE algorithm turns text into a sequence of tokens. The input is tokenized into individual bytes. The algorithm checks the vocabulary for merged pairs. If found, the pair is replaced.  Crucially, this iterative process of lookup and replacement continues until all input bytes are processed.

* **Decoding Process:** This mirrors the encoding process but reverses it.  Each token is broken down. The reversed vocabulary is used to look up the constituent bytes. The reversed process is essential to recover the original text.

* **Vocabulary Structure:** This section highlights the organization of the BPE vocabulary. It's vital to have clear mappings between original bytes and the merged tokens.

* **Example:** A simple example demonstrates the BPE process using sample input text and frequent byte pairs. This concrete example clarifies the abstract concepts.

* **Training Process:** This subsection shows the training phase of BPE. The dataset is tokenized. Frequencies are counted. Merges are performed iteratively until the vocabulary converges to a stable state.


This Mermaid diagram provides a comprehensive visual representation of the Byte Pair Encoding (BPE) algorithm, covering its core components, the encoding and decoding processes, vocabulary structure, and the training phase.  The example demonstrates how the algorithm works in practice. Remember to adapt and enhance these diagrams with specific details from the actual documentation you are working with.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---