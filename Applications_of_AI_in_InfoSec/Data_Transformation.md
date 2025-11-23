# Data Transformation & Splitting Notes

This document covers how to prepare your dataset for machine learning, especially focusing on encoding, scaling, and splitting.

---

##  Data Transformation

###  Encoding Categorical Features

Machine learning models need numeric data. Categorical data like `protocol` (e.g., TCP, FTP, etc.) must be converted.

** One-Hot Encoding**

This converts a categorical column into binary columns, one for each unique category.

```python
from sklearn.preprocessing import OneHotEncoder
import pandas as pd

encoder = OneHotEncoder(handle_unknown='ignore', sparse_output=False)
encoded = encoder.fit_transform(df[['protocol']])
encoded_df = pd.DataFrame(encoded, columns=encoder.get_feature_names_out(['protocol']))

# Replace original 'protocol' column
df = pd.concat([df.drop('protocol', axis=1), encoded_df], axis=1)
```

This ensures your model treats each protocol equally, not as ordered numbers.

---

##  Handling Skewed Data

Sometimes, numeric columns like `bytes_transferred` are **skewed**—they contain very large outliers. This hurts performance.

** Log Transformation**

```python
import numpy as np

# Apply log transform to reduce skewness
df["bytes_transferred"] = np.log1p(df["bytes_transferred"])  # log1p = log(1 + x)
```

This transformation spreads out low values and compresses high ones, helping models learn better.

---

##  Splitting the Data

To avoid overfitting and ensure fair model evaluation, we split the dataset into:

- **Training Set** – 60%
- **Validation Set** – 20%
- **Test Set** – 20%

###  Code for Splitting

```python
from sklearn.model_selection import train_test_split

# Split features and labels
X = df.drop("threat_level", axis=1)
y = df["threat_level"]

# First split: 80% train/val, 20% test
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=1337)

# Second split: from train, take 25% as validation (0.8 x 0.25 = 0.2)
X_train, X_val, y_train, y_val = train_test_split(X_train, y_train, test_size=0.25, random_state=1337)
```

###  Use Cases

- Train your model on `X_train`, `y_train`
- Tune hyperparameters on `X_val`, `y_val`
- Evaluate performance on `X_test`, `y_test`

---

##  Summary

| Task                    | Method Used              |
|-------------------------|--------------------------|
| Encode Categorical      | `OneHotEncoder`          |
| Fix Skewed Data         | `np.log1p()`             |
| Split Dataset           | `train_test_split()`     |

> These steps improve model learning, reduce bias from raw data, and ensure fair performance testing.

---

 _Next Steps_: You can now begin training models on your clean, well-prepped data.
