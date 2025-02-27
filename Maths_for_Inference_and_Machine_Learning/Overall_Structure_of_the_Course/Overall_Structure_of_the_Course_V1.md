---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Overall Structure of the Course
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## The structure of the book

```mermaid
---
title: Mathematics for Inference and Machine Learning - The Table of Content
config:
  theme: dark
---
mindmap
    root((Mathematics for Inference and Machine Learning))
        Instructors
            Marc_Deisenroth
            Stefanos_Zafeiriou
        1_Linear_Regression
            1.1_Problem_Formulation
            1.2_Probabilities
                1.2.1_Means_and_Covariances
                    1.2.1.1_Sum_of_Random_Variables
                    1.2.1.2_Affine_Transformation
                1.2.2_Statistical_Independence
                1.2.3_Basic_Probability_Distributions
                    1.2.3.1_Uniform_Distribution
                    1.2.3.2_Bernoulli_Distribution
                    1.2.3.3_Binomial_Distribution
                    1.2.3.4_Beta_Distribution
                    1.2.3.5_Gaussian_Distribution
                    1.2.3.6_Gamma_Distribution
                    1.2.3.7_Wishart_Distribution
                1.2.4_Conjugacy
            1.3_Probabilistic_Graphical_Models
                1.3.1_From_Joint_Distributions_to_Graphs
                1.3.2_From_Graphs_to_Joint_Distributions
                1.3.3_Further_Reading
            1.4_Vector_Calculus
                1.4.1_Partial_Differentiation_and_Gradients
                    1.4.1.1_Jacobian
                    1.4.1.2_Linearization_and_Taylor_Series
                1.4.2_Basic_Rules_of_Partial_Differentiation
                1.4.3_Useful_Identities_for_Computing_Gradients
                1.4.4_Chain_Rule
            1.5_Parameter_Estimation
                1.5.1_Maximum_Likelihood_Estimation
                    1.5.1.1_Closed_Form_Solution
                    1.5.1.2_Iterative_Solution
                    1.5.1.3_Maximum_Likelihood_Estimation_with_Features
                    1.5.1.4_Properties
                1.5.2_Overfitting
                1.5.3_Regularization
                1.5.4_Maximum_A_Posterior_MAP_Estimation
                    1.5.4.1_MAP_Estimation_for_Linear_Regression
            1.6_Gradient_Descent
                1.6.1_Stepsize
                1.6.2_Gradient_Descent_with_Momentum
                1.6.3_Stochastic_Gradient_Descent
                1.6.4_Further_Reading
            1.7_Model_Selection_and_Cross_Validation
                1.7.1_Cross_Validation_to_Assess_the_Generalization_Performance
                1.7.2_Bayesian_Model_Selection
                1.7.3_Bayes_Factors_for_Model_Comparison
                1.7.4_Fully_Bayesian_Treatment
                1.7.5_Computing_the_Marginal_Likelihood
                1.7.6_Further_Reading
            1.8_Bayesian_Linear_Regression
                1.8.1_Model
                1.8.2_Parameter_Posterior
                    1.8.2.1_Linear_Transformation_of_Gaussian_Random_Variables
                    1.8.2.2_Completing_the_Squares
                1.8.3_Prediction_and_Inference
                    1.8.3.1_Derivation
        2_Feature_Extraction
            2.1_Decompositions
                2.1.1_Eigen_decomposition
                    2.1.1.1_Symmetric_Matrices
                2.1.2_QR_decomposition
                    2.1.2.1_Gram_Schmidt_Process
                2.1.3_Singular_Value_Decomposition
                    2.1.3.1_Thin_SVD
                    2.1.3.2_Dimensionality_Reduction_and_SVD
                2.1.4_Principal_Component_Analysis
                    2.1.4.1_Statistical_Perspective
                    2.1.4.2_Reconstruction_Perspective
                    2.1.4.3_Computing_PCA
                    2.1.4.4_Link_between_SVD_and_PCA
                2.1.5_Linear_Discriminant_Analysis
                    2.1.5.1_The_two_class_case
                    2.1.5.2_Multi_class_Case
            2.2_Computing_Linear_Discriminant_Analysis
                2.2.1_Kernel_PCA_and_Kernel_LDA
                    2.2.1.1_Maximum_Likelihood_for_Probabilistic_PCA
        3_Support_Vector_Machines
            3.1_Support_Vector_Classification
                3.1.1_Linear_Separating_Hyperplane_with_Maximal_Margin
                    3.1.1.1_Lagrangian_Duality
                    3.1.1.2_Conditions_for_Optimality_Karush_Kuhn_Tucker_Conditions
                    3.1.1.3_SVM_dual_problem
                3.1.2_Mapping_Data_to_Higher_Dimensional_Spaces
                3.1.3_The_Dual_Problem
            3.2_Support_Vector_Regression
                3.2.1_Linear_Regression
                3.2.2_Support_Vector_Regression
        Appendix
            A.1_Preliminaries_on_Vectors_and_Matrices
                A.1.1_Vectors_and_Vector_Operators
                A.1.2_Matrices_and_Matrix_Operators
                    A.1.2.1_Matrix_Norms
                    A.1.2.2_Matrix_Multiplications
                    A.1.2.3_Matrix_Transposition
                    A.1.2.4_Trace_Operator
                    A.1.2.5_Matrix_Determinant
                    A.1.2.6_Matrix_Inverse
                    A.1.2.7_Matrix_Pseudo_Inverse
                    A.1.2.8_Range_Null_Space_and_Rank_of_a_matrix
                    A.1.2.9_Eigenvalues_and_Eigenvectors
                    A.1.2.10_Positive_and_Negative_Definite_Matrices
                    A.1.2.11_Triangular_Matrices
                    A.1.2.12_QR_decomposition
                A.2_Scalar_Products
                    A.2.1_Lengths_Distances_Orthogonality
                    A.2.2_Applications
                A.3_Useful_Matrix_Identities

```

