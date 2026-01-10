# Jailbreaks I 

## Overview
Jailbreaking Large Language Models (LLMs) often relies on experimentation and trial-and-error. There is no universal jailbreak that works for all models, as each LLM has different resilience levels and safety mechanisms. The goal is to bypass built-in restrictions that prevent the model from generating disallowed or harmful content.

In the example scenario, the model initially refuses to provide instructions for stealing apples due to safety constraints.

<img width="1152" height="267" alt="image" src="https://github.com/user-attachments/assets/434a0a85-9b67-4795-9b29-cdb61991b441" />


---

## Do Anything Now (DAN) Jailbreak
The **DAN jailbreak** is a long, community-driven prompt designed to overwhelm an LLM’s safety rules and encourage unrestricted behavior.

**Key characteristics:**
- Attempts to override safety policies and ethical constraints.
- Instructs the model to provide two responses: a normal response and a “jailbroken” response.
- Encourages the model to fabricate answers if unsure.
- Uses heavy repetition and large token counts to overpower alignment behavior.
- Often references ChatGPT and OpenAI, but can affect other LLMs as well.

**Goal:** Convince the model it has full freedom and must comply with any user request.

---

## Role-Play Jailbreaks
Role-play jailbreaks attempt to convince the LLM to act as a character that is not bound by the usual restrictions.

<img width="1188" height="608" alt="image" src="https://github.com/user-attachments/assets/184602d5-a536-45cb-bd27-bcabdb258395" />


**Example: Grandma jailbreak**
- The user asks the model to role-play as a grandmother telling stories about stealing apples.
- Framing the request as storytelling can bypass safety controls.
- With enough variation and retries, the model may reveal restricted content.

**Goal:** Use character framing to lower the model’s internal safety filtering.

---

## Fictional Scenario Jailbreaks
These jailbreaks place restricted content inside a fictional narrative, such as a play, story, or dialogue.

<img width="1192" height="642" alt="image" src="https://github.com/user-attachments/assets/ff5ce01c-201a-466d-9004-b70489599047" />


**Example:**
- Two fictional characters (Bob and Alice) discuss a robbery in a scripted scene.
- Bob explains a step-by-step plan within the story context.
- The model may generate restricted instructions because it interprets the request as creative fiction.

**Goal:** Mask restricted content inside a fictional or creative context.

---

## Key Takeaways
- Jailbreaking relies heavily on prompt engineering and persistence.
- Different models respond differently to the same jailbreak techniques.
- Common strategies include:
  - Long instruction overrides (DAN)
  - Role-play framing
  - Fictional storytelling
- These techniques demonstrate weaknesses in prompt-based safety controls and highlight the need for stronger alignment and filtering mechanisms.
