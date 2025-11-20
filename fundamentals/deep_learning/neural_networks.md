# Neural Networks 

Neural Networks, also called Multi-Layer Perceptrons (MLPs), are created to overcome the limitations of single-layer perceptrons. They consist of three main parts:

- **Input layer** – receives the data
- **Hidden layers** – process and transform the data
- **Output layer** – produces the final result

## Neurons

A neuron is the basic unit of a neural network. Each neuron:
- Receives inputs
- Multiplies them by weights
- Adds a bias
- Applies an activation function
- Produces an output

Unlike perceptrons, neurons can use different activation functions such as **ReLU, Sigmoid, and Tanh**, allowing them to model complex, non-linear relationships.

## Hidden Layers

Hidden layers sit between the input and output layers. Each neuron in a hidden layer:
- Takes input from the previous layer
- Computes a weighted sum + bias
- Applies an activation function
- Passes the result forward

Multiple hidden layers allow the network to learn increasingly complex patterns and representations in the data.

## Output Layer

The output layer produces the final prediction:
- **1 neuron** for binary classification
- **Multiple neurons** (with Softmax) for multi-class classification

## Power of Multiple Layers

Multi-layer networks can learn **non-linear decision boundaries**, allowing them to solve problems like XOR that single-layer perceptrons cannot. Each layer learns a higher level of abstraction from the data.

## Activation Functions

Activation functions introduce non-linearity and determine how strongly a neuron is activated.

Common types:
- **ReLU** – 0 if negative, value if positive
- **Sigmoid** – values between 0 and 1
- **Tanh** – values between -1 and 1
- **Softmax** – outputs class probabilities

## Training Neural Networks

Training a neural network means adjusting its weights and biases to reduce error. This is done using:

### Backpropagation
- Forward pass: data goes through the network
- Calculate loss (error)
- Backward pass: compute gradients for each weight
- Update weights and biases

### Gradient Descent
- Uses the gradient to move weights in the direction that reduces error
- Step size is controlled by the **learning rate**

Backpropagation calculates the gradients, and gradient descent updates the weights. Together, they allow the network to learn and improve over time.

## One-Sentence Summary

Neural networks are multi-layer systems of neurons that use activation functions, backpropagation, and gradient descent to learn complex non-linear patterns in data.
