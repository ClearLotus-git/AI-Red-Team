<img width="685" height="548" alt="image" src="https://github.com/user-attachments/assets/1b0b8bfc-a79b-4128-a08a-80beb2d8fa93" />

# Linear Regression 

## What is Regression?
Regression = predicting a **continuous number**, not a category.

Examples:
- Predicting house price  
- Forecasting temperature  
- Estimating website traffic  

Regression outputs a **number**, unlike classification which outputs a label.

---

## What is Linear Regression?
Linear Regression assumes a **straight-line relationship** between input(s) and output.

Its goal: find the **best-fitting line** that predicts **y** from **x**.

---

## Simple Linear Regression (1 input)
Equation:

```
y = mx + c
```

Where:
- **y** = predicted value  
- **x** = input  
- **m** = slope (how much y changes when x changes)  
- **c** = intercept (y when x = 0)  

The model tries to find the best **m** and **c**.

---

## Multiple Linear Regression (many inputs)
Equation:

```
y = b0 + b1*x1 + b2*x2 + ... + bn*xn
```

Where:
- **x1, x2, ..., xn** = input features  
- **b0** = intercept  
- **b1...bn** = coefficients for each feature  

---

## Ordinary Least Squares (OLS)

<img width="840" height="702" alt="image" src="https://github.com/user-attachments/assets/398e39f9-f44c-47ee-8e3c-0b2846aab71d" />

OLS finds the best line by minimizing the **sum of squared errors**.

Steps:
1. Predict **y** for each data point  
2. Compute residuals:  
   ```
   residual = actual_y - predicted_y
   ```
3. Square each residual  
4. Add them up → **RSS (Residual Sum of Squares)**  
5. Choose coefficients that **minimize RSS**

This gives the “line of best fit.”

---

## Key Assumptions
Linear Regression works best when these assumptions hold:

1. **Linearity** — Relationship between inputs and output is roughly linear  
2. **Independence** — Data points don’t depend on each other  
3. **Homoscedasticity** — Residuals have equal variance (no funnel shape)  
4. **Normality** — Errors are roughly normally distributed  

If these fail, predictions can be unreliable.

---

## Summary
Linear Regression:
- Predicts numbers  
- Uses a straight-line relationship  
- Finds best coefficients using OLS  
- Works best when assumptions are met  
