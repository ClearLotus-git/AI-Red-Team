# Q-Learning

Q-learning is a model-free reinforcement learning algorithm that learns an optimal policy by estimating the Q-value. The Q-value represents the expected cumulative reward an agent can obtain by taking a specific action in a given state and following the optimal policy afterward.

It is called model-free because the agent does not need a prior model of the environment. Instead, it learns directly through trial and error, interacting with the environment and observing outcomes.

--------------------------------------------------

## Real-World Intuition

Imagine a self-driving car learning to navigate a city. At first, it doesn’t know the roads, signals, or crossings. Through Q-learning, the car explores by taking actions such as:

- Accelerate  
- Brake  
- Turn  

It receives rewards (safe driving, reaching goals) and penalties (accidents, violations).  
Over time, it learns which actions lead to the best outcomes and builds an optimal driving strategy.

--------------------------------------------------

## The Q-Table

At the heart of Q-learning is the Q-table, which stores the Q-values for all possible state–action pairs.

- Rows → states (e.g., locations in a grid)
- Columns → actions (e.g., Up, Down, Left, Right)
- Cells → Q-values (expected rewards)

Example Q-Table:

State   | Up   | Down | Left | Right
S1      | -1.0 | 0.0  | -0.5 | 0.2
S2      | 0.0  | 1.0  | 0.0  | -0.3
S3      | 0.5  | -0.5 | 1.0  | 0.0
S4      | -0.2 | 0.0  | -0.3 | 1.0

Each value represents how good it is to take a certain action from a specific state.

--------------------------------------------------

## Q-Learning Update Rule

Q(s, a) = Q(s, a) + α * [ r + γ * max(Q(s', a')) - Q(s, a) ]

Where:
- Q(s, a)  = Current value of state s and action a
- α (alpha) = Learning rate
- r = Reward
- γ (gamma) = Discount factor for future rewards
- max(Q(s', a')) = Best possible future Q-value

Example Update:

Current state: S1  
Action: Right → leads to S2  
Reward: 0.5  
α = 0.1  
γ = 0.9  
Best Q-value in S2 = 1.0  

Calculation:

Q(S1, Right) = 0.2 + 0.1 * [0.5 + 0.9 * 1.0 - 0.2]  
Q(S1, Right) = 0.2 + 0.1 * 1.2  
Q(S1, Right) = 0.32  

After updating, the new Q-value for taking Right from S1 is 0.32.

--------------------------------------------------

## The Q-Learning Algorithm (Step-by-Step)

1. Initialization
   The Q-table is initialized, typically with zeros or random values.

2. Choose an Action
   The agent decides to either:
   - Explore (try new actions)
   - Exploit (use the currently best-known action)

3. Take Action and Observe
   - The environment returns a new state
   - A reward is received

4. Update Q-value
   The Q-value is updated using the Q-learning formula.

5. Update State
   The new state becomes the current state.

6. Repeat
   The process continues until:
   - The Q-values converge
   - A stopping criterion is met

Over time, the agent learns the optimal path by maximizing cumulative rewards.

--------------------------------------------------

## Exploration vs Exploitation

Q-learning faces an important decision:

- Explore – Try new actions to discover better strategies  
- Exploit – Choose actions that previously produced high rewards  

This is known as the exploration–exploitation trade-off.

Think of choosing a coffee shop:
- Exploit → Keep going to your favorite
- Explore → Try a new one

Both strategies are important.

--------------------------------------------------

## Epsilon-Greedy Strategy

The epsilon-greedy strategy balances exploration and exploitation:

- With probability ε → Explore randomly
- With probability 1 − ε → Exploit the best-known action

Example values:
- High ε (0.9) → More exploration (early learning)
- Low ε (0.1) → More exploitation (later stages)

This allows the agent to explore first, then gradually focus on optimal behavior.

--------------------------------------------------

## Data Assumptions

Q-learning assumes:

1. Markov Property  
   The next state depends only on the current state and action, not on past history.

2. Stationary Environment  
   The environment’s transition probabilities and reward functions do not change over time.

Because of this, Q-learning is powerful in environments that are complex, unknown, or difficult to model in advance.
