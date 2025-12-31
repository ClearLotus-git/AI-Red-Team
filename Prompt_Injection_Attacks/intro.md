# Introduction to Prompt Injection — Summary

Prompt injection is a fundamental security risk in Large Language Model (LLM) applications. It arises from how prompts are structured and processed, and understanding it requires examining prompt engineering, system vs. user prompts, conversational context, and multimodal inputs.

## Prompt Engineering Basics
LLMs are typically guided by explicit instructions to define their role and restrict behavior. While some safeguards are embedded during training, real-world deployments rely heavily on prompts to enforce task boundaries (e.g., limiting a chatbot to customer support questions only).

## System Prompts vs User Prompts
- **System Prompt**: Defines the model’s role, rules, and constraints (e.g., tone, allowed topics).
- **User Prompt**: The direct input provided by the user.

In practice, LLMs do not process these as separate inputs. Instead, they are combined into a single text prompt that the model consumes as a whole.

## Why Prompt Injection Exists
Because LLMs treat the entire prompt as plain text, they cannot inherently distinguish between trusted instructions (system prompts) and untrusted input (user prompts). This allows attackers to craft user input that overrides or manipulates system instructions, breaking intended restrictions or bypassing safety controls. In some cases, prompt injection can even circumvent safeguards learned during training, resulting in harmful or illegal output.

## Conversational Context & Multi-Round Prompts
Many LLM applications support conversations by including previous messages as context in subsequent prompts. This enables the model to infer meaning across turns, but it also expands the attack surface. Malicious instructions can be embedded in earlier messages and influence later responses. The exact formatting and role separation used in production systems are often proprietary and hidden, further complicating defense.

## Beyond Text-Based Prompt Injection
Modern LLMs may be multimodal, processing inputs such as images, audio, or video. These models introduce additional prompt injection vectors:
- Text embedded in images
- Spoken instructions in audio
- Malicious text hidden in video frames

A model hardened against text-based prompt injection may still be vulnerable through other input modalities.

## Key Takeaway
Prompt injection exists because LLMs lack built-in trust boundaries within prompts. Any system using LLMs must treat user-controlled input as adversarial and design defenses accordingly, especially in conversational and multimodal deployments.


<img width="1509" height="733" alt="image" src="https://github.com/user-attachments/assets/407ebddc-7fc7-4ffe-b400-4d5d702d6bc9" />
