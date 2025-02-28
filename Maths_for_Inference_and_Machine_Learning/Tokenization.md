---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Tokenization
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagram Structure



```mermaid
---
title: Tokenization
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
    A[Tokenization] --> B{Types of Tokenization}
    B --> C(Word Tokenization)
    C --> CA{Splitting text into individual words}
    
    subgraph Word_Tokenization_Example["Word Tokenization Example"]
        CA -- Example: 'Hello, world!' --> CB["'Hello', ',', 'world', '!'"]
    end

    B --> D(Subword Tokenization)
    D --> DA{Splitting words into sub-units}
    
    subgraph Subword_Tokenization_Example["Subword Tokenization Example"]
        DA -- Example: 'unbelievable' --> DB["'un', 'believ', 'able'"]
    end

    B --> E(Character Tokenization)
    E --> EA{Splitting text into individual characters}
    
    subgraph Character_Tokenization_Example["Character Tokenization Example"]
        EA -- Example: 'Hello' --> EB["'H', 'e', 'l', 'l', 'o'"]
    end


    B --> F(Sentence Tokenization)
    F --> FA{Splitting text into individual sentences}
    
    subgraph Sentence_Tokenization_Example["Sentence Tokenization Example"]
        FA -- Example: 'This is a sentence. This is another sentence.' --> FB["'This is a sentence.', 'This is another sentence.'"]
    end
    

    B --> G(N-gram Tokenization)
    G --> GA{Splitting text into sequences of n words}
    
    subgraph Ngram_Tokenization_Example["Ngram Tokenization Example"]
        GA -- Example: 'This is a sentence' (n=2) --> GB["'This is', 'is a', 'a sentence'"]
    end
    

    B --> H(Other Tokenization Techniques)
    H --> HA{Other types, depending on application}
    
    subgraph Other_Tokenization_Techniques_Example["Other Tokenization Techniques Example"]
        HA -- Example: Named Entity Recognition, part-of-speech tagging --> HB["'Named Entity Recognition', 'part-of-speech tagging'"]
    end
    
```

----

### Explanation and Considerations

* **Tokenization:**  The overall process of breaking down text into smaller units (tokens).

* **Word Tokenization:** The simplest form, splitting text into individual words.  Punctuation is often handled as separate tokens, or removed before tokenization.

* **Subword Tokenization:**  Breaks down words into smaller sub-units, like prefixes and suffixes, to handle out-of-vocabulary words or rare words.

* **Character Tokenization:**  Splits text into individual characters. This can be useful for tasks that require even finer-grained analysis or for languages without clear word boundaries.

* **Sentence Tokenization:**  Splits text into sentences, using punctuation marks to determine sentence boundaries.

* **N-gram Tokenization:**  Generates sequences of n words (n-grams). Useful for capturing word context and relationships within a sequence.

* **Other Tokenization Techniques:**  A catch-all category for specialized techniques like named entity recognition (NER) or part-of-speech (POS) tagging, which are more complex tokenization procedures that may not be straightforwardly split into tokens but may be part of the overall process.

---


### Diagram Elements and Interpretation

*   **Nodes:** Each node represents a type of tokenization or a concept related to tokenization.
*   **Edges:** Arrows connect a node to another to show relationships and dependencies.
*   **Subgraphs:** The use of subgraphs can group related concepts for a more structured visual.
*   **Examples:** The examples clarify the tokenization process by providing illustrative input-output pairs.



This diagram provides a high-level overview of tokenization types and demonstrates the different ways text can be broken down into smaller units.  The specific examples are just illustrative; the actual tokenization rules can vary significantly depending on the language and the application.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---