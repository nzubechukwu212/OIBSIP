# Unemployment Analysis in India

**Track:** Data Science
**Task:** 2 — Unemployment Analysis with Python
**Internship:** Oasis Infobyte (OIBSIP)

## Overview
This project explores regional and temporal trends in India's unemployment data, with a particular focus on how the **COVID-19 lockdown (announced 25 March 2020)** affected unemployment rates across states. The dataset covers **May 2019 – June 2020** across 28 states/UTs, broken down by Rural and Urban regions.

## Workflow
1. **Data Loading & Cleaning**
   - Loaded the raw CSV (768 rows, 7 columns).
   - Dropped 28 fully-null rows (no reliable way to impute them).
   - Stripped whitespace from column names.
   - Converted `Date` to datetime, and the rate/employment columns to numeric.
   - Derived `Month` and `Year` columns for seasonality analysis.
2. **Exploratory Data Analysis — Region-wise & Month-wise Trends**
   - Region-wise average unemployment rate (Rural + Urban combined).
   - Month-wise average unemployment rate to check for seasonality.
3. **Time-Series Analysis** — Unemployment rate over time for 5 major states (Karnataka, Uttar Pradesh, Tamil Nadu, Delhi, West Bengal), with the lockdown date marked on the chart.
4. **Bar Chart** — Top 10 states by average unemployment rate over the full period.
5. **Correlation Heatmap** — Relationship between Unemployment Rate, Estimated Employed, and Labour Participation Rate.
6. **Pre-COVID vs. Post-COVID Comparison** — Split the dataset at 25 March 2020 and compared mean unemployment rate, employment, and labour participation before vs. after, both nationally and by state.

## Key Findings

**Month-wise trend**
![Average unemployment rate by month](screenshots/01_monthwise_avg_unemployment.png)

The national unemployment rate stayed fairly stable for most of the period (roughly 8–11%), with a sharp spike in **April 2020** tied to the lockdown that began 25 March 2020.

**Time series for major states**
![Unemployment rate over time for major states](screenshots/02_timeseries_major_states.png)

Karnataka, Uttar Pradesh, Tamil Nadu, Delhi, and West Bengal all show low, stable rates through 2019 and early 2020 — then a sharp post-lockdown spike. **Tamil Nadu and Delhi** were hit hardest, briefly exceeding 40–50%, likely reflecting their reliance on informal and urban service-sector employment.

**Top 10 states by average unemployment rate**
![Top 10 states bar chart](screenshots/03_top10_states_barchart.png)

**Haryana, Tripura, Jharkhand, Bihar, and Himachal Pradesh** had the highest average rates across the full period (this blends pre- and post-lockdown data, so it reflects both persistent weak labour markets and lockdown spikes).

**Correlation heatmap**
![Correlation heatmap](screenshots/04_correlation_heatmap.png)

Unemployment Rate has a weak, near-zero correlation with raw Estimated Employed (which is mostly a function of population size), and only a mild positive correlation with Labour Participation Rate.

**Pre-COVID vs. Post-COVID**
![Pre-COVID vs Post-COVID bar chart](screenshots/05_precovid_postcovid_barchart.png)

The national average unemployment rate roughly **doubled to tripled** after the lockdown. At the state level, **Puducherry, Tamil Nadu, Bihar, and Jharkhand** saw the largest jumps — several by more than 30 percentage points — while some smaller states/UTs changed more moderately. Labour Participation Rate dipped slightly post-lockdown too, possibly reflecting discouraged workers exiting the labour force rather than continuing to seek work.

## Summary
Unemployment varies substantially across India, with Haryana, Tripura, and Jharkhand running above the national average even before COVID-19. Outside the pandemic period, monthly rates were relatively stable — the April 2020 spike is tied to the lockdown, not a recurring seasonal pattern. The lockdown caused a sudden nationwide rise in unemployment, hitting urban/service-oriented states like Tamil Nadu and Puducherry hardest. Raw employment counts are weakly related to the unemployment rate (population-driven), while Labour Participation Rate shows only a mild positive relationship with it.

## Tech Stack
- **Language:** Python 3
- **Libraries:**
  - `pandas` — data loading, cleaning, grouping, pivot tables
  - `numpy` — conditional period labeling (`np.where`)
  - `matplotlib` / `seaborn` — line charts, bar charts, correlation heatmap

## How to Run
1. Install dependencies:
   ```
   pip install pandas numpy matplotlib seaborn jupyter
   ```
2. Open the notebook (the dataset CSV is already in this folder, alongside it):
   ```
   jupyter notebook unemployment_analysis.ipynb
   ```
3. Run all cells in order.

## Files in this Folder
- `unemployment_analysis.ipynb` — Full Jupyter notebook (cleaning, EDA, time series, correlation, pre/post-COVID comparison).
- `Unemployment in India1.csv` — Raw dataset used by the notebook.
- `README.md` — This file.
- `screenshots/` — Output visualizations exported from the notebook:
  - `01_monthwise_avg_unemployment.png`
  - `02_timeseries_major_states.png`
  - `03_top10_states_barchart.png`
  - `04_correlation_heatmap.png`
  - `05_precovid_postcovid_barchart.png`

---
*Part of the Oasis Infobyte Data Science Internship (OIBSIP).*
