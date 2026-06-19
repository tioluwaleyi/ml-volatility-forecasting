# Volatility Forecasting Using Machine Learning

## Research Question

Can machine learning models outperform traditional econometric methods in forecasting next-day equity volatility?

## Dataset

- AAPL (target asset)
- SPY
- MSFT
- VIX
- Period: 2016–2025

## Models Evaluated

1. Historical Average
2. GARCH(1,1)
3. Random Forest
4. XGBoost

## Results

| Model | QLIKE | RMSE | MAE |
|---------|---------|---------|---------|
| Random Forest | 0.2734 | 0.5113 | 0.3507 |
| XGBoost | 0.2949 | 0.5259 | 0.3663 |
| Historical Average | 0.3385 | 0.5819 | 0.3927 |
| GARCH(1,1) | 0.3987 | 0.7552 | 0.6036 |

## Key Finding

Random Forest achieved a 19.2% reduction in QLIKE loss relative to the Historical Average benchmark and a 31.4% reduction relative to GARCH(1,1).
