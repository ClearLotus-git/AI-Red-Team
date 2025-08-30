# Mathematics Refresher for AI (Notes)

## Basic Arithmetic
- Multiplication `*` → product (3 * 4 = 12)  
- Division `/` → quotient (10 / 2 = 5)  
- Addition `+` → sum (5 + 3 = 8)  
- Subtraction `-` → difference (9 - 4 = 5)  

## Algebraic Notation
- Subscript `x_t` → variable at time t (used in sequences, time series)  
- Superscript `x^n` → exponent/power  
- Norm `||v||` → vector length  
  - Euclidean: `sqrt(v1^2 + v2^2 + ... + vn^2)`  
  - L1: `|v1| + |v2| + ...`  
  - L∞: `max(|v1|, |v2|, ...)`  

## Summation
- `Σ` → sum of sequence (Σ a_i from i=1 to n)  

## Logs & Exponentials
- log2(x) → base 2 logarithm (log2(8) = 3)  
- ln(x) → natural log (base e)  
- e^x → exponential growth/decay  
- 2^x → exponential base 2 (used in binary systems)  

## Matrices & Vectors
- Matrix-Vector mult → transforms vector (A * v)  
- Matrix-Matrix mult → combine transformations (A * B)  
- Transpose `A^T` → swap rows/columns  
- Inverse `A^-1` → matrix that undoes A  
- Determinant `det(A)` → scalar, shows if invertible  
- Trace `tr(A)` → sum of diagonal  

## Set Theory
- Cardinality `|S|` → number of elements  
- Union `A ∪ B` → all elements from both sets  
- Intersection `A ∩ B` → common elements  
- Complement `A^c` → all elements not in A  

## Comparison Operators
- `>=` greater or equal  
- `<=` less or equal  
- `==` equality  
- `!=` inequality  

## Eigenvalues & Eigenvectors
- Eigenvalue λ → scalar in `A * v = λ * v`  
- Eigenvector → direction unchanged by transformation (scaled by λ)  
- Used in PCA, dimensionality reduction  

## Functions & Operators
- max(...) → largest value  
- min(...) → smallest value  
- Reciprocal `1/x` → inverse of x  
- Ellipsis `...` → continuation in sequence  

## Functions & Probability
- Function notation `f(x)` → mapping input to output  
- Conditional probability `P(x|y)` → prob of x given y  
- Expectation `E[X]` → average/mean over distribution  
- Variance `Var(X)` → spread around mean  
- Std Dev `σ(X)` → sqrt of variance  
- Covariance `Cov(X,Y)` → how two variables vary together  
- Correlation `ρ(X,Y)` → normalized covariance (between -1 and 1)  
