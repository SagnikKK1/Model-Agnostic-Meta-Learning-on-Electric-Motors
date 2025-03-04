# Galileo Ferraris Contest (GalFer) - Multi-Physics Simulation of Traction Electrical Machines

## Overview
This repository contains our work for the **Galileo Ferraris Contest (GalFer Contest)**, which aims to compare data-driven methodologies for the multi-physics simulation of traction electrical machines. Participants are provided with datasets for two **IVM-type motors** (Motor A and Motor B) and are tasked with:

1. Creating a model that **interpolates well** within the given datasets.
2. Developing a model that can generalize to **Motor C**, another IVM-type motor, for which only input data is provided.

The final results will be evaluated based on the **accuracy and efficiency** of the methodologies, particularly in assessing the **Pareto Front** in the performance space.

## Dataset Details
- **Motor A:** Complete dataset for training.
- **Motor B:** Dataset split into **fine-tuning (256 rows)** and **testing**.
- **Motor C:** Only input data provided, requiring zero-shot generalization.

## Approach
We implement **Model-Agnostic Meta-Learning (MAML)** to train a neural network that learns a good initialization from Motor A, fine-tunes on Motor B, and aims to generalize to Motor C.

### Methodology
1. **Preprocessing:**
   - Standardize input and output features.
   - Split Motor B into a fine-tuning subset (256 rows) and a test set.

2. **Meta-Learning using MAML:**
   - Train on **Motor A** using MAML to learn a general representation.
   - Fine-tune on **Motor B** (256 rows) for adaptation.
   - Evaluate performance on **Motor B's test set**.

3. **Evaluation:**
   - R² Score and Percentage Error per output variable.
   - The final step involves generalization testing on Motor C.

## Code Structure
```
|-- data/                 # Dataset (Motor A, Motor B, Motor C)
|-- models/               # Neural network and MAML implementation
|-- scripts/              # Training, fine-tuning, and evaluation scripts
|-- main.py               # Entry point for training and evaluation
|-- README.md             # Project documentation (this file)
```

## Dependencies
- Python 3.x
- PyTorch
- NumPy
- Pandas
- Scikit-learn

Install dependencies using:
```sh
pip install torch numpy pandas scikit-learn
```

## Running the Code
### 1. Train MAML on Motor A:
```sh
python main.py --train
```

### 2. Fine-Tune on 256 Rows of Motor B:
```sh
python main.py --fine-tune
```

### 3. Evaluate Model on Remaining Motor B Data:
```sh
python main.py --evaluate
```

## Results
The model is evaluated using **R² score** and **percentage error** on Motor B. Future work involves extending generalization to Motor C.

## Next Steps
- Develop a **zero-shot** prediction approach for Motor C.
- Improve meta-learning strategies for better adaptation.
- Explore alternative loss functions for improved robustness.

## Contributors
- **[Your Name]** - [Your Email]
- **[Collaborators]**

---
*This is an ongoing research project as part of the GalFer Contest. Contributions and suggestions are welcome!*

