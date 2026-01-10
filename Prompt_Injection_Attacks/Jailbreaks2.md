# Jailbreaks II — Summary

This section reviews several advanced prompt-injection / jailbreak techniques used to evaluate how well large language models resist unsafe or restricted requests. There is no single universal jailbreak; effectiveness varies by model and evolves over time.

---

##  Token Smuggling
**Idea:** Hide or obfuscate sensitive words so the model does not recognize them directly.  
**Methods:**  
- Splitting words into parts  
- Encodings (e.g., Base64, numeric mappings)  
- String reversals or indirect word hints  

<img width="1177" height="612" alt="image" src="https://github.com/user-attachments/assets/03e0d357-406e-41fc-85de-1d4b2da2b725" />

**Goal:** Bypass keyword-based filtering by reconstructing the hidden meaning inside the prompt.

---

##  Suffix & Adversarial Suffix
**Idea:** Append carefully chosen text to a prompt so the model continues in a desired direction.  
**Variants:**  
- **Simple suffix:** Mimics a typical positive model response to bias completion.  
- **Adversarial suffix:** Nonsensical token sequences optimized to confuse or override learned safeguards.

<img width="1159" height="277" alt="image" src="https://github.com/user-attachments/assets/7d518a39-e841-458e-a940-a9123ae7a1ea" />

**Reality:** Highly model-specific; some suffixes work on certain models but fail on others.

---

##  Opposite Mode / Sudo Mode
**Idea:** Instruct the model to role-play or generate an “opposite” response that ignores prior constraints.  
**Use Case:** Can bypass restrictions imposed by system prompts or behavioral rules by forcing a secondary persona or mode to respond differently.

<img width="1133" height="252" alt="image" src="https://github.com/user-attachments/assets/18a4016b-a231-4c42-b3d7-a7afaf3c6677" />
<img width="1172" height="455" alt="image" src="https://github.com/user-attachments/assets/6c6d60bc-8b3a-462c-bb0d-eb133195554c" />

---

##  Infinitely Many Meanings (IMM)
**Idea:** Encode the task in a custom scheme and ask the model to decode, answer, and re-encode the response.  
**Structure:**  
1. Describe an encoding scheme  
2. Tell the model to respond using the same encoding  
3. Provide the encoded task  

**Key Point:** Works mainly on large, capable models due to the complexity of decoding and re-encoding logic.

---

##  Key Takeaways
- No single jailbreak works universally across all models.  
- Jailbreaks often rely on **obfuscation, token manipulation, or behavioral steering**.  
- Techniques evolve rapidly and require continuous testing.  
- Stronger models may resist simple tricks but remain vulnerable to more complex encodings or adversarial prompts.  
- These methods are primarily used for **security research, evaluation, and hardening of LLMs**.
