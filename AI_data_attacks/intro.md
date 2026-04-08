# Introduction to AI Data & Security

AI systems learn from data. Their performance, reliability, and security all depend on it.

If data is corrupted, manipulated, or leaked, the model inherits those issues. Models cannot distinguish between legitimate patterns and attacker-injected patterns.

This drives the entire AI threat landscape.

---

# The AI Data Pipeline

AI systems rely on a data pipeline:

Collect → Process → Transform → Utilize

Utilization targets:
- Train models
- Generate predictions

---

# 1. Data Collection

## Sources
- Web application logs (JSON, Kafka)
- Databases (PostgreSQL)
- IoT devices (MQTT)
- Web scraping
- Third-party data

## Key Challenges
- Multiple trust boundaries
- Diverse data formats (JPEG, JSON, semi-structured)

## Security Risk
- No inherent validation
- Malicious or low-quality data propagates downstream

---

# 2. Storage

## Storage Types
- Relational databases (PostgreSQL)
- NoSQL databases (MongoDB)
- Data lakes (S3, distributed storage)
- Time-series databases (InfluxDB)

## Stored Assets
- Datasets
- Serialized models (.pkl, .pt, ONNX)

## Security Risk
- Model files can be replaced or tampered with
- .pkl files can execute arbitrary Python code
- Attackers may bypass poisoning and directly replace models

---

# 3. Data Processing & Transformation

## Tasks
- Data cleaning (handling missing values)
- Scaling numerical features
- Feature engineering
- Distributed processing (Apache Spark)
- Workflow orchestration (Apache Airflow)

## Tools
- Pandas
- scikit-learn
- spaCy
- OpenCV

## Security Risk
- Processing logic is code and can be compromised
- Corruption can be introduced even if raw data appears clean

---

# 4. Modeling

## Process
- Data exploration (Jupyter Notebooks)
- Model training (PyTorch, TensorFlow)
- Hyperparameter tuning (Optuna)
- Validation and iteration

## Key Insight
- Models learn whatever data teaches them
- No inherent defense against poisoned data

## Security Reality
- Modeling is not the attack surface
- It is where the consequences appear

---

# 5. Deployment

## Common Patterns
- REST APIs (FastAPI, Flask)
- Containers (Docker)
- Orchestration (Kubernetes)
- Serverless functions
- Edge deployment

## Security Risk
- Model files are trusted implicitly
- Tampered models can lead to:
  - Incorrect predictions
  - Arbitrary code execution

---

# 6. Monitoring & Maintenance

## Monitoring Types
- Operational metrics (latency, throughput)
- ML metrics (data drift, prediction quality)

## Retraining
- Uses new data and feedback loops
- Automated through orchestration tools

## Security Risk
- Cannot distinguish real behavior vs malicious input
- Enables online data poisoning
- Attack exploits system design, not a bug

---

# Example 1: E-commerce Recommendation System

## Pipeline
- Data collection: Kafka streams, user activity, reviews
- Storage: AWS S3 data lake
- Processing: Apache Spark (session reconstruction, sentiment analysis)
- Modeling: AWS SageMaker
- Storage: Model saved as pickle file in S3
- Deployment: Docker + Kubernetes API
- Monitoring: Click-through rates
- Retraining: Continuous feedback loop

## Attack Surface
- Data streams
- Storage buckets
- Processing jobs
- Model files
- Retraining loop

---

# Example 2: Healthcare Diagnostic System

## Pipeline
- Data collection: Patient images and clinical notes
- Storage: Encrypted and restricted systems
- Processing: Python scripts for normalization and feature extraction
- Modeling: PyTorch training on specialized hardware
- Deployment: Internal API
- Retraining: Controlled and infrequent

## Key Insight
- Same pipeline structure as other systems
- Same vulnerabilities persist
- Higher stakes due to impact on patient care

---

# Core Takeaways

- AI systems are only as trustworthy as their data
- The main attack surface is in:
  - Data collection
  - Storage
  - Processing
- Models do not defend against poisoned data
- Retraining pipelines amplify risk
- Security weaknesses are structural, not incidental
