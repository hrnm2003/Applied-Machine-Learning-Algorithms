# KNN Classifier Evaluation on Synthetic Data

This project explores the behavior of the K‑Nearest Neighbors (KNN) classifier using a controlled synthetic dataset. The goal is to understand how different distance metrics, noise, and class imbalance affect classification performance.

## Dataset

Two classes are generated:
- **Class X**: 2000 points `[u, 0]` with `u ~ Uniform(0, 1)`
- **Class Y**: 2000 points `[0, z]` with `z ~ Uniform(-1, 0)`

The two classes lie on perpendicular axes, making them perfectly linearly separable in the absence of noise.

## Experiments

### 1. Euclidean vs. Cosine Distance
KNN classifiers with `k = [1, 5, 20, 50]` were trained using both Euclidean and Cosine distance metrics.  
**Result**: Both metrics achieve **100% accuracy** because the data points are strictly orthogonal, making them perfectly separable.

### 2. Effect of Gaussian Noise
Gaussian noise (mean=0, std=0.1) was added to the training and test sets.  
**Result**: Accuracy drops to ~95‑96%. Larger values of `k` slightly improve performance by smoothing the decision boundary.

### 3. Imbalanced Dataset
An imbalanced dataset (10,000 Class X, 1,000 Class Y) was created without noise.  
**Result**: Accuracy remains near 100% because the classes are still perfectly separable. However, if noise were present, larger `k` values would tend to bias predictions toward the majority class.

## Requirements

- Python 3.7+
- NumPy
- Matplotlib
- scikit-learn

See `requirements.txt` for exact versions.

## Usage

Run the Jupyter notebook:

```bash
jupyter notebook KNN_Classifier_Synthetic_Data_Evaluation.ipynb