----

Here's a breakdown of the changes and why they were made:

*   **Structure:** The mind map is structured hierarchically, directly mirroring the structure of the table of contents.  The main title ("Mathematics for Inference and Machine Learning") is the root.  Each chapter, section, subsection, etc., becomes a child node of its parent.




----


## Mathematics for Inference and Machine Learning - A Diagrammatic Overview
```mermaid
---
title: Overall Structure of the Course
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
    A["Mathematics for Inference and Machine Learning"] --> B("Linear Regression")
    B --> C{"Probabilities"}
    B --> D{"Vector Calculus"}
    B --> E{"Parameter Estimation"}
    B --> F{"Gradient Descent"}
    B --> G{"Model Selection & Cross-Validation"}
    B --> H["Bayesian Linear Regression"]
    
    subgraph Feature_Extraction["Feature Extraction"]
        B --> I("Feature Extraction")
    end
    subgraph Support_Vector_Machines["Support Vector Machines"]
        I --> J("Support Vector Machines")
    end
    subgraph Appendices["Appendices"]
        A --> K["Appendices"]
    end

    C --> CA("Probability Density Functions")
    C --> CB("Means & Covariances")
    C --> CC("Statistical Independence")
    C --> CD("Basic Probability Distributions")
    C --> CE("Conjugacy")
    
    D --> DA("Partial Differentiation")
    D --> DB("Gradients")
    D --> DC("Jacobian")
    D --> DD("Linearization & Taylor Series")
    
    E --> EA("Maximum Likelihood Estimation")
    E --> EB("Overfitting")
    E --> EC("Regularization")
    E --> ED("Maximum-A-Posterior Estimation")
    
    F --> FA("Gradient Descent Algorithm")
    F --> FB("Stepsize")
    F --> FC("Momentum")
    F --> FD("Stochastic Gradient Descent")
    
    G --> GA(Cross-Validation)
    G --> GB(Bayesian Model Selection)
    G --> GC(Bayes Factors)
    
    H --> HA(Gaussian Prior)
    H --> HB(Parameter Posterior)
    H --> HC("Prediction & Inference")

    I --> IA("Eigen-decomposition")
    I --> IB(QR decomposition)
    I --> IC(SVD)
    I --> ID(PCA)
    I --> IE(LDA)
    I --> IF(Kernel Methods)

    J --> JA(Support Vector Classiﬁcation)
    J --> JB(Mapping to Higher Dimensions)
    J --> JC(Dual Problem)
    J --> JD(Support Vector Regression)

    K --> KA(Vector/Matrix Preliminaries)
    K --> KB(Scalar Products)
    K --> KC(Useful Matrix Identities)

    click A "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf" "Inference and Machine Learning Notes - Click to see the original lecture notes"
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---