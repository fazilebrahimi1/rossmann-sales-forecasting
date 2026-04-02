# Rossmann Store Sales Forecasting

A time series forecasting project comparing SARIMA, ARIMA, and XGBoost 
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
├── rossmann_forecasting_project.ipynb  # Main notebook
├── requirements.txt                     # Dependencies
└── README.md                            # This file
```

## Methods
| Model | Description |
|-------|-------------|
| SARIMA(1,1,1)(1,1,1,52) | Classical seasonal model, baseline |
| Prophet | Additive model with holiday regressors |
| XGBoost | Gradient boosted trees with lag + promo features |

## Key Findings
- Promotions are the single strongest predictor of weekly sales
- XGBoost achieves the best accuracy by capturing promotional signals
- Prophet provides the most interpretable decomposition of trend, 
  seasonality and holiday effects
- SARIMA correctly identifies the annual seasonal pattern but cannot 
  incorporate external features like promotions

## Evaluation Metrics
Models are compared using MAE, RMSE, and MAPE on a held-out 
test set (last 20% of weeks).

## How to Run
1. Clone this repository
```bash
git clone https://github.com/YOURUSERNAME/rossmann-sales-forecasting.git
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
jupyter notebook rossmann_forecasting_project.ipynb
```

## References
- Rossmann Store Sales Competition: https://www.kaggle.com/c/rossmann-store-sales
- Prophet documentation: https://facebook.github.io/prophet/
- XGBoost documentation: https://xgboost.readthedocs.io/
- Hyndman, R.J. & Athanasopoulos, G. (2021) Forecasting: Principles 
  and Practice https://otexts.com/fpp3/
