# Polynomial Regression with Cross-Validation

This project demonstrates the application of **K‑Fold Cross‑Validation** to evaluate the performance of polynomial regression models of varying complexity on a synthetic noisy dataset. The analysis illustrates the **bias–variance tradeoff** and helps identify the optimal model complexity.

## Workflow Summary

1. **Data Generation**  
   A synthetic dataset of 500 points is created using the function:  
   $$ y = 3 \cdot \sin(2x) + 0.5 \cdot x + \varepsilon $$  
   where `ε` is Gaussian noise with standard deviation 0.3.

2. **Cross‑Validation Setup**  
   The dataset is randomly split into **10 equal folds** using `KFold` with shuffling.

3. **Model Training & Evaluation**  
   For each fold, polynomial models of **degrees 1 through 25** are trained on 9 folds and evaluated on the remaining 1 fold using **Mean Squared Error (MSE)**.

4. **Performance Aggregation**  
   For each degree, the **mean** and **variance** of the 10 MSE scores are calculated to analyze model stability and accuracy.

5. **Visualization & Interpretation**  
   - Plots of mean and variance versus polynomial degree clearly illustrate the **bias–variance tradeoff**.  
   - The best (lowest mean MSE) and worst (highest mean MSE) models are visually compared against the original data.  
   - Additional fits for random degrees are shown to further demonstrate overfitting and underfitting.

## Results

- **Best degree**: 11 (Mean MSE = 0.1322)  
- **Worst degree**: 1 (Mean MSE = 4.4403)

The analysis shows that low‑degree models (1–5) have high bias and underfit the data, while high‑degree models (≥13) have high variance and overfit. The optimal complexity lies around degrees 9–12, where the mean MSE is lowest and variance remains relatively low.

## Requirements

The code requires Python 3 and the following libraries:

- `numpy`
- `matplotlib`
- `scikit-learn`

You can install them with:

```bash
pip install -r requirements.txt