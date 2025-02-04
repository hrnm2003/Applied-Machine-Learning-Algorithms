# Soybean Cultivars Clustering with K‑Means++

This project applies K‑Means clustering to a dataset of soybean cultivars, using the **K‑Means++** initialization to improve centroid selection. The optimal number of clusters is determined by maximizing the **Silhouette Coefficient**. Additionally, a comparison is made between **Euclidean** and **Mahalanobis** distance measures to assess clustering quality.

---

## Dataset

The dataset (`dataset-Q6.csv`) contains numerical features describing various soybean cultivars. The features are standardised using `StandardScaler` before clustering.

---

## Methodology

1. **K‑Means++ Initialization**  
   - The first centroid is chosen uniformly at random.  
   - Subsequent centroids are selected with probability proportional to the squared distance from the nearest existing centroid.  
   - This spreads initial centroids and reduces the risk of poor local minima.

2. **Optimal Number of Clusters**  
   - The Silhouette Coefficient is computed for \(k = 2\) to \(10\).  
   - The \(k\) with the highest average silhouette score is selected as optimal.

3. **Distance Comparison**  
   - **Euclidean Distance**:  
     $$
     d_E(x,y) = \sqrt{(x-y)^\top (x-y)}
     $$
   - **Mahalanobis Distance**:  
     $$
     d_M(x,y) = \sqrt{(x-y)^\top \Sigma^{-1} (x-y)}
     $$
     where \(\Sigma\) is the sample covariance matrix (regularised with a small identity matrix to ensure invertibility).  
   - Both distances are used with K‑Means++ on the same dataset, and the Silhouette score is reported for each.

---

## Results

| Clustering Method               | Optimal k | Silhouette Score |
|----------------------------------|-----------|------------------|
| Euclidean K‑Means++             | 2         | 0.2589           |
| Mahalanobis K‑Means++           | 2         | 0.0899           |

- The **Euclidean** distance yields a substantially higher Silhouette score, indicating that the clusters are more compact and well‑separated under the Euclidean metric.
- **Mahalanobis** distance, despite accounting for feature correlations and scale, performs worse on this dataset—possibly due to the high‑dimensionality or near‑singular covariance matrix.

---

## Requirements

Install the required packages with:

```bash
pip install -r requirements.txt