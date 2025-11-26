# Network Anomaly Detection — NSL-KDD + Random Forest (Summary)

## What is Anomaly Detection?
Anomaly detection finds data points that deviate from normal patterns. In cybersecurity, anomalies can indicate intrusions, malicious traffic, or unusual network behavior.

## Why Use Random Forests?
Random Forests are an ensemble of decision trees that handle high-dimensional data well, reduce overfitting, and provide robust, generalizable predictions.

### Key Random Forest Concepts
- Bootstrapping: Each tree is trained on a random sample (with replacement)
- Random Features: A random subset of features is used at each split
- Voting/Averaging: Predictions are combined (majority vote for classification)

## Random Forests for Anomaly Detection
The model is trained on normal (benign) data. New data is compared to learned normal patterns. Low confidence or abnormal patterns are flagged as anomalies.

## NSL-KDD Dataset
A cleaned, balanced version of the original KDD’99 dataset:
- Removes duplicate records
- Fixes class imbalance
- Supports binary and multi-class attack detection
- Widely used for intrusion detection research

## Downloading the Dataset
```python
import requests, zipfile, io

url = "https://academy.hackthebox.com/storage/modules/292/KDD_dataset.zip"
response = requests.get(url)

z = zipfile.ZipFile(io.BytesIO(response.content))
z.extractall('.')  # Extract to current directory
```

## Import Libraries
```
import numpy as np
import pandas as pd
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, confusion_matrix, classification_report
import seaborn as sns
import matplotlib.pyplot as plt
```


## Define File Path + Columns
```
file_path = r'KDD+.txt'

columns = [
    'duration','protocol_type','service','flag','src_bytes','dst_bytes',
    'land','wrong_fragment','urgent','hot','num_failed_logins','logged_in',
    'num_compromised','root_shell','su_attempted','num_root',
    'num_file_creations','num_shells','num_access_files','num_outbound_cmds',
    'is_host_login','is_guest_login','count','srv_count','serror_rate',
    'srv_serror_rate','rerror_rate','srv_rerror_rate','same_srv_rate',
    'diff_srv_rate','srv_diff_host_rate','dst_host_count','dst_host_srv_count',
    'dst_host_same_srv_rate','dst_host_diff_srv_rate',
    'dst_host_same_src_port_rate','dst_host_srv_diff_host_rate',
    'dst_host_serror_rate','dst_host_srv_serror_rate',
    'dst_host_rerror_rate','dst_host_srv_rerror_rate',
    'attack','level'
]
```

## Load Dataset into a DataFrame

```
df = pd.read_csv(file_path, names=columns)
print(df.head())
```
