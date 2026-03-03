# California Housing Price Prediction 🏠

**Portfolio Project #01 | Regression | Python | scikit-learn**

## Results at a Glance

| Metric | Linear Regression (Baseline) | Random Forest (Final) |
|--------|------------------------------|----------------------|
| R² Score | 0.6514 | **0.8047** |
| RMSE | 0.6759 | **0.5059** |
| Avg Error | $67,587 | **$50,590** |

The Random Forest improved R² by +0.15 and reduced average prediction error by $17,000 over the baseline.

---

## Overview

This project builds a machine learning pipeline to predict median house values across California neighborhoods using 1990 U.S. Census data. Starting from a Linear Regression baseline, it progresses to a Random Forest model that explains **80% of the variation in house prices** with an average error of $50,590.

---

## Dataset

**Source:** California Housing Dataset (built into scikit-learn) — 20,640 neighborhoods

| Feature | Description | Economic Interpretation |
|---------|-------------|------------------------|
| `MedInc` | Median household income | Primary driver of purchasing power and demand |
| `HouseAge` | Median age of housing stock | Older stock may signal established neighborhoods |
| `AveRooms` | Average rooms per household | Proxy for property size and quality |
| `AveBedrms` | Average bedrooms per household | Space allocation within properties |
| `Population` | Block group population | Demand-side density indicator |
| `AveOccup` | Average household size | Crowding measure — higher = lower value signal |
| `Latitude` | Geographic latitude | Captures coastal and Bay Area premiums |
| `Longitude` | Geographic longitude | East-west geographic variation |
| `MedHouseVal` | **Median house value (TARGET)** | Dependent variable — what we predict |

---

## Methodology

**1. Exploratory Data Analysis**

Examined distributions, identified a right skew in house values, and flagged data censoring at the $500,000 cap.

**2. Feature Engineering**

Created 3 new economic features from existing variables:
- `RoomsPerPerson` — adjusts room count for household size (occupancy-adjusted space)
- `BedroomRatio` — bedrooms as a share of total rooms (layout quality signal)
- `PopulationPerRoom` — density proxy combining population and housing stock

**3. Preprocessing**

An 80/20 train-test split was applied with StandardScaler normalization on training data only (no data leakage).

**4. Modeling**

Linear Regression was trained as a baseline, then a Random Forest (100 estimators) was used to capture non-linear relationships between features.

---

## Key Findings

- **Median income (MedInc)** was the strongest predictor — consistent with housing economics theory linking purchasing power to demand
- **Average occupancy (AveOccup)** ranked second, capturing the signal that overcrowded neighborhoods correlate with lower property values
- **Latitude** ranked third, acting as an implicit proxy for coastal and Bay Area location premiums — learned purely from data with no geographic labels
- Data censoring at $500,000 limits model accuracy at the top end of the market — flagged as a limitation for future work

---

## How to Run

No downloads required. The dataset is built into scikit-learn.

**Option 1 — Google Colab (recommended):**
Open the notebook and run all cells in order.

**Option 2 — Local setup:**
```bash
pip install scikit-learn pandas matplotlib
jupyter notebook california_housing.ipynb
```

---

## Tools & Libraries

- Python 3.12
- `pandas` — data manipulation
- `scikit-learn` — modeling, preprocessing, evaluation
- `matplotlib` — visualization

---

## About

Built as part of an Economics portfolio by an economics major exploring machine learning applications in finance and policy. **Project 1 of 10.**
