# Time Series Lecture: Temperature Forecasting Baselines

This repository contains two teaching notebooks that walk through practical time series decomposition and baseline forecasting using daily minimum temperature data from the SMEAR Estonia station.

## Project Contents

- `tsa1.ipynb`: Part 1
- `tsa2.ipynb`: Part 2
- `data/SMEAR_2m_daily_min_temperature.csv`: Input dataset

## Dataset

The dataset contains daily minimum temperature observations with the following columns:

- `date`
- `min_temperature`

Data span in this lecture: 2014 to 2023.

## What You Learn

### Part 1 (`tsa1.ipynb`)

- Basic inspection and plotting of a daily temperature time series
- Time series decomposition with `seasonal_decompose(..., model='additive', period=365)`
- Interpretation of trend, seasonal component, and residuals
- Seasonal naive baseline forecast (`shift(365)`)
- Evaluation with SMAPE (instead of MAPE to avoid division issues near zero)

### Part 2 (`tsa2.ipynb`)

- Improving baseline models without moving to ARIMA/SARIMA
- Standard decomposition-based baseline (trend + seasonal)
- Daily average model by day-of-year
- Calendar-day average model by `(month, day)` to handle leap-year details
- Blended model: 70% calendar-day forecast + 30% previous-day temperature
- SMAPE comparison across baseline variants

## Expected Progression of Forecast Accuracy

Approximate SMAPE values shown in the notebooks:

- Seasonal naive model: ~22.75%
- Decomposition-based baseline: ~20.93%
- Day-of-year average model: ~20.90%
- Calendar-day average model: improved further
- Blended model: ~18.52%

## Requirements

Install the following Python packages:

- `pandas`
- `numpy`
- `matplotlib`
- `statsmodels`
- `jupyter` (or `notebook`)

## Quick Start

1. Create and activate a virtual environment.
2. Install dependencies:

```bash
pip install pandas numpy matplotlib statsmodels jupyter
```

3. Start Jupyter:

```bash
jupyter notebook
```

4. Open and run notebooks in order:

- `tsa1.ipynb`
- `tsa2.ipynb`

## Notes

- The notebooks set the date column as index and enforce daily frequency with forward fill for missing values.
- SMAPE is used as the primary error metric because temperature values can be close to zero.


