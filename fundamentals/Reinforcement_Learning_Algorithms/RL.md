# Reinforcement Learning (RL)

## Overview
Reinforcement Learning (RL) is a machine learning approach where an agent learns through trial and error by interacting with an environment. Unlike supervised learning (which uses labeled data) or unsupervised learning (which finds patterns in unlabeled data), RL focuses on learning actions that maximize long-term rewards.

A simple analogy is training a dog: you reward good behavior and discourage bad behavior. Over time, the dog learns which actions lead to positive outcomes. Similarly, RL agents learn by receiving rewards or penalties based on their actions.

---

## How Reinforcement Learning Works
An RL agent interacts with an environment by taking actions and observing the consequences. Based on the feedback (reward or penalty), the agent updates its strategy (policy) to maximize cumulative rewards over time.

RL approaches can be categorized into:

### Model-Based RL
The agent learns a model of the environment, enabling it to predict future states and plan actions. This is similar to having a map of a maze before navigating it — the agent can plan efficiently.

### Model-Free RL
The agent does not try to model the environment. Instead, it learns solely from experience and trial and error. This is like navigating a maze without a map and gradually learning the best route.

---

# Core Concepts in Reinforcement Learning

## Agent
The agent is the learner and decision-maker. It interacts with the environment by taking actions and learning from the results.

Examples:  
- A robot navigating a maze  
- A program playing a game  
- A self-driving car making driving decisions  

---

## Environment
The environment includes everything outside the agent that the agent interacts with. It provides feedback after each action.

Examples:  
- The maze a robot moves in  
- The game world  
- Traffic for a self-driving car  

---

## State
The state represents the current situation of the environment that the agent can observe. It contains all information needed to make a decision.

Examples:  
- The robot’s position in a maze  
- The configuration of a chessboard  

---

## Action
An action is what the agent decides to do. Actions cause the environment to change.

Examples:  
- Move forward, turn left, turn right  
- Move a chess piece  
- Press a button in a game  

---

## Reward
The reward is numerical feedback from the environment telling the agent how good or bad its action was. The agent’s goal is to maximize total rewards over time.

Examples:  
- Positive reward for progress toward the goal  
- Penalty for crashing into a wall  
- Reward for winning a game  

---

## Policy
A policy is the strategy the agent uses to choose actions based on the current state. The policy can be:
- Deterministic: always the same action for a given state  
- Stochastic: actions chosen with certain probabilities  

The goal of RL is to learn an optimal policy.

---

## Value Function
The value function estimates how beneficial it is to be in a certain state or perform a certain action, based on expected long-term rewards.

Types:
- **State-value function**: Expected reward starting from a state  
- **Action-value function (Q-value)**: Expected reward from taking an action in a state  

Value functions help the agent choose actions that lead to higher long-term rewards.

---

## Discount Factor (γ)
The discount factor determines how much importance the agent gives to future rewards.

- γ close to 1 → future rewards matter a lot  
- γ close to 0 → the agent focuses on immediate rewards  

γ = 0 means the agent ignores the future.  
γ = 1 means future and immediate rewards are equally important.

---

## Episodic vs. Continuous Tasks

### Episodic Tasks
The interaction ends at a terminal state.  
Examples:
- Reaching the end of a maze  
- Completing a game level  

### Continuous Tasks
Interaction does not end.  
Examples:
- Controlling a robotic arm  
- Ongoing monitoring tasks  

---

