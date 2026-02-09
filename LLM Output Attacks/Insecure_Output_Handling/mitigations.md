## Insecure Output Handling – Mitigations Summary

```text
# Core Principle

Treat ALL LLM-generated output as untrusted data.
LLM output must be handled exactly like user input.

--------------------------------------------------
Root Cause of Vulnerabilities
--------------------------------------------------

• LLM output inserted directly into:
  - HTML → XSS
  - SQL queries → SQL Injection
  - System commands → Code Injection
  - Function calls → RCE / Excessive Agency

• No validation, sanitization, or escaping
• Prompt-based restrictions used as access control

--------------------------------------------------
Primary Prevention Measures
--------------------------------------------------

1. Output Validation
- Validate format, type, length, and structure
- Reject unexpected or malformed output

2. Output Sanitization & Escaping
- HTML-encode LLM output before rendering in browsers
- Escape special characters
- Strip dangerous constructs where possible

3. Context-Specific Handling
- HTML → Apply HTML encoding
- SQL → Use prepared statements / parameterized queries
- OS commands → Never pass raw LLM output
- File paths → Enforce allowlists

--------------------------------------------------
LLM Access Control Model
--------------------------------------------------

Assumption:
ALL data and functions accessible to the LLM are PUBLIC

Implications:
• Prompt engineering ≠ access control
• “Admin-only” prompts are ineffective
• LLM cannot enforce authorization boundaries

Mitigation:
• Do NOT expose sensitive data to LLMs
• Do NOT expose privileged functions
• Enforce authorization outside the LLM

--------------------------------------------------
Access Control Best Practices
--------------------------------------------------

• Implement access control in backend logic
• Enforce permissions before invoking LLM features
• Separate high-privilege and low-privilege workflows
• Never rely on system prompts for security decisions

--------------------------------------------------
Hardening Measures
--------------------------------------------------

1. Sandboxing
- Execute LLM-generated code in isolated containers
- Restrict filesystem, network, and process access

2. Least Privilege
- Run execution environments with minimal permissions
- No root access
- Read-only filesystems where possible

3. Defense in Depth
- Combine validation + access control + sandboxing
- Assume LLM output may be malicious

--------------------------------------------------
Code Injection Specific Mitigations
--------------------------------------------------

• Never execute LLM output directly
• Use allowlists for commands
• Avoid shell execution entirely
• Prefer APIs over command execution

--------------------------------------------------
Key Takeaways
--------------------------------------------------

• LLMs are NOT trusted components
• Output handling vulnerabilities mirror classic injections
• Prompt engineering is NOT a security boundary
• Backend controls must enforce security
• Sandboxing limits blast radius of failures

Security Goal:
Reduce likelihood AND impact of exploitation
```

