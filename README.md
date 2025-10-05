# Assignment 3

## Name: Apurv Ravindra Kshirsagar

## Roll No: CE22B042

---

## Project Overview

This project explores **non-linear dimensionality reduction** and **manifold learning** to visualize and understand the structure of a high-dimensional, multi-label dataset. The dataset used is the **Yeast dataset**, where each sample can be associated with multiple functional categories.

The objective is to:

1.  **Preprocess** the high-dimensional feature matrix and simplify the complex multi-label system for effective visualization.
2.  Apply **t-SNE (t-Distributed Stochastic Neighbor Embedding)** to visualize the local neighborhood structure and identify clusters.
3.  Apply **Isomap (Isometric Mapping)** to visualize the global manifold structure of the data.
4.  **Compare** the two techniques and use the visualizations as a diagnostic tool to analyze data quality, identify outliers, and infer the complexity of the underlying data manifold for future classification tasks.

---

## Steps Performed

### 1. Preprocessing and Label Simplification

- Loaded the **yeast.arff** dataset using SciPy and converted it to a pandas DataFrame.
- Analyzed the label frequencies to identify the most common single labels and the most frequent multi-label combination.
- Engineered a new, simplified 2-category target variable (`Dominant_Labels` and `Other`) to enable clear and insightful coloring in the visualizations.
- Applied **Standardization (Z-score scaling)** to the feature matrix, a crucial step to ensure all features contribute equally to the distance-based algorithms.

### 2. t-SNE for Local Structure Visualization

- Applied **t-SNE** to reduce the 103-dimensional feature space down to 2 dimensions.
- Systematically experimented with the **`perplexity`** hyperparameter (testing values from 5 to 50) to find the optimal visualization.
- Selected **perplexity=30** as the final choice, as it provided the best balance between preserving local neighborhood structures and revealing larger, meaningful clusters.
- Performed a **Veracity Inspection** on the final t-SNE plot to:
  - Identify **noisy labels** (points of one color embedded in clusters of another).
  - Find **outliers** (isolated points and small, distant clusters).
  - Locate **hard-to-learn samples** at the boundaries between clusters, where a simple classifier would struggle.

### 3. Isomap for Global Manifold Learning

- Applied **Isomap** to reduce the data to 2D, explaining its focus on preserving global **geodesic distances** ("walking distance") rather than local neighborhoods.
- Generated a scatter plot using the Isomap coordinates.
- Compared the visualizations, concluding that **t-SNE is superior for cluster separation**, while **Isomap provides a better representation of the data's global manifold structure**.
- Analyzed the Isomap plot's shape to infer that the data lies on a **complex and highly curved manifold**, suggesting that simple linear models would be ineffective for classification and that more advanced, non-linear models are required.

---

## Libraries Required

Install the following Python libraries before running the notebook:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```
