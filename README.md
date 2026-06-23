# 🇹🇳 Tunisia Tourism Flux Forecasting

> Predicting monthly tourism flux across 24 Tunisian governorates (2017–2025) using tabular ML and deep learning.

*Notebooks are written in French as this project was developed during studies at Université Paris-Dauphine Tunis.*

## Overview

End-to-end forecasting project on a spatio-temporal dataset of 2,520 observations covering all Tunisian governorates. The pipeline progresses from a baseline tabular model to an LSTM sequence model, with a geographic visualization of predictions.

## Dataset

| Feature | Detail |
|---------|--------|
| Observations | 2,520 (24 governorates × 12 months × 9 years) |
| Period | 2017 – 2025 |
| Variables | 32 (climate, geography, temporal lags, rolling means) |
| Missing values | 0 |

Key variables: `temperature_c`, `rainfall_mm`, `humidity_pct`, `ndvi_score`, `tourism_pressure_score`, temporal lags (`observed_lag_1` to `observed_lag_12`).

## Approach

### 1. EDA (`1_EDA.ipynb`)
- Distribution analysis of target variables
- Seasonality & yearly trends (COVID-19 impact visible in 2020)
- Geographic disparities across governorates
- Correlation analysis — lag features & climate variables

### 2. Modeling (`2_Modeling.ipynb`)

| Stage | Model | Description |
|-------|-------|-------------|
| A | Random Forest / XGBoost | Baseline tabular model |
| B | PCA + Random Forest | Dimensionality reduction |
| C | MLP (tuned) | Neural network on tabular features |
| D | LSTM | Sequence model on temporal windows |
| Bonus | GeoPandas choropleth | Spatial visualization of predictions (UTM 32N) |

## Project Structure

```
tunisia-tourism-forecasting/
├── notebooks/
│   ├── 1_EDA.ipynb        # Exploratory Data Analysis
│   └── 2_Modeling.ipynb   # Modeling pipeline (RF → PCA → MLP → LSTM)
├── data/
│   └── ex23_flux_touristique.csv
├── outputs/               # Generated maps and figures
└── requirements.txt
```

## Tech Stack

`Python` `pandas` `scikit-learn` `XGBoost` `TensorFlow/Keras` `GeoPandas` `matplotlib` `seaborn`

## Setup

```bash
git clone https://github.com/YOUR_USERNAME/tunisia-tourism-forecasting.git
cd tunisia-tourism-forecasting
pip install -r requirements.txt
```

## Author

**Ikram Saidane** — M1 IA & Data Science, Université Paris-Dauphine Tunis
