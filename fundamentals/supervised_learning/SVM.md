# Support Vector Machines

<img width="689" height="545" alt="image" src="https://github.com/user-attachments/assets/0c85f43e-5dfb-4af7-bf96-914111599bc0" />

## What Are SVMs?
Support Vector Machines are supervised learning algorithms used for:
- Classification
- Regression (SVR)

They work well with:
- High-dimensional data  
- Non-linear patterns  
- Complex boundaries  

SVMs find an **optimal hyperplane** that separates classes with the **maximum margin**.

---

## Maximizing the Margin
An SVM chooses the hyperplane that leaves the **largest possible gap** between classes.

Key terms:
- **Margin**: distance between the hyperplane and closest data points  
- **Support Vectors**: the points closest to the boundary; they define the margin  

A larger margin → better generalization and robustness.

---

## Linear SVM
Used when classes are **linearly separable**.

Goal:
- Find a straight line (or hyperplane in higher dimensions) that maximizes the margin and separates classes.

<img width="678" height="545" alt="image" src="https://github.com/user-attachments/assets/8d3322c8-a643-4f52-8690-893461a042bf" />


Hyperplane equation:
```
w * x + b = 0
```

Where:
- **w** = weight vector (perpendicular to the hyperplane)  
- **x** = feature vector  
- **b** = bias  

SVM training finds the optimal w and b.

---

## Non-Linear SVM

<img width="689" height="545" alt="image" src="https://github.com/user-attachments/assets/c71c745a-a869-49ed-8d2e-00b8cb42673b" />

Most real-world data is **not** linearly separable.

SVMs handle this using the **kernel trick**, which maps data into a higher-dimensional space where a linear separator *can* be found.

You cannot see the new space directly, but the kernel does the transformation mathematically.

---

## Kernel Trick
A kernel function computes similarity between points in a transformed feature space without explicitly computing the transformation.

Common kernels:

### Polynomial Kernel
Captures curved relationships by including polynomial terms (x², x³, etc.).

### RBF (Radial Basis Function) Kernel
Most common kernel.  
Captures complex, non-linear patterns using a Gaussian similarity function.

### Sigmoid Kernel
Similar to activation in neural networks.  
Useful for certain types of non-linear separation.

---

## Practical Example: Spam Classification
Plot each email by:
- x-axis: frequency of “free”
- y-axis: frequency of “money”

A linear SVM finds a line separating spam vs. not spam.  
A non-linear SVM (using RBF) could draw a curved boundary if needed.

Support vectors are the closest points that determine this boundary.

---

## Optimization Formulation
SVM finds the hyperplane by solving:

```
Minimize: 1/2 ||w||^2
Subject to: yi(w * xi + b) >= 1 for all i
```

Where:
- **w** = weight vector  
- **xi** = data point  
- **yi** = class label (-1 or 1)  
- **b** = bias  

This maximizes the margin while keeping all points correctly classified.

---

## Why SVMs Work Well
SVMs are effective because they:

- **Do not assume a data distribution**  
- Handle **high-dimensional feature spaces**  
- Are **robust to outliers**  
- Can learn **non-linear boundaries** via kernels  

They are widely used in:
- Image classification  
- Text classification  
- Bioinformatics  
- Complex pattern recognition  

---

## Key Assumptions
SVMs require minimal assumptions:
- No need for linearity  
- No specific distribution required  
- Works even when features > samples  
- Assumes classes can be separated (possibly in higher dimensions)

---

## Summary
Support Vector Machines:
- Find the hyperplane that maximizes the margin  
- Use support vectors to define boundaries  
- Can model both linear and non-linear relationships  
- Use kernels to handle complex data patterns  
- Are powerful for high-dimensional classification tasks  



