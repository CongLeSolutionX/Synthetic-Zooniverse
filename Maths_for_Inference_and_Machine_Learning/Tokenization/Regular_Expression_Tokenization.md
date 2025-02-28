---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Regular Expression Tokenization
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Regular Expression Tokenization - A Diagram Structure



```mermaid
---
title: Regular Expression Tokenization
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
    A[Regular Expression Tokenization] --> B{Types of Tokens}
    B --> C(Keywords)
    C --> CA["Reserved words<br>(e.g., 'if', 'else', 'for')"]
    C --> CB["Language constructs<br>(e.g., '+', '-', '*', '.' )"]
    C --> CC["Identifiers<br>(e.g., variable names, function names)"]
    
    B --> D(Literals)
    D --> DA["Numeric literals<br>(e.g., '123', '3.14')"]
    D --> DB["String literals<br>(e.g., 'hello', 'world')"]
    D --> DC["Boolean literals<br>(e.g., 'true', 'false')"]

    B --> E(Operators)
    E --> EA["Arithmetic operators<br>(e.g., '+', '-', '*', '/')"]
    E --> EB["Comparison operators<br>(e.g., '==', '!=', '>', '<')"]
    E --> EC["Logical operators<br>(e.g., '&&', '||', '!')"]
    E --> ED["Assignment operators<br>(e.g., '=' ,'+=')"]
    E --> EE["Other operators<br>(e.g., '.' ,'->')"]

    B --> F(Punctuation)
    F --> FA["Parentheses<br>('(', ')')"]
    F --> FB["Braces<br>('{', '}')"]
    F --> FC["Brackets<br>('[', ']')"]
    F --> FD["Semicolons<br>(';')"]
    F --> FE["Commas<br>(',')"]
    
    B --> G(Whitespace)
    G --> GA["Spaces"]
    G --> GB["Tabs"]
    G --> GC["Newlines"]

    B --> H(Comments)
    H --> HA["Single-line comments"]
    H --> HB["Multi-line comments"]


    subgraph Summary
        C --> CI[Regular expressions define patterns to match specific tokens]
        D --> DI[Literals represent data values]
        E --> EI[Operators perform actions or comparisons]
        F --> FI[Punctuation defines the structure and flow of the code]
        G --> GI[Whitespace is ignored in the parsing process, but is crucial to readability]
        H --> HI[Comments are for documentation and are ignored in parsing]
        
        I[Tokenization Process] --> IJ[Regex matching applied to the input]
        IJ --> IK[Matching tokens are extracted and classified]
        IK --> IL[Tokens are returned]
    end
    
```

---

### Explanation

This diagram outlines the different types of tokens that can be generated during regular expression-based tokenization.  It categorizes these tokens into:

* **Keywords:** Reserved words with special meanings in the language (e.g., `if`, `for`, `while`).
* **Literals:**  Representing data values, including numeric (integers, floats), string (sequences of characters), and boolean (true/false) literals.
* **Operators:** Symbols used for arithmetic, comparison, logical, and assignment operations.
* **Punctuation:**  Marks like parentheses, braces, brackets, semicolons, and commas that structure the code.
* **Whitespace:** Spaces, tabs, and newlines are often ignored during the tokenization process itself but are vital for code readability.
* **Comments:**  Text annotations for documentation, typically ignored during parsing.

The diagram shows how regular expressions are used to match these patterns in the input code, resulting in a sequence of classified tokens. This sequence of tokens is the output of the tokenization process.  The diagram emphasizes the process from the input string to the output tokens, showcasing how regular expressions play a central role in identifying and classifying these different token types.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---