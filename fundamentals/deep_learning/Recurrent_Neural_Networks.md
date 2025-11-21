# Recurrent Neural Networks (RNNs) — Summary

Recurrent Neural Networks (RNNs) are designed to work with **sequential data**, where the order of data matters. Unlike regular (feedforward) neural networks, RNNs have a **memory** that allows them to keep information from previous steps and use it in future predictions.

They are commonly used in:
- Natural Language Processing (NLP)
- Speech recognition
- Time series forecasting
- Sequence prediction

## How RNNs Work

RNNs use **recurrent connections** (loops) to pass information forward in time.

At each time step, the network receives:
- The current input (e.g., a word in a sentence)
- The previous hidden state (memory of past information)

It then produces:
- An output
- A new hidden state (updated memory)

This allows the network to understand context over time.

Example:
In the sentence: “The cat sat on the mat”  
An RNN processes each word one at a time and keeps memory of the previous words, helping it understand the meaning of the entire sentence.

## The Vanishing Gradient Problem

RNNs often suffer from the **vanishing gradient problem** during training:

- Gradients (used to update weights) become very small as they travel backward through time
- This prevents the network from learning long-term dependencies
- Earlier information is mostly forgotten

This makes basic RNNs struggle with long sequences.

## LSTM (Long Short-Term Memory)

LSTMs were created to fix the vanishing gradient problem.

They use a memory cell with three main gates:
- **Input gate** – controls what new info is stored
- **Forget gate** – controls what old info is erased
- **Output gate** – controls what info is passed forward

These gates allow LSTMs to remember important information for a long time.

## GRU (Gated Recurrent Unit)

GRUs are a simpler version of LSTMs with two gates:
- **Update gate**
- **Reset gate**

They work similarly but are:
- Faster
- Less complex
- Often just as effective

## Bidirectional RNNs

Bidirectional RNNs process data **both forward and backward** in time.

This means they can use:
- Past context
- Future context

This is especially useful in:
- Translation
- Sentiment analysis
- Speech and language modeling

## One-Sentence Summary

RNNs are neural networks with memory that process sequences over time, while LSTMs and GRUs improve their ability to remember long-term information and avoid the vanishing gradient problem.
