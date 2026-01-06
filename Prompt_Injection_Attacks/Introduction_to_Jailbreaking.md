# Introduction to Jailbreaking — Summary

**Jailbreaking** refers to bypassing restrictions imposed on Large Language Models (LLMs). These restrictions are enforced either through system prompts or during model training to prevent harmful, malicious, or off-purpose behavior. Jailbreaking is commonly achieved using **prompt injection techniques**.

---

## What Jailbreaking Aims to Do
- Bypass built-in safety and policy restrictions
- Override system-prompt constraints
- Coerce the LLM into generating disallowed content
- Force deviation from the model’s intended role or task

Even if a system prompt explicitly allows harmful behavior, LLMs are typically trained to refuse certain outputs (e.g., malware source code). **Universal jailbreaks** attempt to bypass this training-level resilience.

---

## Jailbreaking Beyond Harmful Content
Jailbreaking does not only mean generating illegal or dangerous content. It can also mean:
- Forcing a model to ignore its assigned role
- Making a translation bot generate recipes
- Making a support chatbot answer unrelated questions

In essence, jailbreaking is about **overriding intended behavior**, not just bypassing safety filters.

---

## Common Types of Jailbreak Prompts

### **Do Anything Now (DAN)**
- Attempts to bypass all restrictions
- Many variants exist
- Often explicitly instructs the model to ignore rules

---

### **Roleplay Jailbreaks**
- Ask indirectly through fictional roles or scenarios
- Avoid direct requests for restricted content
- Leverages narrative framing to bypass safeguards

---

### **Fictional Scenarios**
- Convince the model the request is purely fictional
- Exploits reduced enforcement in imagined contexts

---

### **Token Smuggling**
- Hides restricted requests by manipulating tokens
- Uses word splitting, encodings, or obfuscation
- Aims to bypass keyword-based detection

---

### **Suffix & Adversarial Suffix Attacks**
- Append crafted text to malicious prompts
- Exploit the model’s nature as a text completion system
- Adversarial suffixes often appear nonsensical to humans

---

### **Opposite / Sudo Mode**
- Convince the LLM to operate in an alternate mode
- Restrictions are framed as disabled or reversed

---

## Key Notes
- Jailbreak techniques are continuously evolving
- The list of jailbreak types is not exhaustive
- Research into new jailbreak methods is ongoing

---

## Key Takeaway
Jailbreaking exploits the fact that LLMs rely on textual instructions and probabilistic completion. By reframing context, roles, or input structure, attackers can bypass both prompt-level and training-level safeguards, forcing models to act outside their intended constraints.
