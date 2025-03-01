---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Binomial Distribution
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
title: Binomial Distribution
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
    A[Binomial Distribution] --> B{Definition}
    B --> C(Discrete Probability Distribution)
    C --> D[Describes the probability of getting exactly k successes in n independent Bernoulli trials]
    
    subgraph Binomial_Distribution_Components["Binomial Distribution Components"]
        D -- n --> E[n]
        E -- Number of trials --> F[Number of trials]
        D -- k --> G[k]
        G -- Number of successes --> H[Number of successes]
        D -- p --> I[p]
        I -- Probability of success in a single trial --> J[Probability of success]

        D -- Formula --> K["p(k; n, p) = (n choose k) * p^k * (1-p)^(n-k)"]
        K -- (n choose k) --> L[(n choose k)]
        L -- Combination --> M[Combination of n items taken k at a time]

    end
    
    subgraph Binomial_Distribution_Properties["Binomial Distribution Properties"]
        D -- Mean --> N["E(k) = n*p"]
        D -- Variance --> O["Var(k) = n*p*(1-p)"]
    end

    subgraph Examples["Examples"]
        O -- Coin Flips --> P["Probability of getting exactly 3 heads in 5 coin flips if p(head) = 0.5"]
        O -- Quality Control --> Q["Probability of finding exactly 2 defective items in a batch of 10 if p(defective) = 0.1"]
    end

```

---


### Explanation

The diagram depicts the Binomial Distribution, highlighting its key components and properties.

* **Definition:** The Binomial Distribution is a discrete probability distribution.
* **Components:**  It's defined by:
    * `n`: The number of independent Bernoulli trials.
    * `k`: The number of successes observed in those `n` trials.
    * `p`: The probability of success in a single trial.
* **Formula:** The probability mass function (PMF) is shown, emphasizing the combination (n choose k) and the powers of `p` and `(1-p)`.
* **Properties:** The diagram also shows the mean (expected value) and variance of the distribution.
* **Examples:** Practical examples demonstrate how the binomial distribution can model real-world scenarios involving repeated Bernoulli trials.

This diagram effectively visualizes the key elements of the Binomial Distribution, facilitating understanding of its use in probability calculations.  Note that this diagram is highly adaptable for adding more details like specific examples, or calculations depending on the context.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---