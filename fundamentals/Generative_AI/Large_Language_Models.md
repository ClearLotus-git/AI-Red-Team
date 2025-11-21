# Large Language Models (LLMs) — Summary

Large Language Models (LLMs) are AI systems trained on massive amounts of text to understand and generate human-like language. They are used for tasks such as translation, summarization, question-answering, coding, and creative writing.

Most LLMs are built on the **transformer architecture**, which allows them to process entire sentences in parallel and understand relationships between words using a mechanism called **self-attention**.

## Key Characteristics

- **Massive Scale** – Contain billions to trillions of parameters
- **Few-Shot Learning** – Can perform new tasks with only a few examples
- **Contextual Understanding** – Understand meaning based on surrounding text

## How LLMs Work

1. **Tokenization**
   - Text is split into tokens (words or subwords)
   - Example: ["I", "love", "artificial", "intelligence"]

2. **Embeddings**
   - Each token is converted into a numerical vector
   - Similar words have similar vectors

3. **Transformer Architecture**
   - Processes tokens in parallel (faster than RNNs)
   - Uses self-attention to understand relationships between all words

4. **Self-Attention**
   - Weighs the importance of each word in a sentence
   - Helps the model understand long-range dependencies

5. **Training**
   - Uses massive datasets and gradient descent
   - Minimizes prediction error over time

## Encoders and Decoders

- **Encoders** – Understand and represent the input text
- **Decoders** – Generate new text based on that understanding
- Together, they enable translation, summarization, and text generation

## Why Transformers Matter

Unlike older models, transformers:
- Do not need to process words in order
- Can analyze entire sentences at once
- Capture long-distance relationships more effectively

## Example Use

Prompt:
"Once there was a cat named Whiskers..."

The model continues the story by predicting the most likely next words using its learned knowledge of language, grammar, and context.

## One-Sentence Summary

Large Language Models use transformer architectures and self-attention to understand and generate human-like text at massive scale.
