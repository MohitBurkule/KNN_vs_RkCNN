# Attention is Soft KNN

Visualizing the explicit mathematical equivalence between Transformer Attention and Nadaraya-Watson Kernel Regression.


https://github.com/user-attachments/assets/96be729d-93d7-4286-8298-abcbfb216f04



## Live Demo

Check out the live visualization here: [https://mohitburkule.github.io/Attention_is_KNN/](https://mohitburkule.github.io/Attention_is_KNN/)

## About

This project is a single-file HTML application that visualizes how the Attention mechanism in Transformers works, by drawing parallels to Kernel Regression (KNN).

It features:
- Interactive visualization where you can drag a "Query" ring to see how it absorbs colors ("Values") from nearby "Keys".
- Real-time calculation of Attention Weights.
- Mathematical explanation and side-by-side comparison of Kernel Regression and Transformer Attention formulas.

## Why is this useful?

Understanding modern Large Language Models (LLMs) can be daunting due to their complexity. However, at their core, the Attention mechanism—the engine of Transformers—is actually a differentiable version of a classic algorithm: **Kernel Density Estimation** or **Nadaraya-Watson Kernel Regression**.

By visualizing this link, we demystify "Attention" and ground it in well-understood statistical concepts. It shows that LLMs are effectively performing a sophisticated lookup (or "soft dictionary search") in a high-dimensional space. This intuition is crucial for students and researchers trying to grasp the fundamental operations of Deep Learning models without getting lost in the jargon.

## The Equivalence: Attention = Soft KNN

The core insight is that the attention operation is mathematically identical to a weighted average estimator, where the weights are determined by similarity.

### 1. Kernel Regression (1964)
In classical non-parametric regression, to predict a value $y$ for a new query point $x$, we look at existing data points $x_i$ and calculate a weighted average of their values $y_i$. The weights depend on how similar (or close) $x$ is to $x_i$, determined by a kernel function $K$.

$$y = \frac{\sum K(x, x_i)y_i}{\sum K(x, x_i)}$$

### 2. Transformer Attention (2017)
In Transformers, to compute a new representation (Context) for a token (Query $Q$), we compare it against other tokens (Keys $K$) to retrieve information (Values $V$).

$$\text{Attn}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d}}\right)V$$

### The Mapping

| Concept | Kernel Regression Term | Transformer Attention Term |
| :--- | :--- | :--- |
| **Search Input** | Target $x$ | Query $Q$ |
| **Database** | Examples $x_i$ | Keys $K$ |
| **Content** | Labels $y_i$ | Values $V$ |
| **Similarity** | Kernel $K(x, x_i)$ | Dot Product $QK^T$ |
| **Normalization** | Denominator $\sum K(...)$ | Softmax |
| **Result** | Smoothed $y$ | Context Vector |

In essence, **Attention is just a database lookup where you get a blend of results based on relevance, rather than a single exact match.**

## How to Run Locally

Simply open the `index.html` file in your web browser.

```bash
# Clone the repository
git clone <repository-url>

# Open index.html
open index.html # On macOS
xdg-open index.html # On Linux
start index.html # On Windows
```

## Technologies Used

- HTML5 Canvas
- Tailwind CSS
- MathJax (for rendering equations)
