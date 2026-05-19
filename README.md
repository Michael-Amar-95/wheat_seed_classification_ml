# Wheat Seed Classification – Machine Learning Pipeline

## Overview

This project presents a complete **machine learning pipeline** for classifying wheat seeds into different varieties based on physical kernel measurements.

The workflow includes:
- Data validation and preprocessing
- Feature normalization
- Dimensionality reduction (PCA)
- Supervised learning models (KNN, Decision Trees)
- Model evaluation and comparison
- Cost-sensitive learning analysis

---

# Dataset Description

The dataset contains **wheat seed measurements** extracted using soft X-ray imaging techniques.

Each sample includes:
- Area
- Perimeter
- Compactness
- Kernel Length
- Kernel Width
- Asymmetry Coefficient
- Kernel Groove Length
- Type (target variable)

---

# Data Preprocessing

## Validation
The dataset was checked for:
- Missing values
- Invalid or negative values
- Duplicate records

No data quality issues were detected.

---

## Normalization

Min-Max normalization was applied to scale all features into the range [0,1]:

\[
x' = \frac{x - min(x)}{max(x) - min(x)}
\]

This ensures fair comparison between features with different scales.

---

## Train-Test Split

- 160 samples used for training
- Remaining samples used for testing
- Randomized split with fixed seed for reproducibility

---

# Exploratory Data Analysis

## Correlation Analysis
A strong correlation was observed between:
- Area and Perimeter (~0.99)

This suggests strong dependency between grain size features.

---

## PCA Visualization

Principal Component Analysis (PCA) was used to project the dataset into 2D space for visualization.

This helped reveal:
- Natural clustering between wheat varieties
- Feature separability

---

# Machine Learning Models

## 1. K-Nearest Neighbors (KNN)

The KNN algorithm was evaluated with different values of k:
- k = 3
- k = 5
- k = 7

### Results
- Best performance: **k = 3**
- Achieved highest classification accuracy

---

## 2. Decision Tree (C5.0)

A decision tree classifier was trained using the C5.0 algorithm.

### Features:
- Interpretable tree structure
- Rule-based classification

### Performance:
- Accuracy ~87% on test data

---

## 3. Cost-Sensitive Decision Tree

A custom cost matrix was introduced to penalize misclassification differently.

### Goal:
Improve classification performance by weighting error types.

### Observation:
- No significant improvement in accuracy was observed
- Model performance remained similar

---

# Model Comparison

| Model | Accuracy |
|------|---------|
| KNN (k=3) | 100% |
| Decision Tree | ~87% |
| Cost-Sensitive Tree | ~87% |

---

# Key Insights

- KNN performed best on this dataset, likely due to:
  - Small dataset size
  - Clear feature separation
- Decision trees provided interpretability but lower accuracy
- PCA visualization confirmed strong clustering structure
- Cost-sensitive learning did not improve results in this case

---

# Technologies Used

- R
- ggplot2 (visualization)
- corrplot (correlation analysis)
- class (KNN)
- C50 (decision trees)
- PCA (prcomp)

---

# Conclusion

This project demonstrates a full machine learning workflow from raw data analysis to model evaluation.

It highlights the trade-off between:
- Accuracy (KNN)
- Interpretability (Decision Trees)
- Robust modeling strategies (cost-sensitive learning)
