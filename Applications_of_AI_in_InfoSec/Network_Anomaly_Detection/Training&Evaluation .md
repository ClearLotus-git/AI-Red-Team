# Training & Evaluation — Network Anomaly Detection (NSL-KDD)

This document summarizes the training, validation, and testing workflow for a **Random Forest multi-class network anomaly detection model** using the **NSL-KDD** dataset.  
The model classifies traffic into five categories:

- **Normal**
- **DoS**
- **Probe**
- **Privilege Escalation**
- **Access Attacks**

---

## 1. Model Training

A Random Forest model (`random_state=1337`) is trained on the multi-class training split (`multi_train_X`, `multi_train_y`).  
This step learns traffic patterns that distinguish normal activity from various attack behaviors.

---

## 2. Validation Phase

The trained model is evaluated on a validation set to measure generalization before final testing.

Metrics computed:
- **Accuracy** — overall correctness  
- **Precision (weighted)** — correctness of predicted attack labels  
- **Recall (weighted)** — ability to detect actual attacks  
- **F1-Score (weighted)** — balance between precision & recall  

Additional validation outputs:
- **Confusion matrix** visualized with Seaborn  
- **Classification report** showing per-class precision, recall, F1, and support  

This phase helps understand class-specific weaknesses before testing on unseen data.

---

## 3. Test Set Evaluation

Final performance is measured on the held-out test set.  
Observed dataset distribution (approx):

- 15,349 Normal  
- 10,708 DoS  
- 2,788 Probe  
- 703 Access  
- Minor cross-class misclassifications observed  

Metrics computed on the test set:
- **Accuracy**
- **Precision (weighted)**
- **Recall (weighted)**
- **F1-Score (weighted)**

Additional outputs:
- **Confusion matrix** (test set)
- **Classification report** (test set)

This step represents true, real-world performance on never-before-seen traffic.

---

## 4. Model Persistence (Saving the Model)

The trained Random Forest model is saved to disk using Joblib:

`network_anomaly_detection_model.joblib`

This enables reuse for:
- Deployment  
- Inference scripts  
- Future retraining  
- Model comparison and versioning  

---

##  Summary of Accomplishments

- Successfully trained a **Random Forest multi-class classifier** for network anomaly detection  
- Validated performance using accuracy, precision, recall, and F1-score  
- Generated confusion matrices and classification reports for both validation and test sets  
- Exported the fully trained model for deployment or later analysis  

This workflow establishes a complete baseline anomaly detection pipeline using the NSL-KDD dataset.
