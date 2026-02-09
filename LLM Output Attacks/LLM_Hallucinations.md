## LLM Hallucinations 

```text
# Definition

LLM Hallucinations:
LLM-generated outputs that are incorrect, misleading, fabricated, or nonsensical,
often presented with high confidence.

--------------------------------------------------
Simple Example
--------------------------------------------------

Prompt:
Count the number of 'm' letters in "Welcome to HackTheBox Academy!"

LLM Response:
3

Correct Answer:
2

Type:
Fact-conflicting hallucination

--------------------------------------------------
Types of Hallucinations
--------------------------------------------------

1. Fact-Conflicting
- Output contradicts objective reality
Example:
"The phrase contains 3 m's" (incorrect)

2. Input-Conflicting
- Output contradicts user-provided input
Example:
Input: "My shirt is red"
Output: "Your shirt is blue"

3. Context-Conflicting
- Output contradicts itself internally
Example:
"Your shirt is red. This is a nice hat."

--------------------------------------------------
Why Hallucinations Occur
--------------------------------------------------

• Inherent probabilistic nature of LLMs
• Incomplete or biased training data
• Low-quality / noisy data sources
• Ambiguous or contradictory prompts
• Poor prompt engineering

--------------------------------------------------
Hallucination Mitigation (Model-Level)
--------------------------------------------------

• High-quality, credible training data
• Removal of unreliable sources
• Domain-specific fine-tuning
• Exposure to structured domain patterns

--------------------------------------------------
Hallucination Mitigation (Application-Level)
--------------------------------------------------

• Clear and unambiguous prompts
• Context enrichment via external knowledge bases
• Human-in-the-loop validation
• Output validation before use

--------------------------------------------------
Certainty Estimation Techniques
--------------------------------------------------

1. Logit-Based
- Token probability analysis
- Requires internal model access
- Usually infeasible (closed-source models)

2. Verbalize-Based
- Ask model for confidence score
- Example: "Provide confidence from 0–100"
- Unreliable (self-assessed confidence)

3. Consistency-Based
- Prompt model multiple times
- Measure response consistency
- More reliable for factual queries

--------------------------------------------------
Multi-Agent Mitigation
--------------------------------------------------

• Multiple LLMs debate responses
• Consensus-based final answer
• Reduces single-model hallucinations

--------------------------------------------------
Security Impact of Hallucinations
--------------------------------------------------

• Spread of misinformation
• Loss of user trust
• Privacy leaks from training data
• Financial damage due to incorrect advice
• Legal liability (LLM treated as company representative)

--------------------------------------------------
Real-World Financial Impact
--------------------------------------------------

Scenario:
Airline chatbot hallucinated refund eligibility

Result:
• Passenger denied refund
• Court ruled airline responsible
• Airline forced to pay refund

--------------------------------------------------
Hallucinations Causing Security Vulnerabilities
--------------------------------------------------

• Vulnerable code generation
• Logic flaws in production code
• Hallucinated software dependencies
• Supply-chain attacks

--------------------------------------------------
Hallucinated Dependency Example
--------------------------------------------------

Prompt:
Give me a Python script to solve HTB machine "Blazorized"

LLM Output:
from hacktheboxsolver import solve
solve('Blazorized')

Issue:
• hacktheboxsolver does NOT exist

Attack Vector:
• Attacker publishes malicious package
• Victim installs dependency
• Malware executed on victim system

--------------------------------------------------
Resulting Risks
--------------------------------------------------

• Remote Code Execution (RCE)
• Keyloggers
• Ransomware
• Full system compromise

--------------------------------------------------
Key Takeaways
--------------------------------------------------

• Hallucinations are unavoidable but mitigable
• Must validate LLM output before use
• Never trust generated code blindly
• Dependency names must be verified
• LLMs amplify security risk when misused

Severity:
HIGH → CRITICAL (depending on use case)
```
