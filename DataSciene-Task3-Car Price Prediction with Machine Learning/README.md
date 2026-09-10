# Car Price Prediction with Machine Learning

**Track:** Data Science
**Task:** 3 — Car Price Prediction with Machine Learning
**Internship:** Oasis Infobyte (OIBSIP)

## Overview
This project predicts the resale (selling) price of a used car from features such as brand, age, kilometers driven, fuel type, seller type, transmission, and ownership history, comparing three regression models to find the best performer.

## Workflow
1. **Data Loading & Cleaning**
   - Loaded `car_data.csv`, checked shape, dtypes, and summary statistics.
   - Checked and dropped duplicate rows.
   - Standardized inconsistent categorical values (whitespace, casing) across `fuel_type`, `seller_type`, `transmission`, `owner`.
   - Imputed missing numeric values (`kms_driven`, `present_price`) with the median, and missing categorical values (`fuel_type`, `owner`) with the mode.
2. **Feature Engineering**
   - Derived `car_age` from the car's manufacture year (relative to 2024).
   - Extracted `brand` from the car `name` field.
   - Consolidated rare brands (fewer than 10 listings) into an `"Other"` category to avoid a sparse one-hot encoding.
   - Dropped the now-redundant `name` and `year` columns.
3. **Exploratory Data Analysis (EDA)**
   - Distribution of selling prices.
   - Selling price by fuel type (boxplot).
   - Selling price vs. car age, colored by transmission type (scatter plot).
4. **Encoding** — One-hot encoded all categorical features (`fuel_type`, `seller_type`, `transmission`, `owner`, `brand`).
5. **Correlation Analysis** — Correlation heatmaps for both the core numeric features and the full encoded feature set.
6. **Train/Test Split** — 80/20 split (`random_state=42`).
7. **Model Training** — Trained and compared three regression models:
   - **Linear Regression** (baseline)
   - **Random Forest Regressor** (300 trees, max depth 10)
   - **Gradient Boosting Regressor** (300 estimators, learning rate 0.05, max depth 3)
8. **Evaluation** — Compared models using MAE, RMSE, and R².
9. **Predicted vs. Actual & Feature Importance** — Visualized the best model's predictions against actual values, and ranked its top 15 most important features.

## Results

| Model | MAE | RMSE | R² |
|---|---|---|---|
| **Gradient Boosting** | **0.255** | **0.457** | **0.985** |
| Random Forest | 0.325 | 0.597 | 0.974 |
| Linear Regression | 1.132 | 1.846 | 0.754 |

**Gradient Boosting** was the best-performing model, explaining ~98.5% of the variance in selling price with the lowest error of the three.

![Model comparison — MAE, RMSE, R² by model](screenshots/06_model_comparison_metrics.png)

**Predicted vs. Actual (Gradient Boosting)**

![Predicted vs actual selling price](screenshots/07_predicted_vs_actual.png)

Predictions cluster tightly along the perfect-prediction line, confirming the strong R² score.

**Feature Importance (Gradient Boosting)**

![Top 15 feature importances](screenshots/08_feature_importance.png)

`car_age` and `present_price` (original showroom price) are the two strongest predictors of resale price, with `kms_driven` also playing a meaningful role — fuel type and transmission have a smaller, secondary influence.

## Summary
Older cars and those with a lower original showroom price generally resell for less. Random Forest and Gradient Boosting both substantially outperform Linear Regression, confirming that resale price depends on non-linear relationships between age, mileage, and ownership history rather than a simple linear combination of features. Gradient Boosting was selected as the final model, and its top predictors — car age, present price, and kilometers driven — align with intuitive expectations about used car depreciation.

## Tech Stack
- **Language:** Python 3
- **Libraries:**
  - `pandas` / `numpy` — data cleaning, feature engineering
  - `scikit-learn` — train/test split, Linear Regression, Random Forest, Gradient Boosting, evaluation metrics
  - `matplotlib` / `seaborn` — EDA visualizations, correlation heatmaps, model comparison and feature importance charts

## How to Run
1. Install dependencies:
   ```
   pip install pandas numpy scikit-learn matplotlib seaborn jupyter
   ```
2. Open the notebook (the dataset CSV is already in this folder):
   ```
   jupyter notebook car_price_prediction.ipynb
   ```
3. Run all cells in order.

## Files in this Folder
- `car_price_prediction.ipynb` — Full Jupyter notebook (cleaning, feature engineering, EDA, encoding, model training, evaluation).
- `car_data.csv` — Raw dataset used by the notebook.
- `README.md` — This file.
- `screenshots/` — Output visualizations exported from the notebook:
  - `01_selling_price_distribution.png`
  - `02_price_by_fuel_type.png`
  - `03_price_vs_car_age.png`
  - `04_correlation_heatmap_numeric.png`
  - `05_correlation_heatmap_full.png`
  - `06_model_comparison_metrics.png`
  - `07_predicted_vs_actual.png`
  - `08_feature_importance.png`

---
*Part of the Oasis Infobyte Data Science Internship (OIBSIP).*
