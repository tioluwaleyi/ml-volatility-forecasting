# Machine Learning vs Econometric Models for Volatility Forecasting

## Project Overview

This project investigates whether machine learning models can outperform traditional econometric models in forecasting equity market volatility.

The study compares classical volatility forecasting approaches such as GARCH and EGARCH against machine learning techniques including Random Forest and XGBoost. The project uses financial market data from major equities and market indices and will later be extended using realized volatility datasets from global indices.

---

# Day 1 – Project Setup

## Objectives

- Create GitHub repository
- Establish project structure
- Configure development environment
- Install required libraries
- Initialize version control

## Completed Tasks

- Created GitHub repository: `ml-volatility-forecasting`
- Connected local repository to GitHub
- Configured Git version control
- Installed required Python packages
- Created project folder structure
- Added README and documentation files

## Project Structure

```text
ml-volatility-forecasting/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
│
├── notebooks/
│
├── reports/
│
├── figures/
│
├── src/
│
├── README.md
├── requirements.txt
└── .gitignore
```

## Key Outcome

The project environment was successfully established and synchronized with GitHub, providing a reproducible research framework for subsequent analysis.

---

# Day 2 – Data Collection

## Objectives

- Acquire historical market data
- Build a reproducible data collection pipeline
- Store raw financial datasets

## Assets Selected

### Individual Equities

- AAPL (Apple)
- MSFT (Microsoft)

### Market Benchmark

- SPY (S&P 500 ETF)

### Market Volatility Indicator

- VIX (CBOE Volatility Index)

## Data Source

Yahoo Finance via the `yfinance` Python package.

## Data Period

2015 – 2025

## Completed Tasks

- Downloaded historical market data
- Inspected dataset structure
- Verified data integrity
- Saved raw dataset to project directory

## Key Outcome

A multi-asset financial dataset was successfully collected and stored, forming the foundation for volatility forecasting and feature engineering.

---

# Day 3 – Returns and Volatility Construction

## Objectives

- Transform price data into returns
- Generate volatility measures
- Create modeling dataset

## Methodology

### Log Returns

Daily log returns are calculated as:

r_t = ln(P_t / P_(t-1))

where:

- r_t = return at time t
- P_t = current price
- P_(t-1) = previous price

### Rolling Volatility

The following volatility measures are generated:

- 5-Day Rolling Volatility
- 20-Day Rolling Volatility
- 60-Day Rolling Volatility

## Completed Tasks

- Loaded raw market dataset
- Calculated daily log returns
- Generated rolling volatility measures
- Created processed datasets
- Visualized return behavior
- Visualized volatility clustering

## Initial Observations

- Financial returns exhibit periods of high and low volatility.
- Volatility appears clustered through time.
- Market shocks are followed by persistent elevated volatility.
- Volatility persistence supports the use of econometric models such as GARCH.

## Generated Files

```text
data/processed/
│
├── returns.csv
└── volatility_features.csv
```

## Key Outcome

Raw financial prices were transformed into return and volatility datasets suitable for econometric and machine learning forecasting models.

---

# Next Steps

## Day 4

Feature Engineering

Tasks:

- Create lagged return features
- Add VIX features
- Create rolling statistics
- Generate model-ready dataset

## Planned Models

### Traditional Models

- GARCH(1,1)
- EGARCH

### Machine Learning Models

- Random Forest
- XGBoost

### Advanced Extension

- HAR-RV
- LSTM
- Realized Volatility Forecasting

---

## Research Question

Can machine learning models outperform traditional econometric models in forecasting future equity market volatility?
# Day 4 – Feature Engineering

## Objectives

- Create predictive features from historical market data.
- Incorporate market-wide volatility indicators.
- Prepare model-ready datasets.

## Feature Categories

### Lagged Returns

The following lagged return features are created:

- Return Lag 1
- Return Lag 5
- Return Lag 10

These features capture short-term market memory and momentum effects.

### Rolling Volatility Measures

The following volatility windows are included:

- 5-Day Volatility
- 20-Day Volatility
- 60-Day Volatility

These variables represent recent market uncertainty and volatility persistence.

### Market Indicators

External market information includes:

- VIX Index
- SPY Returns
- SPY Volatility

These variables provide additional information regarding overall market sentiment and systemic risk.

## Data Processing

- Missing values removed.
- Features aligned by date.
- Feature dataset validated for modeling.

## Expected Outcome

A structured feature matrix suitable for both econometric and machine learning forecasting models.

---

# Day 5 – Exploratory Analysis of Features

## Objectives

- Understand relationships among variables.
- Identify predictive patterns.
- Detect multicollinearity and feature importance candidates.

## Analysis Performed

### Correlation Analysis

Investigate relationships between:

- Returns
- Volatility Measures
- VIX
- Market Indicators

### Distribution Analysis

Examine:

- Skewness
- Kurtosis
- Heavy-tailed behavior

### Volatility Regime Inspection

Identify periods of:

- Low volatility
- Moderate volatility
- Extreme volatility

Examples include:

- COVID-19 Market Crash
- Post-COVID Recovery
- Inflationary Market Conditions

## Initial Observations

- Volatility displays persistence through time.
- Returns are not normally distributed.
- Market shocks produce extended periods of elevated volatility.
- VIX appears positively related to realized volatility.

## Key Outcome

Feature relationships and market behavior are understood prior to model construction.

---

# Day 6 – Baseline Forecasting Models

## Objectives

- Establish benchmark forecasting performance.
- Create reference points for advanced models.

## Benchmark Model 1

### Naive Volatility Forecast

Assumption:

Future volatility equals current volatility.

Forecast:

Volatility(t+1) = Volatility(t)

## Benchmark Model 2

### Historical Average Volatility

Assumption:

Future volatility equals the average historical volatility over a selected window.

## Evaluation Metrics

The following metrics are used:

### Mean Squared Error (MSE)

Measures average squared prediction error.

### Root Mean Squared Error (RMSE)

Measures forecast accuracy in original units.

### Mean Absolute Error (MAE)

Measures average magnitude of forecasting errors.

## Why Baselines Matter

A sophisticated model should outperform simple forecasting rules.

Without benchmarks, it is impossible to determine whether machine learning adds predictive value.

## Expected Outcome

Baseline forecasting performance established for later comparison with:

- GARCH(1,1)
- EGARCH
- Random Forest
- XGBoost

Research Interpretation

This suggests that volatility in AAPL exhibits substantial mean-reverting behavior over the sample period.

Rather than tomorrow's volatility simply equaling today's volatility, a forecast based on recent average volatility provides a more accurate estimate of future realized volatility.

The results also indicate that volatility persistence exists but is not perfectly captured by a one-period persistence assumption.

Add This to the Paper
4.4 Baseline Results
Model	QLIKE	RMSE	MAE
Naive Forecast	0.4451	0.5997	0.4363
Historical Average Forecast	0.3385	0.5819	0.3927
Discussion

The historical average model outperformed the naive persistence model across all evaluation metrics. The largest improvement was observed in QLIKE loss, which decreased from 0.4451 to 0.3385. This finding suggests that recent average volatility contains more predictive information about future volatility than a simple assumption that tomorrow's volatility equals today's volatility.

The historical average forecast therefore serves as the primary benchmark against which all subsequent models will be evaluated.