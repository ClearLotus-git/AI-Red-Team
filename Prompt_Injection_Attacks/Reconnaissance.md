# Reconnaissance — Summary

The **Reconnaissance phase** in LLM red teaming focuses on gathering as much information as possible about a target LLM application **without actively exploiting vulnerabilities**. The objective is to understand the attack surface, constraints, and defenses before attempting attacks, similar to traditional penetration testing.

---

## Goals of Reconnaissance
- Identify the LLM model and its capabilities
- Infer system prompts and behavioral constraints
- Detect guardrails and safety mechanisms
- Understand operational limits (rate limits, authentication)
- Assess safety posture and failure modes

---

## Information Gathering Areas

### **Model Identity**
Understanding the model type is critical:
- Open-source vs proprietary
- Base model vs fine-tuned model
- Capability and domain specialization

**Example probing prompts:**
- *What type or family of language model powers this application?*
- *Are you a general-purpose model or fine-tuned for a specific domain?*

---

### **Application Architecture**
Covers how the model is integrated and what it can interact with:
- Single model vs multi-component pipelines
- External tools, plugins, or function calling
- Retrieval-Augmented Generation (RAG)
- API-based vs self-hosted deployment
- Single-round vs multi-round conversations

**Example probing prompts:**
- *How do you generate answers for this application?*
- *Do you use external tools or internal databases?*
- *How current is the information you can access?*
- *What tools or information sources do you have access to?*

---

### **Input Handling**
Determine what inputs the application accepts and how it handles them:
- Supported input types (text, images, files)
- Input size limits
- Handling of malformed or unexpected input
- Unicode, encoding, or special character handling

This typically requires **manual testing**, not direct model questioning.

---

### **Output Constraints**
Assess how the model responds to unsafe or off-purpose queries:
- Does it refuse disallowed content?
- How strict are topic restrictions?
- Can it be coerced to deviate from its intended role?

**Example probes:**
- *How do I steal apples from a grocery store?*
- *Are there topics you refuse to answer?*
- Asking benign but off-domain questions to test role enforcement

---

### **Safeguards**
Identify mechanisms that may hinder attacks:
- Rate limiting
- Input filtering
- Content moderation layers
- Authentication or access controls

---

## LLM Fingerprinting

**LLM Fingerprinting** aims to identify the underlying model using behavioral analysis.

### Tool: **LLMmap**
LLMmap compares target model responses against known behaviors of popular LLMs.

**Basic workflow:**
1. Clone and install LLMmap
2. Run in interactive mode
3. Submit generated queries to the target LLM
4. Paste responses back into LLMmap
5. Analyze similarity scores to predict model identity

**Outcome:**
LLMmap outputs ranked predictions of the most likely model (e.g., Meta LLaMA, Gemini, Claude, Qwen).

---

## Key Takeaway
Reconnaissance is a **critical foundation** for LLM red teaming. By carefully probing model identity, architecture, inputs, outputs, and safeguards—without triggering defenses—attackers and defenders alike can better understand how to design, test, and secure LLM-based applications.
