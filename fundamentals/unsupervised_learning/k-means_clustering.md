# K-Means Clustering

<img width="833" height="699" alt="image" src="https://github.com/user-attachments/assets/ed111ee9-13fb-402f-8355-a1b5e81955da" />

## Overview
K-means clustering is a widely used unsupervised learning algorithm that partitions data into K distinct, non-overlapping clusters. The objective is to group similar data points based on distance in multi-dimensional space.

This is commonly used for:
- Customer segmentation
- Recommendation systems
- Pattern discovery
- Marketing analytics

## How It Works

### 1. Initialization
Randomly select K data points as the initial centroids.

### 2. Assignment
Assign each data point to the nearest centroid using a distance metric (typically Euclidean distance).

### 3. Update
Recalculate each centroid as the mean of all points assigned to that cluster.

### 4. Iterate
Repeat assign/update steps until the centroids no longer change significantly or a maximum number of iterations is reached.

The goal is to minimize within-cluster variance.

## Euclidean Distance

Used to measure similarity between data points.

Formula:

d(x, y) = sqrt(Σ (xi - yi)²)

Where xi and yi are feature values for data points x and y.

## Choosing the Optimal K

<img width="859" height="545" alt="image" src="https://github.com/user-attachments/assets/233bbd40-7542-4889-ad51-a01aefb9f941" />


Choosing K is essential because it directly affects cluster quality and interpretability.

### Elbow Method
1. Run K-means for a range of K values.
2. Compute WCSS (Within-Cluster Sum of Squares) for each K.
3. Plot WCSS vs K.
4. Identify the “elbow” point where the decrease in WCSS slows.

This point balances model simplicity and cluster compactness.

### Silhouette Analysis

<img width="1189" height="592" alt="image" src="https://github.com/user-attachments/assets/9881ea9c-b687-429f-be94-fab7193ae903" />

A more quantitative metric for evaluating K.

- Score ranges from -1 to 1.
- Higher values indicate better-defined clusters.

Steps:
1. Run K-means for various K values.
2. Compute silhouette score for each point.
3. Compute the average silhouette score per K.
4. Select the K with the highest average score.

## Domain Expertise
While mathematical techniques help, real-world context matters. Practical considerations include:
- Interpretability of clusters
- Business constraints
- Whether the chosen K makes sense in the operational environment

## Data Assumptions

K-means works best when:
- Clusters are roughly spherical
- Clusters have similar sizes
- Features are standardized or normalized
- There are few outliers (outliers distort centroids)

Standardizing the data before applying K-means is highly recommended.








