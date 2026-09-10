# Iris Flower Classification

**Track:** Data Science
**Task:** 1 — Iris Flower Classification
**Internship:** Oasis Infobyte (OIBSIP)

## Overview
This project builds a machine learning model to classify iris flowers into one of three species — *Setosa*, *Versicolor*, and *Virginica* — based on four measured features: sepal length, sepal width, petal length, and petal width. The classic Iris dataset (via `sklearn.datasets.load_iris`) is used as the data source.

## Workflow
1. **Data Loading** — Loaded the Iris dataset directly from scikit-learn (150 samples, 4 features, 3 classes).
2. **Exploratory Data Analysis (EDA)**
   - Checked data shape, feature data types, and confirmed there are no missing values.
   - Generated descriptive statistics (mean, std, min/max, quartiles) for each feature.
   - Visualized relationships with a **pair plot** (colored by species).
   - Visualized feature distributions per species with **boxplots**.
   - Examined a **correlation heatmap** to identify the most discriminative features.

   ![Pairplot of Iris features by species](screenshots/01_pairplot.png)
   ![Correlation heatmap](screenshots/06_correlation_heatmap.png)

3. **Feature/Target Split** — Separated the dataset into features (`X`) and target labels (`y`).
4. **Train/Test Split** — 80/20 split (`random_state=42`) using `train_test_split`.
5. **Model Training & Evaluation** — Trained and evaluated two classifiers:
   - **Logistic Regression**
   - **Random Forest Classifier** (100 estimators)

   For each model: accuracy score, classification report (precision/recall/F1), and a confusion matrix (visualized as a heatmap).
6. **Model Comparison** — Compared both models side-by-side on accuracy, precision, recall, and F1-score.

## Results
Both the Logistic Regression and Random Forest models achieved **100% accuracy** on the held-out test set, with perfect precision, recall, and F1-scores across all three species. This is expected given the well-separated nature of the Iris classes (particularly *Setosa*, which is linearly separable from the other two species).

| Logistic Regression | Random Forest |
|:---:|:---:|
| ![Confusion matrix — Logistic Regression](screenshots/07_confusion_matrix_logistic_regression.png) | ![Confusion matrix — Random Forest](screenshots/08_confusion_matrix_random_forest.png) |

## Tech Stack
- **Language:** Python 3
- **Libraries:**
  - `scikit-learn` — dataset, train/test split, Logistic Regression, Random Forest, evaluation metrics
  - `pandas` — data handling and descriptive statistics
  - `numpy` — missing value checks
  - `matplotlib` / `seaborn` — data visualization (pairplot, boxplots, heatmaps)

## How to Run
1. Install dependencies:
   ```
   pip install scikit-learn pandas numpy matplotlib seaborn jupyter
   ```
2. Open the notebook:
   ```
   jupyter notebook iris_flower_classification.ipynb
   ```
3. Run all cells in order.

## Files in this Folder
- `iris_flower_classification.ipynb` — Full Jupyter notebook containing EDA, visualizations, model training, and evaluation.
- `README.md` — This file.
- `screenshots/` — Output visualizations exported from the notebook:
  - `01_pairplot.png` — Pairwise feature relationships colored by species.
  - `02–05_boxplot_*.png` — Boxplots of each feature by species.
  - `06_correlation_heatmap.png` — Feature correlation matrix.
  - `07_confusion_matrix_logistic_regression.png` — Confusion matrix for the Logistic Regression model.
  - `08_confusion_matrix_random_forest.png` — Confusion matrix for the Random Forest model.

---
*Part of the Oasis Infobyte Data Science Internship (OIBSIP).*
