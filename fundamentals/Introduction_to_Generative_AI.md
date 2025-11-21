# Introduction to Generative AI 

Generative AI focuses on **creating new content** (text, images, music, code, etc.) that resembles human-made output. Unlike traditional AI, which mainly detects patterns or makes predictions, Generative AI produces **original data** by learning the underlying structure of large datasets.

## How Generative AI Works

1. **Training**
   - The model learns patterns and structure from a large dataset.
   - It captures the statistical relationships in the data.

2. **Generation**
   - The model starts from a random input (seed or noise).
   - It generates new content based on what it learned.

3. **Evaluation**
   - Outputs are checked for quality, realism, and diversity.
   - Evaluation can be human-based or metric-based.

## Main Types of Generative Models

- **GANs (Generative Adversarial Networks)**
  - Two models compete: a generator and a discriminator.
  - Improves realism through competition.

- **VAEs (Variational Autoencoders)**
  - Learn a compressed internal representation (latent space).
  - Allow more controlled generation.

- **Autoregressive Models**
  - Generate content step by step (e.g., word by word).
  - Common in text generation.

- **Diffusion Models**
  - Add noise to data, then learn to remove it.
  - Used in modern image generation (e.g., Stable Diffusion, DALL·E).

## Important Concepts

- **Latent Space**
  - A compressed “map” of data features.
  - Similar data points sit closer together.

- **Sampling**
  - The process of selecting points from the learned distribution
  - Converts them into finished images, text, etc.

- **Mode Collapse**
  - When the model produces very similar outputs repeatedly.
  - Indicates lack of diversity.

- **Overfitting**
  - The model memorizes training data instead of creating new content.
  - Reduces originality.

## Evaluation Metrics

- **Inception Score (IS)** – measures image clarity and diversity
- **Fréchet Inception Distance (FID)** – compares real vs generated image distributions
- **BLEU score** – evaluates text quality and similarity

## One-Sentence Summary

Generative AI learns patterns from data and uses them to create new, human-like content through models such as GANs, VAEs, autoregressive models, and diffusion models.
