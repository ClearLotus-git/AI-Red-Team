# Model Evaluation Metrics — Summary

## Core Metrics

**Accuracy**
- Measures overall correctness  
- Formula: (TP + TN) / Total  
- Can be misleading with imbalanced data (e.g., 99% non-spam → high accuracy even if no spam is caught)

**Precision**
- Measures how often predicted positives are correct  
- Formula: TP / (TP + FP)  
- High precision = fewer false alarms

**Recall (Sensitivity)**
- Measures how many actual positives were found  
- Formula: TP / (TP + FN)  
- High recall = fewer missed positives

**F1-Score**
- Harmonic mean of precision and recall  
- Formula: 2 * (P * R) / (P + R)  
- Best for balancing precision vs. recall in imbalanced datasets

## Why Multiple Metrics Matter
- Accuracy alone can hide poor performance on minority classes
- Precision ≠ Recall (you can have high one, low the other)
- F1 provides a balanced view

## Example Context
Metrics:  
- Accuracy: 0.975  
- Precision: 0.930  
- Recall: 0.910  
- F1: 0.920  

Interpretation:
- Strong overall performance
- Balanced detection
- Good for real-world tasks if data is representative

## Additional Useful Metrics
- **Specificity** – Correctly identifies negatives
- **AUC-ROC** – Overall discrimination ability
- **MCC** – Strong metric for imbalanced datasets
- **Confusion Matrix** – Visual breakdown (TP, FP, TN, FN)

## Application-Specific Tradeoffs
- **Threat Detection** → Favor Recall (don’t miss threats)
- **Resource-Limited Systems** → Favor Precision (reduce false alarms)

## Final Insight
Best practice: Evaluate **Accuracy + Precision + Recall + F1 + Confusion Matrix** together to ensure robust, meaningful real-world performance.
