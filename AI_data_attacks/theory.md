# AI Data Attacks & Pipeline Threats

AI data attacks target the data pipeline itself. Instead of manipulating outputs at inference time (evasion) or extracting sensitive data (privacy attacks), these attacks corrupt the system earlier.

They:
- Poison training data
- Tamper with stored models
- Manipulate processing logic

By the time predictions are made, the compromise is already embedded.

---

# Attack Surface Across the Pipeline

Each pipeline stage has a corresponding attack:

- Data Collection → Data Poisoning
- Storage → Data/Model Tampering
- Processing → Logic Manipulation
- Modeling → Compromised Learning (inherited)
- Deployment → Model Injection
- Monitoring/Retraining → Online Poisoning

---

# 1. Data Collection Attacks (Data Poisoning)

## Method
Attackers inject malicious data through trusted input channels.

## Techniques
- Label flipping (incorrect labels)
- Feature manipulation (altered inputs)
- Backdoor triggers (hidden patterns)

## Example (E-commerce)
- Fake positive reviews submitted through API
- Reviews include hidden keyword triggers
- Model learns to favor attacker-controlled products

## Example (Healthcare)
- Altered DICOM metadata
- Mislabelled clinical notes
- Small perturbations accumulate into systemic bias

## Key Insight
- No system break-in required
- Attack uses legitimate input channels

---

# 2. Storage Attacks

## Type 1: Dataset Tampering
- Modify stored training data
- Change labels or features after collection

## Type 2: Model Tampering (Critical)

### Targets
- .pkl files
- .pt files
- ONNX models

### Risks
- Model replacement (trojaned models)
- Model stenography (hidden code inside model)

### Critical Issue
- Deserialization (e.g., pickle.load()) executes embedded code

## Impact
- Not just wrong predictions
- Full code execution on production systems

---

# 3. Processing Attacks

## Method
Attackers target transformation logic instead of raw data.

## Targets
- Cleaning scripts
- Feature engineering code
- Processing pipelines (Spark jobs)

## Example (E-commerce)
- Sentiment analysis job flipped:
  - Positive → Negative
  - Negative → Positive

## Example (Healthcare)
- Modified image normalization
- Corrupted feature extraction

## Key Insight
- Raw data remains clean
- Corruption occurs inside pipeline logic
- Harder to detect than data poisoning

---

# 4. Modeling Stage (Impact Layer)

## Role
- Consumes processed data
- Learns patterns blindly

## Outcome of Attacks
- Biased models
- Incorrect classifications
- Backdoor-triggered behaviors

## Key Insight
- Modeling is not the attack surface
- It reflects upstream compromise

---

# 5. Deployment Attacks

## Method
Intercept model during deployment process

## Weak Points
- CI/CD pipelines
- Model pull endpoints
- Lack of integrity checks

## Missing Protections
- No hash verification
- No signature validation
- Insecure deserialization

## Impact
- Trojaned models in production
- Code execution on serving infrastructure

---

# 6. Retraining Attacks (Online Poisoning)

## Method
Inject malicious data into feedback loops

## Example (E-commerce)
- Manipulated clickstream data
- Biased user feedback
- Gradual model drift

## Key Characteristics
- Slow accumulation
- Appears as normal behavior
- Difficult to detect

## Core Problem
System is designed to:
- Trust new data
- Adapt to changes

But cannot distinguish:
- Legitimate behavior shifts
- Random noise
- Adversarial manipulation

---

# Impact of AI Data Attacks

## Mild
- Biased outputs
- Reduced accuracy

## Severe
- Fully compromised models
- Hidden backdoors

## Critical
- Code execution via model files
- Infrastructure compromise

---

# Mapping to Security Frameworks

## OWASP Top 10 for LLMs

### LLM03: Training Data Poisoning
- Covers:
  - Data poisoning (collection, processing, retraining)
  - Most attacks in this category

### LLM05: Supply Chain Vulnerabilities
- Covers:
  - Tampered model artifacts
  - Compromised third-party data
  - Infrastructure weaknesses

---

## Google Secure AI Framework (SAIF)

### Key Areas

#### 1. Secure Design
- Strong system architecture
- Defined trust boundaries

#### 2. Secure Data Supply Chain
- Validate incoming data
- Protect retraining pipelines

#### 3. Secure Deployment
- Ensure model integrity
- Prevent code injection

#### 4. Secure Monitoring & Response
- Continuous anomaly detection
- Track data distribution changes

---

# Core Takeaways

- AI attacks target data, not just models
- Every pipeline stage is an attack surface
- Processing logic is a high-value target
- Retraining pipelines are the weakest trust boundary
- Model files can execute code, not just store weights
- Traditional perimeter security is insufficient
- Continuous monitoring is required to detect subtle attacks

Images:

<img width="1169" height="417" alt="image" src="https://github.com/user-attachments/assets/d71ca4f9-e0b2-45c5-98ee-c5bffce73538" />
[ Pipeline stage and corresponding attack type ]
