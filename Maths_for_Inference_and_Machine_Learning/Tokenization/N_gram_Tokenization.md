---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# N-gram Tokenization
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## N-gram Tokenization - A Diagram Structure


```mermaid
---
title: N-gram Tokenization
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
graph TD
    A[N-gram Tokenization] --> B{Input Text}
    B --> C(Text String)
    C --> D[Tokenization Process]

    subgraph Tokenize_into_N_Grams
        D --> E{"N-gram Size (N)"}
        E --> F[Sliding Window]
        F --> G{Extract consecutive N-grams}
        G --> H[N-gram Tokens]
        
    end
    
    H --> I[Output N-grams]
    
    subgraph Example
        C -- "This is a sentence." --> E1("N=2");
        E1 --> F1["'This', 'is', 'is a', 'a sentence', 'sentence.'"]
        F1 --> G1["'This is', 'is a', 'a sentence', 'sentence.'"]
        G1 --> H1["'This is', 'is a', 'a sentence', 'sentence.'"]
        H1 --> I1["Output: This is, is a, a sentence, sentence."]
        
        C -- "This is a sentence." --> E2("N=3")
        E2 --> F2["'This', 'is', 'is a', 'a sentence', 'sentence.'"]
        F2 --> G2["'This is a', 'is a sentence', 'a sentence.'"]
        G2 --> H2["'This is a', 'is a sentence', 'a sentence.'"]
        H2 --> I2["Output: This is a, is a sentence, a sentence."]
        
    end
    
```


----

### Explanation

The diagram illustrates the process of N-gram tokenization.

* **Input Text:**  The input is a string of text.
* **N-gram Size (N):**  This determines the length of the consecutive sequences to be extracted.
* **Sliding Window:**  A sliding window of size N moves across the input text, extracting overlapping N-grams.
* **Extract consecutive N-grams:** The process identifies and isolates consecutive sequences of N tokens.
* **N-gram Tokens:** The output of the extraction process.
* **Output N-grams:** The resulting sequence of N-grams.

The example section demonstrates how the process works for different values of N (N=2 and N=3).  It clearly shows the overlapping sequences extracted from the input sentence "This is a sentence."


---


### Important Considerations

* **Tokenization:** The diagram implicitly assumes that the input text has already been tokenized into individual words or sub-words.  The specific tokenization method (e.g., splitting by spaces, using a tokenizer like WordPiece) needs to be applied before N-gram creation.
* **Handling Punctuation and Special Characters:**  How to handle punctuation, special characters, and other elements of the text is crucial for accurate N-gram extraction.  Will punctuation be included as a token, or should it be excluded?
* **Case Sensitivity:** Should the N-grams be case-sensitive or case-insensitive?
* **Vocabulary Size:** Depending on the application, the size of the vocabulary derived from the N-grams will change.  This needs to be considered if the vocabulary will be large.
* **Contextual Information:**  In some cases, contextual information might influence the generation of the N-grams.  For example, if working with sentences, knowing the beginning or end of the sentence might influence how the N-grams are processed.


This diagram provides a high-level overview of the process.  More detailed diagrams could be created to depict specific aspects of the process, like the handling of special characters or the use of a tokenizer.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---