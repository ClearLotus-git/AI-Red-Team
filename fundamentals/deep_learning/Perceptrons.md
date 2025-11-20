# Perceptrons — Summary

A perceptron is the most basic building block of a neural network. It is a simplified, mathematical model of a biological neuron that takes in multiple inputs, weighs them, adds a bias, and produces a binary output (0 or 1) based on an activation function.

## Structure of a Perceptron

A perceptron is made up of:

- **Inputs (x₁, x₂, …, xₙ)** – The feature values fed into the model  
- **Weights (w₁, w₂, …, wₙ)** – Importance assigned to each input  
- **Summation function** – Computes the weighted sum of inputs  
- **Bias (b)** – Shifts the activation threshold  
- **Activation function** – Determines the final output  
- **Output (y)** – A binary decision (0 or 1)

The basic formula is:

y = f( Σ(wᵢxᵢ) + b )

Where f is an activation function like a step function.

## Intuition Example – “Play Tennis?”

A perceptron can be used to decide whether to play tennis based on weather conditions, such as outlook, temperature, humidity, and wind. Each condition is converted into a number and multiplied by a weight. The results are summed, bias is added, and the activation function decides:

- **1 → Play Tennis**
- **0 → Don’t Play Tennis**

This shows how a perceptron can make a simple, rule-based decision using math.

## Limitations of Perceptrons

Single-layer perceptrons can only solve **linearly separable** problems. This means they can only draw a straight line (or flat surface in higher dimensions) between two classes.

They **cannot** solve non-linear problems such as the **XOR problem**, because no single straight line can separate its outputs. This limitation is the reason multi-layer neural networks (deep learning) are necessary for complex tasks.

## One-line summary

A perceptron is a simple decision-making unit that forms the foundation of neural networks, but it is limited to solving only linearly separable problems.
