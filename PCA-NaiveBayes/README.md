# TinyMNIST Classification with Custom PCA and Gaussian Naïve Bayes

This project implements **Principal Component Analysis (PCA) from scratch** and applies it to the **TinyMNIST** dataset, followed by classification using a **Gaussian Naïve Bayes** classifier. The goal is to reduce dimensionality while preserving 90% of the variance and evaluate classification accuracy.

## Dataset
- **TinyMNIST**: A reduced version of the MNIST dataset (28×28 pixels flattened to 196 features).
- Training: 5000 samples  
- Testing: 2500 samples  
- Labels: digits 0–9

## Implementation Steps
1. **Data Loading** – Load training and test data using Pandas and convert to NumPy arrays.
2. **Custom PCA**  
   - Mean-center the training data.  
   - Compute the covariance matrix.  
   - Perform eigendecomposition and sort eigenvalues/vectors in descending order.
3. **Optimal Feature Selection**  
   - Plot eigenvalues and cumulative explained variance.  
   - Determine the number of principal components (`k`) needed to capture at least **90%** of the total variance.
4. **Dimensionality Reduction** – Project both training and test data onto the first `k` principal components.
5. **Classification** – Train a Gaussian Naïve Bayes classifier on the reduced training set and evaluate accuracy on the reduced test set.
6. **Discussion** – Compare PCA-based feature reduction with direct feature selection; PCA preserves more information and improves computational efficiency.

## Results
- **Optimal number of features (k)**: 44  
- **Test accuracy (CCR)**: **83.12%**

The PCA-based approach effectively reduces dimensionality while maintaining high classification performance, demonstrating the benefits of variance-maximizing projections.

## Requirements
Install the required packages using:
```bash
pip install -r requirements.txt