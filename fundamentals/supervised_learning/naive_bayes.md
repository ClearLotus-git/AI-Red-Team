# Naive Bayes

<img width="687" height="545" alt="image" src="https://github.com/user-attachments/assets/cd942707-b404-44cc-8101-dd2c5c79637e" />

## What Is Naive Bayes?
Naive Bayes is a probabilistic classification algorithm based on **Bayes' Theorem**.  
It is simple, efficient, and commonly used for:
- Spam detection  
- Text classification  
- Sentiment analysis  

It works well even with high-dimensional data like documents.

---

## Bayes' Theorem
Bayes' theorem gives the probability of an event based on prior knowledge and new evidence.

Formula:
```
P(A|B) = [P(B|A) * P(A)] / P(B)
```

Where:
- **P(A|B)** = Posterior probability (probability of A given B)  
- **P(B|A)** = Likelihood  
- **P(A)** = Prior probability of A  
- **P(B)** = Evidence probability  

---

## Example (Disease Test)
Given:
- P(A) = 0.01 (1% have disease)  
- P(B|A) = 0.95 (95% test positive if diseased)  
- P(B|¬A) = 0.05 (false positive rate)  
- P(¬A) = 0.99  

Compute the probability of testing positive:
```
P(B) = P(B|A)*P(A) + P(B|¬A)*P(¬A)
     = 0.059
```

Compute posterior:
```
P(A|B) = (0.95 * 0.01) / 0.059 ≈ 0.161
```

A positive test gives only a **16.1% chance** of actually having the disease.

---

## How Naive Bayes Works
Naive Bayes uses Bayes' theorem with the **assumption of conditional independence** between features.

Steps:
1. **Calculate prior probabilities** for each class  
   (e.g., P(spam) = 0.2, P(not spam) = 0.8)  
2. **Calculate likelihoods**  
   Probability of each feature given each class  
3. **Apply Bayes' theorem** to compute posterior probabilities  
4. **Predict the class** with the highest posterior probability  

Even though features may not truly be independent, Naive Bayes performs well in many real tasks.

---

## Types of Naive Bayes

### Gaussian Naive Bayes
- For continuous features  
- Assumes data follows a Gaussian (normal) distribution  
- Example: predicting outcomes based on age, height, income  

### Multinomial Naive Bayes
- For discrete count-based features  
- Widely used in text classification  
- Example: word frequency in documents  

### Bernoulli Naive Bayes
- For binary features (present/absent)  
- Example: whether a word appears in a document at least once  

Choice depends on the nature of your data.

---

## Data Assumptions
- **Conditional Independence**: Features are independent given the class  
- **Correct feature distribution**  
  - Gaussian → continuous  
  - Multinomial → word counts  
  - Bernoulli → binary indicators  
- **Enough training data** to estimate probabilities accurately  

---

## Summary
Naive Bayes:
- Is simple and fast  
- Uses Bayes' Theorem to classify  
- Assumes feature independence  
- Works well for text, spam, and sentiment tasks  
- Has variants for different data types  

