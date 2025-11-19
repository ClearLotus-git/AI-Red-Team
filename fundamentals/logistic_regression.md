# Logistic Regression 

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/e81b6245-1237-4887-b7f6-aed6700b7ed3" />


## What is Logistic Regression?
Despite the name, logistic regression is used for **classification**, not regression.

It predicts **binary labels** such as:
- spam / not spam  
- click / no click  
- disease / no disease  

Output = probability between **0 and 1**, then converted into a class label.

---

## What is Classification?
Classification predicts **categories**, not numbers.

Examples:
- Fraud vs. not fraud  
- Cat vs. dog  
- Disease vs. no disease  

Regression → number  
Classification → label  

---

##  How Logistic Regression Works
1. Takes a **linear combination** of input features  
2. Passes it through a **sigmoid function**  
3. Output becomes a **probability**  
4. Probability is compared to a **threshold**  
5. Final decision = class 0 or class 1

---

## The Sigmoid Function

<img width="565" height="456" alt="image" src="https://github.com/user-attachments/assets/9ca386bd-a946-4c34-a7d3-6accfdec4b57" />


```
P(x) = 1 / (1 + e^-z)
```

Where:
- **P(x)** = predicted probability (0 → 1)  
- **e** = ~2.718  
- **z** = linear combination of inputs:  
  ```
  z = m1*x1 + m2*x2 + ... + mn*xn + c
  ```

The sigmoid is an **S-shaped curve** that converts any number into a probability.

---

##  Example: Spam Detection
Model checks:
- keywords  
- sender  
- message length  
- patterns  

Returns probability like:  
```
P(spam) = 0.82
```

If the threshold is 0.5 → classify as spam.  
If threshold is 0.8 → it must be very certain to label spam.

---

##  Decision Boundary

<img width="844" height="701" alt="image" src="https://github.com/user-attachments/assets/cf2cc4ee-2142-41c3-9d7e-570f233fc78f" />


In 2D (two features): a **line** that separates the classes.  
In higher dimensions: a **hyperplane**.

Points on one side → Class 0  
Points on the other → Class 1

---

##  What is a Hyperplane

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/77233a65-495c-43b8-8b41-730d8300ae16" />


A hyperplane is a flat separator:

- In 2D → a line  
- In 3D → a flat plane  
- In n-dimensions → same concept, just harder to visualize  

Logistic regression uses this hyperplane as the decision boundary.

---

##  Threshold Probability
Default threshold = **0.5**, but you can change it.

Rules:
- If `P(x) >= threshold` → classify as **positive (1)**
- If `P(x) < threshold` → classify as **negative (0)**

Tuning threshold helps control:
- false positives  
- false negatives  
- sensitivity vs. specificity  

---

##  Assumptions of Logistic Regression
1. **Binary outcome** (only two classes)  
2. **Linearity of log-odds** (features relate linearly to log-odds, not raw probability)  
3. **Low multicollinearity** (features shouldn't be highly correlated)  
4. **Large sample size** for stable estimates  

Good practice:
- check correlations  
- visualize feature relationships  
- ensure target variable is binary  

---

## Summary
Logistic Regression:
- Predicts **class labels**  
- Uses **sigmoid** to output probability  
- Uses a **decision boundary / hyperplane** to classify  
- Works well when assumptions are met  
