# Principal Component Analysis (PCA)

<img width="1316" height="590" alt="image" src="https://github.com/user-attachments/assets/c3b03195-40f2-4755-b703-345fffc1b51b" />


## Overview
Principal Component Analysis (PCA) is a dimensionality reduction technique used to transform high-dimensional data into a lower-dimensional space while preserving as much information as possible. It identifies new variables called principal components, which are linear combinations of the original features and capture the maximum variance in the data.

PCA is commonly used for:
- Feature extraction  
- Noise reduction  
- Data visualization  
- Pattern recognition  

Example: In image processing, PCA reduces the dimensionality of image data while keeping key features such as edges, textures, and shapes.

PCA can be thought of as finding the most informative "directions" in the data that explain the largest amount of variation.

<img width="704" height="688" alt="image" src="https://github.com/user-attachments/assets/74910adf-b6d2-4e11-a423-ca314928aff6" />

---

## Key Concepts

### Variance
Measures the spread of data around the mean. PCA aims to maximize variance in the directions of the principal components.

### Covariance
Measures how two variables change together. PCA uses the covariance matrix to understand relationships between features.

### Eigenvectors and Eigenvalues
- Eigenvectors: Directions of maximum variance (principal components)
- Eigenvalues: Amount of variance captured by each eigenvector

<img width="714" height="391" alt="image" src="https://github.com/user-attachments/assets/d7fe326c-dbf6-4b13-9c14-bb5b19a49ea8" />

Larger eigenvalues correspond to components that explain more variance.

---

## PCA Algorithm Steps

### 1. Standardize the Data
Subtract the mean and divide by the standard deviation so that all features have equal scale.

### 2. Compute Covariance Matrix
Calculate the covariance matrix of the standardized dataset. This shows how features vary with one another.

### 3. Compute Eigenvectors and Eigenvalues
Determine eigenvectors (directions of variance) and eigenvalues (amount of variance) of the covariance matrix.

### 4. Sort Eigenvectors
Sort eigenvectors in descending order based on their eigenvalues. Higher eigenvalues represent more important components.

### 5. Select Principal Components
Choose the top k eigenvectors based on the desired target dimensionality.

### 6. Transform the Data
Project the original dataset onto the selected principal components to obtain the lower-dimensional representation.

---

## Understanding Eigenvalues and Eigenvectors

An eigenvector is a vector that maintains its direction after being transformed by a matrix. Its eigenvalue indicates how much it is stretched or compressed.

Example:

A = [[2, 0],  
     [0, 1]]

v = [1, 0]

A * v = [2, 0]

The vector remains in the same direction but is scaled by 2, meaning:
- Eigenvector: [1, 0]  
- Eigenvalue: 2

---

## Eigenvalue Equation in PCA

The principal components are obtained by solving the eigenvalue equation:

C * v = λ * v

Where:
- C is the covariance matrix  
- v is an eigenvector (principal component direction)  
- λ is the eigenvalue (variance explained by v)

---

## Methods for Solving Eigenvalue Problems

### Eigenvalue Decomposition
Direct computation of eigenvalues and eigenvectors from the covariance matrix.

### Singular Value Decomposition (SVD)
A more stable numerical method that decomposes the data matrix into singular vectors and singular values. Often preferred in practical implementations.

---

## Selecting Principal Components

After computing eigenvectors and eigenvalues:
1. Sort eigenvectors by descending eigenvalues.
2. Choose the top k eigenvectors.
3. Form a matrix V containing these eigenvectors.
4. Transform the original data X using:

Y = X * V

Where:
- Y is the reduced-dimensional representation  
- V contains the selected principal components  

---

## Choosing the Number of Components

A common method is analyzing the explained variance ratio. This shows how much total variance each component accounts for. A typical goal is retaining components that explain around 95% of total variance.

Plotting cumulative explained variance helps determine the point of diminishing returns.

---

## Data Assumptions

PCA assumes:
- Linearity between variables  
- High correlation between features  
- Equal feature scale (requires standardization)  

Because PCA is sensitive to feature scaling and outliers, preprocessing steps like normalization and outlier removal are often important.

---

## Summary
PCA simplifies datasets by projecting them into a lower-dimensional space while retaining the most important variance. It is widely used in machine learning, computer vision, and statistical analysis for compression, visualization, denoising, and improving model performance.

