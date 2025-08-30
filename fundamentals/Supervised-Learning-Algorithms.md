# Supervised Learning Algorithms (Notes)

## Definition
- Learn from **labeled data** → input features + known outcomes (labels)
- Goal: build a mapping function to predict labels for **new, unseen data**

Example: like teaching a child fruits by showing examples with names.

---

## Types of Problems
- **Classification** → predict categories (spam vs not spam, cat/dog/bird)
- **Regression** → predict continuous values (house price, stock forecast)

---

## Core Concepts
- **Training Data** → labeled dataset, foundation for learning
- **Features** → input variables (e.g., size, location, age of house)
- **Labels** → target/output variable (e.g., house price)
- **Model** → mathematical function mapping features → label
- **Training** → adjust parameters to minimize prediction error
- **Prediction** → use model on new data for label output
- **Inference** → understand structure, relationships, importance of features

---

## Evaluation
Metrics to measure performance:
- **Accuracy** → proportion of correct predictions
- **Precision** → true positives / predicted positives
- **Recall** → true positives / actual positives
- **F1-score** → harmonic mean of precision & recall

---

## Key Ideas
- **Generalization** → ability to perform well on unseen data
- **Overfitting** → model memorizes training data (poor generalization)
- **Underfitting** → model too simple, misses patterns (poor performance overall)
- **Cross-Validation** → split data into folds to test generalization
- **Regularization** → prevents overfitting by penalizing complexity
  - L1 → absolute value penalty  
  - L2 → squared value penalty  
