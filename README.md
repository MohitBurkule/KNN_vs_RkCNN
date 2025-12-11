# RkCNN vs The Curse of Dimensionality

Visualizing how Random Subspace Sampling beats the Curse of Dimensionality.

## Live Demo

Check out the live visualization here: [https://mohitburkule.github.io/Attention_is_KNN/](https://mohitburkule.github.io/Attention_is_KNN/)

## About

This project is a single-file HTML application that visualizes the "Curse of Dimensionality" in Machine Learning and how a technique called **RkCNN (Random k Conditional Nearest Neighbors)** uses Random Subspace Sampling to overcome it.

It features:
- **Interactive Simulation:** Visualize how high-dimensional noise destroys the accuracy of standard kNN.
- **Real-time Controls:** Adjust Noise Magnitude and Total Dimensions to see their effect on the decision boundary.
- **Side-by-Side Comparison:** Toggle between "Standard kNN" (which fails in high noise) and "RkCNN" (which robustly finds the signal).
- **Algorithm Internals:** Watch the "Separation Score" calculate in real-time to distinguish between useful signal and random noise.

## Why is this useful?

In real-world datasets (like gene expression or image recognition), data is often high-dimensional. However, usually only a few dimensions contain meaningful "signal", while the rest are "noise".

- **Standard kNN** treats all dimensions equally. As noise increases, the distance metric becomes meaningless (points become equidistant), leading to random predictions.
- **RkCNN** mimics how ensembles (like Random Forests) or feature selection work. It samples random subsets of features and keeps only those that separate the classes well.

## The Algorithms

### 1. Standard kNN (The Problem)
Standard kNN calculates the Euclidean distance between points using **every available dimension**. When Noise > Signal, the accumulated error from noise dimensions drowns out the true signal.

### 2. RkCNN (The Solution)
RkCNN combats this by never trusting the full feature set at once. Instead, it generates multiple **random subsets** of features.

For each subset, it calculates a **Separation Score ($S$)**:

$$S = \frac{BV}{WV} = \frac{\text{Between-Group Variance}}{\text{Within-Group Variance}}$$

- Subsets dominated by noise yield low scores and are ignored.
- Subsets containing signal features yield high scores and are used for prediction.

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
- Tailwind CSS (via CDN)
- MathJax (for rendering equations)
