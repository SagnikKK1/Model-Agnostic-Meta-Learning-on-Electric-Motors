# Galileo Ferraris Contest: Data-Driven Traction Motor Design

## Overview
This repository is dedicated to the **Galileo Ferraris Contest**, where participants leverage data-driven methodologies to analyze and model traction motors. The contest emphasizes the challenges of **multi-physical** interactions in motor design, requiring advanced techniques to optimize performance while balancing contrasting constraints.

## Context
Traction motors present a **complex design challenge** due to their **multi-physical** nature, involving interactions across multiple domains:
- **Electromagnetic**
- **Thermal**
- **Structural**
- **Acoustic**

These interactions impose **demanding constraints**, making traditional design approaches less effective. Instead, **data-driven pre-design tools** become crucial for efficient modeling and optimization.

### Key Challenges
1. **Contrasting Design Criteria**: Multiple factors must be considered in the design process, often competing against each other:
   - **Torque vs. Temperature**
   - **Rotating Speed vs. Mechanical Stresses**
   - Other domain-specific trade-offs

2. **Need for a Multi-Physical Approach**: Since different physics-based interactions influence performance, an integrated modeling strategy is necessary.

3. **Optimization for Performance**: A Pareto-optimal approach is needed to **balance trade-offs** and ensure an efficient motor design under varying constraints.

## Data-Driven Approach
Given these challenges, we explore the application of **machine learning and optimization techniques** to predict motor performance across different operating conditions. Potential approaches include:
- **Supervised Machine Learning techniques** for incorporating data driven approaches.
- **Model Agnostic Meta-Learning (MAML)** to generalize across different motor datasets.

## Tasks
Our model will be tested on a 8 input, 7 output multiregression task, with the help of the inverse geometric distance 
based on the optimal pareto front.
- Interpolation Problem: The input will be generated from Motor A or Motor B, which has been provided to us. The current mean R2 score is **0.97**
- Extrapolation Problem: The input will be generated from Motor C, whose partial dataset will be provided to us soon. Currently our extrapolation MAML model is trained only on Dataset A and fine-tuned on 256 rows (6.25%) of Dataset B, and the rest (93.75%) of B is used for testing purposes. Here we have been able to reach a R2 score of **0.93** and above for 5 out of the 7 outputs. We are currently figuring out methods for improving our model for the prediction of Torque Ripple specifically.

## Repository Structure
- **data/**: Contains training and test datasets for different motor types.
- **notebooks/**: Jupyter notebooks for exploratory analysis and model development.

## Next Steps
- Implement and test transformer based Model Agnosting Meta Learning frameworks instead of the MLP based ones.
- Use unsupervised learning for clustering the combined datasets into their motor class and use the labels for the interpolation task.
- Use specific models to improve our predictions on Torque ripple which has come out to be the largest obstacle till now.
## Acknowledgments
This project is inspired by the **Galileo Ferraris Contest**, which promotes innovative approaches to traction motor design. The dataset and problem formulation are derived from real-world constraints encountered in engineering applications.


