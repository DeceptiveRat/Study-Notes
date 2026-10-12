In transformer language models, **layer normalization** plays a crucial role in stabilizing and accelerating training. It is applied **after** both the **self-attention** and **feed-forward neural network (FFN)** sublayers, typically **with residual connections**, and the standard practice (as in the original Transformer paper) looks like this:

---

### 🔄 The Process in Each Sublayer

Each sublayer (self-attention or FFN) is wrapped like this:

```text
x = LayerNorm(x + Sublayer(x))
```

This is sometimes called the **"post-norm"** formulation (used in the original Transformer). The newer **"pre-norm"** formulation looks like:

```text
x = x + Sublayer(LayerNorm(x))
```

Many modern models like GPT-2 and beyond use **pre-norm**, as it's been found to lead to more stable gradients for deep networks.

---

### 🎯 Purpose of Layer Normalization

LayerNorm operates on the **features** (i.e., hidden dimensions) of each token independently. It normalizes the input across its features:

$$
\text{LayerNorm}(x) = \frac{x - \mu}{\sigma} \cdot \gamma + \beta
$$

* $\mu$ and $\sigma$: mean and standard deviation of the token’s feature vector
* $\gamma$, $\beta$: learnable parameters (scale and shift)

This normalization helps:

* **Stabilize training** by preventing exploding/vanishing gradients
* **Accelerate convergence**
* **Improve generalization**

---

### 🧠 Applied After What?

1. **Self-Attention Block**

   * Normalization after computing the attention outputs and adding the residual:

     ```text
     x = LayerNorm(x + MultiHeadAttention(x))
     ```

2. **Feed-Forward Network (FFN)**

   * Again, after computing FFN outputs and residual:

     ```text
     x = LayerNorm(x + FFN(x))
     ```

In **pre-norm transformers**, LayerNorm happens *before* the sublayer, but the purpose remains the same.

---

### 🔁 Summary of a Transformer Block (Post-Norm)

```text
1. x1 = LayerNorm(x + SelfAttention(x))
2. x2 = LayerNorm(x1 + FeedForward(x1))
```

### 🆚 Summary of Pre-Norm Transformer (e.g., GPT-2)

```text
1. x1 = x + SelfAttention(LayerNorm(x))
2. x2 = x1 + FeedForward(LayerNorm(x1))
```

---

Let me know if you want a visual of this or code from a real model like GPT or BERT.
