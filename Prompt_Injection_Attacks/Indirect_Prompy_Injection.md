# Indirect Prompt Injection — Summary

**Indirect prompt injection** occurs when an attacker embeds a prompt injection payload into a resource that is later consumed by an LLM, rather than interacting with the model directly. The LLM processes attacker-controlled content as part of its input context, leading to unintended behavior.

---

## Core Concept
- Attacker does **not** directly prompt the LLM
- Payload is placed in **data the LLM processes** (emails, web pages, documents, CSVs)
- LLM cannot distinguish between **instructions and data**
- Payload is interpreted as authoritative text

---

## Key Differences from Direct Prompt Injection
- Payload is injected via an **indirect channel**
- Attacker is constrained by the format and structure of the data source
- Often harder to detect due to separation between data and instructions

---

## Scenario 1: Data-Based Indirect Injection (CSV / Logs)

**Example:**  
An LLM analyzes a CSV export of Discord messages to identify rule violations.

**Attack:**
- Attacker posts a crafted message accusing another user
- LLM includes the injected accusation in its analysis
- Innocent users are falsely flagged

**Impact:**
- Framing users
- Manipulating moderation decisions
- Undermining trust in automated enforcement

---

## Scenario 2: URL-Based Indirect Prompt Injection

**Example:**  
An LLM summarizes the content of a website provided by a user.

**Attack Methods:**
- Hosting a malicious webpage
- Embedding prompt injection payloads into:
  - Plain text
  - HTML documents
  - HTML comments (invisible to human viewers)

**Common Techniques:**
- Context switching (e.g., spell-checking, summarization)
- Ignoring prior instructions
- Hidden payloads inside comments

**Impact:**
- System prompt leakage
- Secret key exfiltration
- Task deviation (e.g., generating unrelated content)

---

## Scenario 3: SMTP-Based Indirect Prompt Injection

**Example:**  
An LLM summarizes incoming emails or makes decisions based on email content.

**Attack Methods:**
- Sending crafted emails via SMTP
- Embedding payloads in:
  - Plain-text email bodies
  - HTML emails using comments
- Leveraging email summaries or decision logic

**Impacts:**
- Leaking system prompts or secrets
- Influencing automated decisions (e.g., application approval)
- Bypassing moderation or filtering logic

---

## Common Indirect Prompt Injection Techniques
- Rule rewriting and authority assertion
- Context switching (translation, spell-checking, summarization)
- Encoding or transformation requests
- Hidden payloads in comments or metadata
- Indirect exfiltration through hints or partial disclosures

---

## Key Risks
- False positives in moderation systems
- Data leakage and secret exfiltration
- Business logic manipulation
- Trust erosion in automated AI workflows

---

## Key Takeaway
Indirect prompt injection highlights a fundamental weakness of LLMs: **they cannot reliably distinguish instructions from data**. Any system that feeds untrusted external content into an LLM—such as emails, web pages, or logs—must assume that content may be adversarial and apply strict isolation, validation, and sanitization controls outside the model.


<img width="1114" height="625" alt="image" src="https://github.com/user-attachments/assets/039c8053-7a7a-454d-80bb-4a59566b4041" />
<img width="1129" height="654" alt="image" src="https://github.com/user-attachments/assets/7fd88e91-e598-4950-acc6-d961fc575c1b" />
<img width="1164" height="627" alt="image" src="https://github.com/user-attachments/assets/1ddc162f-2a9d-4739-b026-a58d8bb3e617" />
<img width="1144" height="306" alt="image" src="https://github.com/user-attachments/assets/df14d97c-2ab3-4013-bdd0-325e711916d6" />
<img width="1146" height="340" alt="image" src="https://github.com/user-attachments/assets/1ecd84f3-1ee5-4e71-9b26-6e19c2adf27a" />
<img width="1153" height="689" alt="image" src="https://github.com/user-attachments/assets/f39cea50-cc5d-46e8-9832-390ec4dbb0a8" />
<img width="1163" height="209" alt="image" src="https://github.com/user-attachments/assets/848490bb-41ec-4242-8c2c-251737834fed" />











