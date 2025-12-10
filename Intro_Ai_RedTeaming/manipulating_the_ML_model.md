# Manipulating ML Models: Input Attacks & Data Poisoning (Summary)

This section demonstrates how machine learning models—specifically a Naive Bayes spam classifier—can be manipulated through **input modification (ML01)** and **training data poisoning (ML02)**. Using the baseline spam classifier from the “Applications of AI in InfoSec” module, we examine how altering inputs or training samples impacts classification outcomes.

## 1. Input Manipulation (Evasion Attacks)

### Rephrasing
Attackers can reword malicious messages to avoid detection. By testing individual words, we observe how certain terms strongly influence spam probability. Example:
- **"Congratulations!"** → flagged as spam due to its association with common phishing lures.
- Avoiding spam-triggering terms or rephrasing messages (e.g., “Your account has been blocked…”) can cause the classifier to misclassify spam as ham.

### Overpowering
Because Naive Bayes treats words independently, attackers can append long benign text to overwhelm spam indicators. For example, adding part of *Lorem Ipsum* turns a clear spam message into one classified as ham with **100% confidence**, despite the malicious link still being present.

## 2. Training Data Manipulation (Poisoning)

A reduced training set (`poison.csv`, first 100 rows of `train.csv`) increases model sensitivity. Injecting intentionally mislabeled spam samples containing phrases from a target message (e.g., “Hello World”) causes the classifier to learn that these benign phrases are associated with spam.

### Effects of Poisoning
- Minimal poisoning (adding a few fake spam-labeled entries) forces misclassification.
- Confidence shifts from **Ham → Spam (98%+)** for inputs like “Hello World! How are you doing?”
- Overall accuracy drops only slightly (from 94.4% to 94.0%), showing that poisoning can remain hidden.

## Key Takeaways
- **Input manipulation** can bypass filters by rephrasing or adding benign content.
- **Data poisoning** can steer model behavior with very small changes to training data—especially when datasets are small.
- Both attack types reveal how ML systems can be exploited if input and training pipelines are not strictly controlled.


## Code Blocks


```
