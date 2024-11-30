# Non-Parametric Density Estimation: Parzen Window and K-Nearest Neighbors

This repository contains a Jupyter notebook that demonstrates non-parametric density estimation using two fundamental techniques:

- **Parzen Window (Kernel Density Estimation)** with a Gaussian kernel
- **K-Nearest Neighbors (KNN) Density Estimation**

The methods are applied to a synthetic dataset of 1000 points sampled from a uniform distribution `U(-1, 1)`. The goal is to compare how each approach estimates the underlying probability density function without assuming any parametric form.

## Overview

Non-parametric density estimation is essential when the true distribution is unknown or too complex to model parametrically. Instead of fitting a fixed function, these methods let the data itself determine the shape of the density.

### 1. Parzen Window (Gaussian Kernel)

The Parzen window estimator places a kernel (here a standard normal distribution) on each data point and sums them:

$$
\hat{p}(x) = \frac{1}{N h} \sum_{i=1}^{N} K\left(\frac{x - x_i}{h}\right),
\qquad
K(u) = \frac{1}{\sqrt{2\pi}} e^{-u^2/2}
$$

where \(h\) is the bandwidth controlling smoothness. We test four bandwidths: `h = [0.1, 0.5, 1.0, 2.0]`.

**Key observations:**
- **Small `h` (0.1):** High variance, low bias. The estimate is noisy and overfits local variations, but captures sharp boundaries well.
- **Moderate `h` (0.5):** Balanced trade‑off; smooths noise while preserving the true density shape.
- **Large `h` (1.0, 2.0):** High bias, low variance. Over‑smoothing causes the density to spread outside the true support and the peak drops below the true value of 0.5.

### 2. K-Nearest Neighbors (KNN) Density Estimation

The KNN estimator fixes the number of neighbors \(k\) and defines the local volume as the distance to the \(k\)-th nearest neighbor:

$$
\hat{p}(x) = \frac{k}{N \cdot V_k(x)}, \quad V_k(x) = 2 \cdot R_k(x)
$$
in 1D, where \(R_k(x)\) is the distance to the \(k\)-th nearest sample. We evaluate `k = [1, 5, 20, 50]`.

**Key observations:**
- **Small `k` (1):** Extremely high variance; spikes appear at sample points and the estimate is very erratic.
- **Moderate `k` (5, 20):** Noise decreases; for `k=20` the density stabilises near 0.5 within the support.
- **Large `k` (50):** Smooth inside the interval, but heavy tails appear outside `[-1,1]` because the volume grows linearly with distance, leading to a slow `1/|x|` decay.

### Comparison Summary

| Aspect | Parzen Window | KNN |
|--------|---------------|-----|
| **Adaptivity** | Fixed volume (`h`), counts points | Fixed count (`k`), adapts volume |
| **Smoothness** | Smooth (Gaussian kernel) | Non‑smooth step‑like shapes |
| **Boundary behaviour** | Gradual leakage outside support | Heavy‑tailed decay outside support |
| **Tuning parameter** | Bandwidth `h` | Number of neighbors `k` |

Both methods suffer from boundary bias near `x = ±1` due to the discontinuity of the true uniform density.

## Files

- `Non_Parametric_Density_Estimation_Parzen_KNN.ipynb` – Main Jupyter notebook with full implementation and visualisations.
- `README.md` – This file.
- `requirements.txt` – List of Python dependencies.

## Requirements

Install the required packages using:

```bash
pip install -r requirements.txt