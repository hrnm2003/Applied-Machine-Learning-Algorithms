# University Admission Prediction

This project demonstrates a comprehensive machine learning pipeline for predicting university admission chances based on student profile features. It covers key algorithms and optimization techniques, providing both theoretical insights and practical implementations.

## Project Overview

The goal is to predict a student's chance of admission and binary admission status using features such as GRE scores, TOEFL scores, university rating, SOP, LOR, CGPA, and research experience. The notebook implements:

- **Exploratory Data Analysis (EDA)** – distribution visualizations, pair plots, and correlation matrices.
- **Linear Regression (Closed-Form Solution)** – using the normal equation to predict GRE scores.
- **Comparison of Closed-Form vs Gradient Descent** – highlighting computational trade‑offs.
- **Regularization** – Lasso (L1) and Ridge (L2) regression for feature selection and shrinkage.
- **Logistic Regression (Newton–Raphson)** – manual optimization with gradient and Hessian to predict admission (binary outcome).
- **Feature Importance Analysis** – interpreting coefficients to identify the most influential factors.

## Dataset

The dataset (`Admission.csv`) contains the following columns:

- `GRE Score`
- `TOEFL Score`
- `University Rating`
- `SOP` (Statement of Purpose)
- `LOR` (Letter of Recommendation)
- `CGPA`
- `Research` (binary)
- `Chance of Admit` (probability)

The notebook drops the `Serial No.` column and creates a binary target `Admitted` (1 if `Chance of Admit > 0.5`) for logistic regression.

## Key Results

- **Linear Regression** (predicting GRE Score):
  - Train MSE: ~26.99
  - Test MSE: ~31.94
- **Regularization**:
  - Lasso reduces coefficients of less important features (e.g., SOP, LOR, University Rating) to zero, acting as a feature selector.
  - Ridge shrinks all coefficients but preserves all features.
- **Logistic Regression** (binary admission):
  - Train accuracy: 95.00%
  - Test accuracy: 93.75%
- **Feature Importance**:
  - `CGPA` has the highest positive coefficient, followed by `TOEFL Score` and `LOR`.
  - This aligns with the correlation analysis, confirming CGPA as the strongest predictor.

## Requirements

Install the required packages using:

```bash
pip install -r requirements.txt