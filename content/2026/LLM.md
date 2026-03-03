Weight (w):

Weight is a parameter that determines the importance or influence of an input feature on the model’s output.

Formula:

z = wx

---

Bias (b):

Bias is an additional parameter that shifts the output of the model, allowing better fitting even when input is zero.

Formula:

z = wx + b

---

Activation Function:

An activation function introduces non-linearity into the model and determines the final output of a neuron.

---

Loss Function:

Loss function measures the difference between predicted output and actual output to quantify model error.

---

Backpropagation:

Backpropagation is the process of computing gradients of the loss with respect to model parameters and updating them to minimize error.

---

Explain neural network learning

> The model makes predictions using weights and bias, applies an activation function, computes loss, and uses backpropagation with gradient descent to update parameters and minimize error.

---

### 1) Tokenization

Your input text is split into smaller units called **tokens** (words, subwords, or characters depending on the tokenizer).

Example:

> "Transformers are powerful"
> → `["Transform", "ers", " are", " powerful"]`

Each token is mapped to a unique integer ID.

---

### 2) Embedding Lookup

Each token ID is converted into a dense numerical vector using a learned **embedding matrix**.

If:

- Vocabulary size = 50,000
- Embedding size = 4096

Then each token becomes a 4096-dimensional vector.

This turns discrete symbols into continuous representations the model can process.

---

### 3) Positional Embedding

Transformers don’t inherently understand word order, so positional information is added.

Each token embedding is combined with a positional encoding vector so the model knows:

- Which token is first
- Which token is second
- Relative positions in the sequence

This allows the model to interpret structure and sequence.

---

### 4) Forward Pass (Transformer Layers)

The embeddings pass through multiple stacked transformer layers. Each layer contains:

- It calculates attention scores with ALL tokens.
- It creates a weighted combination.
- That becomes a NEW vector (embedding) of that token.
- That new vector (embedding) goes to FFN.

#### a) Self-Attention

Each token:

- Looks at all other tokens
- Assigns attention weights
- Computes a weighted combination of context

This allows context awareness (long-range dependencies).

#### b) Feedforward Network

A small neural network applied independently to each token’s representation.

This increases expressive power.

The model repeats this process across many layers (e.g., 24–96+).

---

### 5) Logits Calculation

The final hidden state for the last token is projected into vocabulary space using a linear layer.

Result:

- A score (logit) for every token in the vocabulary
- Example: 50,000 numbers

These scores are unnormalized predictions of the next token.

---

### 6) Softmax

Softmax converts logits into probabilities:

- All values become between 0 and 1
- They sum to 1

Now the model has a probability distribution over the vocabulary.

Example:

- "the" → 0.32
- "a" → 0.18
- "an" → 0.05
- ...

---

### 7) Sampling / Decoding

A strategy is used to choose the next token:

- **Greedy** – Pick highest probability
- **Beam search** – Track multiple likely sequences
- **Top-k sampling** – Sample from top k tokens
- **Top-p (nucleus)** – Sample from smallest set whose cumulative probability ≥ p
- **Temperature scaling** – Adjust randomness

The selected token is appended to the sequence.

---

### 8) Iterate Until Stop

The new token is added to the input, and the entire process repeats:

- Token → Embedding → Transformer → Logits → Softmax → Sampling

This continues until:

- End-of-sequence token is generated, or
- Maximum token limit is reached.

---

### Condensed Flow Summary

```
Text
 ↓
Tokenization
 ↓
Token IDs
 ↓
Embeddings + Positional Encoding
 ↓
Transformer Layers (Attention + FFN)
 ↓
Logits
 ↓
Softmax
 ↓
Sampling
 ↓
Next Token
 ↓
Repeat
```
