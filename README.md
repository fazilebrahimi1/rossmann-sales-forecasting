# Rossmann Store Sales Forecasting
A time series forecasting project comparing SARIMA, ARIMA and XGBoost 
on real weekly retail sales data from Rossmann, Germany's second-largest 
drugstore chain.

## Business Question
Can we accurately forecast weekly Rossmann store sales — and what drives 
them more, seasonal patterns or promotional activity?

## Dataset
Historical daily sales data for 1,115 Rossmann stores across Germany 
(January 2013 – July 2015), aggregated to weekly frequency for Store 1.

**Download the data here:**
https://www.kaggle.com/datasets/pratyushakar/rossmann-store-sales

You will need two files:
- `train.csv` — historical sales data
- `store.csv` — store metadata

Place both files in the same folder as the notebook before running.

## Project Structure
```
rossmann-sales-forecasting/
│
├── rossmann_final_insights.ipynb  # Main notebook
├── requirements.txt               # Dependencies
└── README.md                      # This file
```

## Methods
| Model | Description |
|-------|-------------|
| SARIMA(1,1,1)(1,1,1,12) | Seasonal model applied at monthly frequency |
| ARIMA(1,1,1) | Linear baseline applied at weekly frequency |
| XGBoost | Gradient boosted trees with lag and promo features |

## Key Findings
- Promotions are the single strongest predictor of weekly sales — a 28.3% uplift worth €6,773 extra revenue per promotional week
- XGBoost achieves the best accuracy (MAPE 8.4%) by directly encoding the promotional calendar
- ARIMA achieves a solid 12.0% MAPE operating purely from historical sales with no external information
- SARIMA achieves 18.2% MAPE — correctly identifies seasonal structure but cannot incorporate promotional signals
- The performance gap between models is driven by information access, not model complexity

## Evaluation Metrics
| Model | MAE | RMSE | MAPE |
|-------|-----|------|------|
| SARIMA(1,1,1)(1,1,1,12) | €20,357 | €20,925 | 18.2% |
| ARIMA(1,1,1) | €3,030 | €3,557 | 12.0% |
| XGBoost | €2,000 | €2,506 | 8.4% |

## How to Run
1. Clone this repository
```bash
git clone https://github.com/fazilebrahimi1/rossmann-sales-forecasting.git
cd rossmann-sales-forecasting
```
2. Install dependencies
```bash
pip install -r requirements.txt
```
3. Download the dataset from Kaggle (link above) and place 
   `train.csv` and `store.csv` in the project folder
4. Open and run the notebook
```bash
jupyter notebook rossmann_final_insights.ipynb
```

## References
- Rossmann Store Sales Competition: https://www.kaggle.com/c/rossmann-store-sales
- XGBoost documentation: https://xgboost.readthedocs.io/
- Hyndman, R.J. & Athanasopoulos, G. (2021) Forecasting: Principles and Practice https://otexts.com/fpp3/
- Statsmodels SARIMAX: https://www.statsmodels.org/stable/generated/statsmodels.tsa.statespace.sarimax.SARIMAX.html
