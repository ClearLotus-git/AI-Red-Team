
The effectiveness of evasion attacks depends on the model’s robustness to adversarial inputs.

---

### **Model Theft (Model Extraction)**
Models are valuable intellectual property due to:
- High training cost
- Proprietary fine-tuning

**Model extraction attacks** aim to reconstruct a copy of the model by analyzing inputs and outputs.

**Consequences:**
- Intellectual property loss
- Financial damage
- Enabling further attacks (e.g., poisoning, evasion)

Traditional security failures (e.g., insecure storage or transmission) can also lead to model theft.

---

## Attacker Tactics, Techniques & Procedures (TTPs)

### **Behavior Analysis**
- Send large volumes of inputs
- Analyze outputs to understand model behavior
- Identify decision boundaries and weaknesses

---

### **Behavior Manipulation**
- Craft prompts to coerce unintended behavior
- Techniques include prompt injection and jailbreaks

**Potential outcomes:**
- Sensitive data disclosure
- Harmful or illegal content generation
- Reputational and financial damage

---

### **Model Extraction**
- Perform strategic, large-scale querying
- Use collected input-output pairs to train a substitute model
- Apply adaptive querying to accelerate extraction

Extracted models can be used to:
- Replicate proprietary systems
- Craft advanced adversarial attacks
- Evade detection mechanisms

---

## Key Takeaway
Attacks on the model component threaten the **integrity, confidentiality, and reliability** of generative AI systems. Effective defense requires protecting training pipelines, hardening inference behavior, and preventing unauthorized model access or replication.

<img width="2576" height="1332" alt="image" src="https://github.com/user-attachments/assets/a258fa51-b38b-40aa-b90a-2d32e24f5d05" />
