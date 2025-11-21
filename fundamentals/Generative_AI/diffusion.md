# Diffusion Models

Diffusion models are a class of generative models that create high-quality images, audio, and other data by **gradually adding noise and then learning how to remove it**. Unlike GANs or VAEs, diffusion models learn the data distribution through a step-by-step noising and denoising process.

---

## How Diffusion Models Work

To generate an image from a text prompt (e.g., “a cat in a hat”), diffusion models combine a **text encoder** with a **denoising network**:

1. **Text Encoding**  
   The prompt is converted into a high-dimensional vector (embedding) using a model like a Transformer or CLIP. This vector contains the meaning of the text and is used to guide image generation.

2. **Conditioned Denoising**  
   During denoising, the model removes noise in a way that moves the image toward matching the text embedding. The loss function includes a term to measure alignment between the image and text.

3. **Sampling**  
   Generation begins with pure noise. At each step, the model removes some noise while using the text embedding as guidance.

4. **Final Output**  
   After many steps, the process produces a clear image that matches the text prompt.

---

## Forward Process: Adding Noise

Noise is gradually added to the data over many steps:

```python
x_t = q(x_t | x_{t-1})
```

Where:

`x_0` = original data

`x_T` = completely noisy data

Each step adds a small amount of noise

This follows the Markov Property — each step only depends on the previous one.

Reverse Process: Removing Noise

A neural network learns to remove the noise:

x_{t-1} = p_θ(x_{t-1} | x_t)


The network is trained to predict the noise using MSE:

L = E[||ε - ε_pred||^2]


Where:

ε = actual noise

ε_pred = predicted noise

Noise Schedule

The amount of noise added at each step is controlled by:

β_t = β_min + (t / T) * (β_max - β_min)


A good schedule helps the model learn smoother and more accurate denoising.

Denoising Network

The denoising network (usually a CNN or Transformer) takes a noisy image x_t and predicts the noise to remove. Its architecture determines:

Output quality

Convergence speed

Final image resolution

Training Steps

Initialize model parameters

Add noise to real images

Predict noise at each timestep

Calculate loss (MSE)

Update parameters

Repeat until convergence

Sampling (Generation Process)

To generate new data:

x_0 = p_θ(x_0 | x_T)


Steps:

Start with random noise x_T

Iteratively denoise from T → 1

Final result x_0 is the generated image

Data Assumptions

Markov Property – Each step depends only on the previous step

Static Distribution – Training data doesn’t change

Smoothness – Small changes produce small result changes
