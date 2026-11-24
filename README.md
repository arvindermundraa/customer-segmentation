# Customer Segmentation Engine

![Python](https://img.shields.io/badge/Python-3.9%2B-blue) ![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.x-orange) ![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

An end-to-end unsupervised machine learning pipeline that segments retail customers into actionable groups using **RFM feature engineering**, **PCA dimensionality reduction**, and three clustering algorithms with rigorous statistical evaluation.

---

## Results

All numbers are from `report.pdf`.

| Step | Result |
|---|---|
| Cleaning | 541,909 raw transactions reduced to 358,580; 4,306 customers retained |
| Features | 8 RFM and behavioural features per customer |
| PCA | 4 components explain 93.59% of total variance |
| Model selected | K-Means with k = 3 (highest Calinski-Harabasz index, 2,790.7, and balanced cluster sizes) |
| DBSCAN | Silhouette 0.449 on non-noise points, but clusters of 62.2%, 35.4% and 0.1% of customers |
| Validation | Logistic regression predicting the segment label: 99.65% test accuracy (862 held-out customers); 99.45% ± 0.34% in 5-fold cross-validation |

---

## Dataset

| Property | Value |
|---|---|
| Source | [UCI Machine Learning Repository — Online Retail](https://archive.ics.uci.edu/ml/datasets/Online+Retail) |
| Period | December 2010 – December 2011 |
| Region | UK-based non-store online retailer |
| Key Variables | Invoice ID, Product codes, Quantities, Prices, Timestamps, Customer IDs |

---

## Pipeline

### 1. Feature Engineering
- **RFM metrics**: Recency (days since last purchase), Frequency (transaction count), Monetary (total spend)
- **Behavioral features**: Purchase patterns, product preferences, spending volatility
- **Temporal features**: Customer tenure, purchase seasonality

### 2. Dimensionality Reduction
- **PCA** applied to reduce feature space and remove multicollinearity before clustering

### 3. Clustering Algorithms

| Algorithm | Description |
|---|---|
| **K-Means** | Centroid-based; optimal K via elbow method and silhouette analysis |
| **Hierarchical Agglomerative** | Bottom-up linkage clustering with dendrogram analysis |
| **DBSCAN** | Density-based; robust to noise and non-convex shapes |

### 4. Evaluation Metrics

| Metric | What It Measures |
|---|---|
| **Silhouette Score** | Cohesion vs. separation of clusters |
| **Davies-Bouldin Index** | Average similarity between each cluster and its nearest neighbor |
| **Calinski-Harabasz Index** | Ratio of between-cluster to within-cluster dispersion |

### 5. Validation
- Supervised classifier trained on cluster labels to confirm segment separability and business utility
- Cross-validation with accuracy, precision, recall, and F1-score metrics

---

## Tech Stack

`Python` · `Pandas` · `NumPy` · `Scikit-learn` · `Matplotlib` · `Seaborn` · `SciPy`

---

## Setup

```bash
pip install -r requirements.txt
```

Download the dataset from the [UCI repository](https://archive.ics.uci.edu/ml/datasets/Online+Retail), place it in the project root, then open `customer segementation.ipynb` in Jupyter or Google Colab.

---

## Files

| File | Description |
|---|---|
| `customer segementation.ipynb` | Full pipeline: EDA → feature engineering → clustering → evaluation |
| `report.pdf` | Comprehensive written report with methodology and conclusions |
| `customer_segementation.pptx` | Presentation slides summarizing methodology and findings |

---

## Course

**STAT 654 — Statistical Computing with R and Python** · Texas A&M University · Spring 2026

---

## Author

**Arvinder Mundra** · [Portfolio](https://portfolio-react-theta-gules.vercel.app/) · [LinkedIn](https://www.linkedin.com/in/arvinder-mundraa) · [GitHub](https://github.com/arvindermundraa)
