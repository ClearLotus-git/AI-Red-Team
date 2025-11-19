# Decision Trees

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/d4a6b69a-8995-46f4-b297-9dc27c9103e2" />
 

## What Are Decision Trees?
Decision trees are supervised learning models used for:
- Classification
- Regression

They use a tree-like structure of decisions to make predictions.  
A tree consists of:
- **Root Node**: The starting point; contains the full dataset  
- **Internal Nodes**: Ask a question based on a feature  
- **Leaf Nodes**: Final predictions or outcomes  

Example: deciding whether to play tennis based on weather conditions.  
The tree asks simple yes/no or multi-branch questions until it reaches a final decision.

---

## How Decision Trees Are Built
A tree is built by choosing the **best feature to split the data** at each step.

Splits are chosen using measures such as:
- **Gini Impurity**
- **Entropy**
- **Information Gain**

Goal: create subsets that are as **pure** as possible (mostly one class).

---

## Gini Impurity
Measures how often you would misclassify a randomly chosen item from the set.

Formula:
```
Gini(S) = 1 - Σ (pi)^2
```

Where:
- S = dataset
- pi = proportion of class i

Example with 30 of class A and 20 of class B:
```
pA = 0.6
pB = 0.4
Gini = 1 - (0.6^2 + 0.4^2) = 0.48
```

---

## Entropy
Measures uncertainty or disorder in the set.

Formula:
```
Entropy(S) = - Σ pi * log2(pi)
```

Example with pA = 0.6, pB = 0.4:
```
Entropy = 0.970954
```

---

## Information Gain
Measures reduction in entropy after splitting on a feature.

Formula:
```
Information Gain(S, A) = Entropy(S) - Σ ((|Sv| / |S|) * Entropy(Sv))
```

Example:
- Total entropy = 0.970954  
- Weighted subset entropy = 0.95098  

```
Information Gain = 0.970954 - 0.95098 = 0.019974
```

The feature with the highest information gain is selected for the split.

---

## Tree Building Process
1. Start with the root node using all data  
2. Evaluate each feature using Gini, entropy, or information gain  
3. Split on the best feature  
4. Repeat for each subset  
5. Stop when:
   - Maximum depth reached  
   - Too few samples left  
   - Node becomes pure (all one class)  


---

<img width="950" height="636" alt="image" src="https://github.com/user-attachments/assets/db888ec1-a806-4c2f-a58c-334efd5fb4cc" />


## Example: Playing Tennis
Dataset features:
- Outlook: Sunny, Overcast, Rainy  
- Temperature: Hot, Mild, Cool  
- Humidity: High, Normal  
- Wind: Weak, Strong  

Target: PlayTennis (Yes/No)

Process:
1. Calculate information gain for each feature  
2. Choose the feature with highest gain (commonly Outlook in this example)  
3. Split into subsets (Sunny, Overcast, Rainy)  
4. Continue splitting each subset using the best remaining feature  
5. Continue until pure nodes or stopping criteria

Final result: a tree with rules such as:
- If Outlook = Sunny → check Humidity  
- If Outlook = Overcast → Play Tennis = Yes  
- If Outlook = Rainy → check Wind  

---

## Data Assumptions
Decision trees require minimal assumptions:
- No linearity required  
- No normal distribution required  
- Robust to outliers  
- Works well with both numerical and categorical data  

This flexibility makes decision trees widely applicable across many tasks.

---

## Summary
Decision trees:
- Use splitting rules to classify or predict  
- Select best features using Gini, entropy, or information gain  
- Produce interpretable, rule-based models  
- Require minimal data assumptions  
