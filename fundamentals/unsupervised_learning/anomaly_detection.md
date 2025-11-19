# Anomaly Detection

<img width="790" height="389" alt="image" src="https://github.com/user-attachments/assets/5d8fe27f-69a1-4fbd-9ad7-c4c040549395" />


## Overview
Anomaly detection (outlier detection) is an unsupervised learning task that identifies data points that differ significantly from normal patterns. These unusual points may indicate fraud, system failures, medical issues, cyberattacks, or rare events.

An easy analogy is a security system: it learns normal activity and raises an alarm when something unusual happens. Similarly, anomaly detection models learn normal data behavior and flag data points that deviate from it.

---

## Types of Anomalies

### Point Anomalies
Single data points that are significantly different from the rest.  
Examples:  
- Sudden spike in network traffic  
- An unusually large credit card charge  

### Contextual Anomalies
Values that are only anomalous within a specific context.  
Examples:  
- 30°C temperature (normal in summer, abnormal in winter)  

### Collective Anomalies
A sequence or group of points that collectively deviate from normal behavior.  
Examples:  
- A burst of login attempts from unknown IPs  
- Coordinated unusual activity patterns  

---

## Techniques for Anomaly Detection

### Statistical Methods
Assume data follows a distribution (often Gaussian) and flag points far from the mean.  
Examples:  
- Z-score  
- Modified Z-score  
- Boxplot outliers  

### Clustering-Based Methods
Group data into clusters and detect points that do not belong or lie in sparse clusters.  
Examples:  
- K-Means  
- Density-based clustering  

### Machine Learning Methods
Learn patterns of normal behavior and classify points that do not fit.  
Examples:  
- One-Class SVM  
- Isolation Forest  
- Local Outlier Factor (LOF)

---

## One-Class SVM
One-Class SVM is specifically designed for anomaly detection. It learns a boundary that encloses the normal data. Any point outside the boundary is classified as an anomaly.

It can model nonlinear boundaries using kernel functions. Conceptually, it “draws a fence” around normal points—anything outside is treated as suspicious.

---

## Isolation Forest
Isolation Forest identifies anomalies by isolating data points through random splits.  
Anomalies are easier to isolate because they are rare and different.

### How It Works:
1. Build multiple isolation trees by randomly choosing:
   - A feature  
   - A split value  
2. Recursively partition the data until every point is isolated.  
3. Measure the average path length needed to isolate each point.  
   - Shorter paths = more anomalous  

### Anomaly Score

score(x) = 2^(-E(h(x)) / c(n))

Where:  
- E(h(x)): Average path length of x in all isolation trees  
- c(n): Average path length of an unsuccessful search in a BST  
- n: Number of observations  

Scores close to 1 indicate anomalies.  
Scores around 0.5 indicate normal points.

---

## Local Outlier Factor (LOF)
LOF is a density-based method. It identifies anomalies by comparing the local density of a point to that of its neighbors.

A point is an anomaly if its local density is much lower than those nearby.

### LOF Score

LOF(p) = (Σ lrd(o) / k) / lrd(p)

Where:  
- lrd(p): Local reachability density of p  
- lrd(o): Local reachability density of neighbor o  
- k: Number of neighbors  

Higher LOF scores indicate stronger anomalies.

---

## Local Reachability Density

lrd(p) = 1 / (Σ reach_dist(p, o) / k)

Where:  
- reach_dist(p, o): max(actual distance(p, o), k-distance of o)

Points in dense regions have low reachability distances; points in sparse regions have high reachability distances.

---

## Data Assumptions

Different anomaly detection methods have different assumptions:

- Some assume **normal data follows a distribution** (e.g., Gaussian).  
- Feature selection matters: irrelevant features reduce performance.  
- Some machine learning methods require **labeled normal data**, though many operate unsupervised.  

---

One-Class SVM 
<img width="707" height="545" alt="image" src="https://github.com/user-attachments/assets/26f99b2a-310a-4df1-8a41-fd5110bf1d67" />

Isolation-forest
<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/70400d2e-75e3-4acc-b616-63a069d38ba7" />

Local-Outlier Factor

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/852ab486-fb94-458f-ab60-74e4f0b421d6" />


## Summary
Anomaly detection is vital in detecting unusual patterns across domains like fraud detection, cybersecurity, healthcare, and monitoring systems. Techniques such as statistical analysis, clustering, One-Class SVM, Isolation Forest, and LOF each provide different approaches to identifying unusual data points. These methods help detect critical events early and support effective decision-making.

