---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Model Selection and Cross-Validation
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
title: Model Selection and Cross-Validation
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
    subgraph ModelSelectionAndCrossValidation["Model Selection And Cross-Validation"]
    style ModelSelectionAndCrossValidation fill:#ccf2,stroke:#333,stroke-width:2px
        A[Model Selection] --> B{Goal}
        B -- Identify the simplest model --> C[Model Complexity]
        C --> CA(Degree of Polynomial)
        C --> CB(Number of Components in Mixture Model)
        C --> CC(Network Architecture in Neural Network)
        C --> CD(Type of Kernel in SVM)
        
        B -- Balance Model Complexity & Data Fit --> D[Evaluation Metrics]
        D --> DA(Cross-Validation)
        D --> DB(Bayesian Model Selection)
        
        subgraph CrossValidation["Cross-Validation"]
        style CrossValidation fill:#cc63,stroke:#333,stroke-width:2px
            DA --> E[K-fold Cross-Validation]
            E --> EA{Partition Data}
            EA -- K Chunks --> EB[Training Set]
            EA -- 1 Chunk --> EC[Validation Set]
            E --> ED[Iterate over Partitions]
            ED -- Compute Generalization Error on Validation Set --> EF[Average Generalization Error]
            EF -- Choose Model with Best Average Error --> EG[Choose Best Model]
            
            subgraph HyperparameterTuning["Hyperparameter Tuning"]
            style HyperparameterTuning fill:#c613,stroke:#333,stroke-width:2px
                ED --> EH[Explore Hyperparameters]
                EH -- (e.g., Multiple Regularization Parameters) --> EI[Multiple Training Runs]
                EI -- Each Run --> EJ[Evaluate Model Quality]
                EJ -- Based on Validation Set --> EK[Choose Best Model Configuration]
            end
        end
        
        subgraph BayesianModelSelection["Bayesian Model Selection"]
        style BayesianModelSelection fill:#c613,stroke:#333,stroke-width:2px
            DB --> F[Bayesian Approach]
            F --> FA[Prior on Models]
            FA --> FB["p(M<sub>k</sub>)"]
            F --> FC[Prior on Model Parameters]
            FC --> FD["p(θ<sub>k</sub>|M<sub>k</sub>)"]
            F --> FE[Generative Process: M<sub>k</sub> θ<sub>k</sub> → D]
            FE --> FF["Posterior over Models: p(M<sub>k</sub>|D)"]
            FF -- Choose Model with Highest Posterior --> FG[Choose Best Model]
            
            subgraph BayesFactors["Bayes Factors"]
            style BayesFactors fill:#c693,stroke:#333,stroke-width:2px
                FF --> FH[Bayes Factor]
                FH -- p(D|M<sub>1</sub>)/p(D|M<sub>2</sub>) --> FI[Compare Models]
                FI -- Choose Model with Higher Bayes Factor --> FJ[Choose Best Model]
            end
        end 
    end
    
```
DOI: [10.13140/RG.2.2.33627.89125](http://dx.doi.org/10.13140/RG.2.2.33627.89125)


---

### Explanation

* **Model Selection:**  The overarching goal is to find the simplest model that effectively explains the data.  This involves considering model complexity, including factors like the polynomial degree, mixture model components, or the network architecture in a neural network.

* **Evaluation Metrics:** This involves methods for assessing how well a model generalizes to unseen data, which are crucial for model selection.  Two key methods are highlighted:

    * **Cross-Validation:**  A process that partitions the dataset into multiple subsets.  One subset is used as a validation set, while the rest is used for training.  This process is repeated for all possible partitions, and the model with the best average performance across all iterations is selected.  The diagram includes a subgraph for hyperparameter tuning, illustrating the common practice of exploring various model configurations during cross-validation.

    * **Bayesian Model Selection:**  This approach uses Bayesian probabilities to quantify the plausibility of different models. A prior is assigned to each model, along with priors on the model's parameters. The posterior probability of each model given the data is calculated, and the model with the highest posterior probability is selected. A subgraph is included to emphasize the use of Bayes factors for model comparison.

* **Hierarchical Structure:**  The diagram uses subgraphs to illustrate the hierarchical nature of these processes.  This visual clarity helps to understand the steps involved and their relationships.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---