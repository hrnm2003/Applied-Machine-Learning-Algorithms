# Feature Selection with Naïve Bayes on TinyMNIST

This repository contains a Jupyter Notebook implementing **forward feature selection** and **backward feature elimination** using a **Gaussian Naïve Bayes** classifier on the **TinyMNIST** dataset. The goal is to identify the optimal subset of features that maximizes the Correct Classification Rate (CCR) while reducing dimensionality.

## Dataset

The **TinyMNIST** dataset is a reduced version of MNIST, consisting of 14×14 pixel grayscale images (196 features). The dataset is split into:
- **Training set**: 5000 samples
- **Test set**: 2500 samples

The data files (`trainData.csv`, `testData.csv`, `trainLabels.csv`, `testLabels.csv`) are expected to be placed in a subdirectory named `TinyMNIST/`.

## Methodology

Two wrapper-based feature selection methods are implemented:

1. **Forward Selection**  
   - Starts with an empty set of features.
   - Iteratively adds the feature that yields the highest CCR when combined with the currently selected features.
   - Stops after evaluating all features.

2. **Backward Elimination**  
   - Starts with the full set of 196 features.
   - Iteratively removes the feature whose elimination causes the least decrease (or the greatest increase) in CCR.
   - Continues until only one feature remains.

At each step, a **Gaussian Naïve Bayes** classifier is trained on the training set and evaluated on the test set using **accuracy** as the performance metric.

## Results

The notebook plots the CCR as a function of the number of selected features for both methods.

- **Forward Selection** achieved its **maximum CCR of 0.7996** with **61 features**.
- **Backward Elimination** achieved its **maximum CCR of 0.7480** with **97 features**.

These results demonstrate that a significant reduction in feature count (from 196 to 61) can improve or maintain high classification accuracy, highlighting the effectiveness of forward selection in this context.

## How to Run

1. Clone this repository.
2. Ensure the TinyMNIST CSV files are placed in the `TinyMNIST/` directory.
3. Install the required packages:
   ```bash
   pip install -r requirements.txt