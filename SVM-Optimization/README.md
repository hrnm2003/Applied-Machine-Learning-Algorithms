# SVM Optimization from Scratch using CVXPY

This project implements two fundamental Support Vector Machine (SVM) formulations entirely from scratch using the CVXPY optimization library, without relying on black-box ML libraries for the core optimization logic.

## Overview

The notebook `Kernelized_SVM_Classifier.ipynb` covers:

1.  **Hard Margin SVM (Primal Formulation)**: Solves the quadratic programming (QP) problem directly to find the optimal separating hyperplane for a linearly separable dataset.
2.  **Kernelized SVM (Dual Formulation)**: Solves the Lagrangian dual problem, incorporating the **Radial Basis Function (RBF)** kernel to handle non-linearly separable data by implicitly mapping features into a higher-dimensional space.

## Implementation Details

- **Primal Problem**: Minimizes `0.5 * ||w||^2` subject to `y_i (w·x_i + b) >= 1`. Support vectors are identified where the constraint is active.
- **Dual Problem**: Maximizes the Lagrange dual using the kernel trick. The objective is `sum(alpha) - 0.5 * sum(alpha_i * alpha_j * y_i * y_j * K(x_i, x_j))`. The code automatically handles positive semi-definite (PSD) adjustments for the kernel matrix.
- **Dataset 1**: `dataset-Q5-1.csv` – Linearly separable data used for the Hard Margin SVM.
- **Dataset 2**: `dataset-Q5-2.csv` – Non-linearly separable data used for the Kernelized SVM with `gamma = 5.0`.

## Results

- **Hard Margin SVM**: Successfully finds the maximum-margin hyperplane. The optimal weights `w` and bias `b` are printed, and the decision boundary (including the margin lines) is plotted alongside the support vectors.
- **Kernelized SVM**: Achieves **100% classification accuracy** on the non-linear dataset by utilizing the RBF kernel. The decision boundary contours effectively separate the two classes, demonstrating the power of kernel methods.

## Requirements

All dependencies are listed in `requirements.txt`.

## Getting Started

1.  Clone the repository and navigate to this directory.
2.  Ensure the dataset files (`dataset-Q5-1.csv` and `dataset-Q5-2.csv`) are placed in the `datasets` directory as the notebook.
3.  Install the required packages:
    ```bash
    pip install -r requirements.txt