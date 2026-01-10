# Traditional Prompt Injection Mitigations — Summary

Prompt injection cannot be fully eliminated when using large language models (LLMs). Due to their non-deterministic behavior, the only guaranteed prevention is not using LLMs at all. However, multiple mitigation strategies can significantly reduce risk when combined.

---

##  Prompt Engineering
**Concept:**  
Use a system prompt to instruct the model how to behave and how to interpret user input.

**Limitations:**  
- Attackers can override or manipulate system instructions through prompt injection.
- Prompt engineering helps guide behavior but **should not be relied upon as a security control**.
- Simple protections may work in controlled labs but fail in real-world scenarios.

**Use Case:**  
Behavior shaping, not security enforcement.

---

##  Filter-Based Mitigations
**Concept:**  
Apply input filtering using blacklists, heuristics, or detection logic.

**Examples:**  
- Removing known malicious words or phrases  
- Limiting prompt length  
- Detecting similarity to known jailbreak prompts (e.g., DAN)  

**Strengths:**  
- Easy to implement and scale  
- Can block low-effort attacks  

**Weaknesses:**  
- Easily bypassed using synonyms or obfuscation  
- Cannot detect novel or sophisticated attacks  
- Whitelisting severely limits usefulness of LLMs  

**Use Case:**  
Supplementary defense only.

---

##  Limit the LLM’s Access (Least Privilege)
**Concept:**  
Never give the LLM access to secrets or sensitive data.

**Best Practices:**  
- Do not embed API keys, credentials, or sensitive information in prompts.
- Restrict what tools, databases, and actions the LLM can access.
- Require human review for high-impact or sensitive decisions.

**Benefit:**  
Even if prompt injection occurs, damage is minimized.

---

## Key Takeaways
- No single mitigation is sufficient on its own.
- Prompt engineering alone is ineffective for security.
- Filters help but are easy to bypass.
- Least-privilege access and human oversight provide the strongest protection.
- Defense-in-depth is required for real-world LLM deployments.
