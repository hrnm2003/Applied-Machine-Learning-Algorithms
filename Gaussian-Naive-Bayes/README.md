# Gaussian Naive Bayes Classifier from Scratch on Iris Dataset

This project implements a **Gaussian Naive Bayes classifier** from scratch using core Python scientific libraries (`numpy`, `pandas`, `matplotlib`). The model is trained and tested on a subset of the Iris dataset (two species: *Iris-versicolor* and *Iris-virginica*) using only **petal length** and **petal width** as features. The implementation is validated by comparing its performance with the official `scikit-learn` `GaussianNB` model.

## Overview

- **Theoretical Background**:  
  - Optimal Bayes classifier uses the full joint probability distribution – theoretically optimal but data‑hungry and computationally expensive.  
  - Naive Bayes simplifies by assuming conditional independence of features given the class. This reduces the problem to estimating 1D marginal distributions, making it data‑efficient and fast.
  - The Gaussian variant models each feature’s conditional distribution as a normal (Gaussian) distribution.

- **Implementation Details**:
  - Custom `NaiveBayesGaussian` class computes class priors, means, and variances from training data.
  - Predictions are made by calculating **log‑posterior** probabilities to avoid numerical underflow.
  - The decision boundary is visualised over the 2D feature space.

- **Dataset**:  
  - Iris dataset from UCI Machine Learning Repository.
  - Only two classes and two features are used to allow 2D visualisation.

- **Evaluation**:
  - Metrics: Accuracy, Precision, Recall, F1‑Score.
  - Confusion matrices for both the custom implementation and the scikit‑learn reference.

## Results

| Metric | Custom GaussianNB | Scikit‑learn GaussianNB |
|--------|-------------------|-------------------------|
| Accuracy   | 90.00% | 90.00% |
| Precision  | 87.50% | 87.50% |
| Recall     | 87.50% | 87.50% |
| F1 Score   | 87.50% | 87.50% |

Both implementations produce **identical results**, confirming the correctness of the manual implementation.

## Files

- `Gaussian_Naive_Bayes_From_Scratch.ipynb` – Jupyter notebook with full code, visualisations, and analysis.
- `requirements.txt` – List of required Python packages.

## Requirements

Install the dependencies with:

```bash
pip install -r requirements.txt