#  Data Preprocessing for Machine Learning

Data preprocessing transforms raw, messy, or incomplete data into a structured and clean format ready for analysis or machine learning. Without proper cleaning and formatting, models can become inaccurate, biased, or even fail completely.

---

##  Key Preprocessing Techniques

| Technique         | Purpose                                                                 |
|------------------|-------------------------------------------------------------------------|
| **Data Cleaning** | Handle missing values, remove duplicates, fix inconsistencies          |
| **Data Transformation** | Normalize, encode, scale, or reduce data                          |
| **Data Integration** | Merge and aggregate from multiple sources                             |
| **Data Formatting** | Ensure correct types (e.g., int, float), reshape if needed             |

---

##  Step-by-Step Cleaning for `demo_dataset.csv`

The dataset contains:
- Mixed types (numeric, categorical, textual)
- Missing or invalid entries (`?`, `STRING_PORT`, `NON_NUMERIC`, etc.)
- Anomalies in key fields (e.g., IPs, ports, bytes)

---

##  Check for Invalid Values

### 1. **Invalid IP Addresses**

```python
import re

def is_valid_ip(ip):
    pattern = re.compile(r'^((25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$')
    return bool(pattern.match(ip))

invalid_ips = data[~data['source_ip'].astype(str).apply(is_valid_ip)]
print(invalid_ips)
```

<img width="907" height="631" alt="image" src="https://github.com/user-attachments/assets/709c9b59-8807-4cba-b466-baed19b7f973" />


### 2. **Invalid Port Numbers**

```python
def is_valid_port(port):
    try:
        port = int(port)
        return 0 <= port <= 65535
    except ValueError:
        return False

invalid_ports = data[~data['destination_port'].apply(is_valid_port)]
print(invalid_ports)
```
<img width="890" height="565" alt="image" src="https://github.com/user-attachments/assets/e0e99406-4c5f-4930-9783-c0f701d21fc7" />


### 3. **Invalid Protocols**

```python
valid_protocols = ['TCP', 'TLS', 'SSH', 'POP3', 'DNS', 'HTTPS', 'SMTP', 'FTP', 'UDP', 'HTTP']
invalid_protocols = data[~data['protocol'].isin(valid_protocols)]
print(invalid_protocols)
```
<img width="883" height="339" alt="image" src="https://github.com/user-attachments/assets/d27a9dc9-4c98-44a2-b1a4-1b99ca24c0e5" />


### 4. **Invalid `bytes_transferred` Values**

```python
def is_valid_bytes(x):
    try:
        return int(x) >= 0
    except:
        return False

invalid_bytes = data[~data['bytes_transferred'].apply(is_valid_bytes)]
print(invalid_bytes)
```

<img width="895" height="472" alt="image" src="https://github.com/user-attachments/assets/92a150f1-e315-44fc-a6f6-4b56617c3a91" />


### 5. **Invalid `threat_level` Entries**

```python
def is_valid_threat_level(x):
    try:
        return 0 <= int(x) <= 2
    except:
        return False

invalid_threat_levels = data[~data['threat_level'].apply(is_valid_threat_level)]
print(invalid_threat_levels)
```

<img width="912" height="507" alt="image" src="https://github.com/user-attachments/assets/c8bce588-949c-4090-aa74-75be4847c8f8" />


---

##  Dropping Invalid Entries

```python
data = data.drop(invalid_ips.index, errors='ignore')
data = data.drop(invalid_ports.index, errors='ignore')
data = data.drop(invalid_protocols.index, errors='ignore')
data = data.drop(invalid_bytes.index, errors='ignore')
data = data.drop(invalid_threat_levels.index, errors='ignore')
print(data.describe(include='all'))
```
<img width="914" height="604" alt="image" src="https://github.com/user-attachments/assets/63902000-cafa-4552-9ffa-7f04b2e3826c" />

---

## Replacing Invalids with `NaN`

```python
import numpy as np

# Replace invalid string flags with NaN
data.replace(['INVALID_IP', 'MISSING_IP', 'STRING_PORT', 'UNUSED_PORT', 
              'NON_NUMERIC', 'NEGATIVE', '?'], np.nan, inplace=True)

# Convert columns to proper numeric format
data['destination_port'] = pd.to_numeric(data['destination_port'], errors='coerce')
data['bytes_transferred'] = pd.to_numeric(data['bytes_transferred'], errors='coerce')
data['threat_level'] = pd.to_numeric(data['threat_level'], errors='coerce')
```

---

## Imputing Missing Values

### Simple Imputation (Mean/Median/Most Frequent)

```python
from sklearn.impute import SimpleImputer

# Impute numeric columns
num_cols = ['destination_port', 'bytes_transferred', 'threat_level']
num_imputer = SimpleImputer(strategy='median')
data[num_cols] = num_imputer.fit_transform(data[num_cols])

# Impute categorical protocol
cat_imputer = SimpleImputer(strategy='most_frequent')
data[['protocol']] = cat_imputer.fit_transform(data[['protocol']])
```

### Advanced Imputation (KNN)

```python
from sklearn.impute import KNNImputer

knn_imputer = KNNImputer(n_neighbors=5)
data[num_cols] = knn_imputer.fit_transform(data[num_cols])
```

---

## Domain-Based Fixes

```python
valid_protocols = ['TCP', 'TLS', 'SSH', 'POP3', 'DNS', 'HTTPS', 'SMTP', 'FTP', 'UDP', 'HTTP']
data.loc[~data['protocol'].isin(valid_protocols), 'protocol'] = data['protocol'].mode()[0]

data['source_ip'] = data['source_ip'].fillna('0.0.0.0')
data['destination_port'] = data['destination_port'].clip(lower=0, upper=65535)
```

---

##  Final Data Check

```python
print(data.describe(include='all'))
```
<img width="718" height="490" alt="image" src="https://github.com/user-attachments/assets/f613aa3f-f52a-4a0a-866c-75ed5c81a9ed" />

---

##  Summary

| Step                        | Goal                                 |
|-----------------------------|--------------------------------------|
| Clean invalid strings       | Replace with `NaN`                   |
| Convert types               | Convert to numeric where applicable  |
| Impute missing data         | Median for numeric, mode for category |
| Validate ranges             | Ports, bytes, threat level           |
| Final inspection            | Confirm data is clean and ready      |

---

## Dataset Reference
[📄 demo_dataset.csv](sandbox:/mnt/data/demo_dataset.csv)

