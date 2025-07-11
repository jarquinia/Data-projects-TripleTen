# Sweet Lift Taxi Demand Forecasting

## Project Overview
Sweet Lift Taxi has collected hourly historical data on airport taxi orders. To optimize driver allocation and reduce passenger wait times, we build and compare several models that forecast the number of taxi orders in the next hour.  

## Data
- **Source:** Internal Sweet Lift Taxi database  
- **Frequency:** Hourly (`2018-03-01 00:00:00` to `2018-08-31 23:00:00`)  
- **Target:** `num_orders` (number of taxi orders per hour)

## Feature Engineering
We augment the raw `num_orders` series with:
- **Time features:**  
  - `hour` (0–23)  
  - `day_of_week` (0=Mon–6=Sun)  
  - `month` (1–12)  

All NaNs from shifting/rolling are dropped before modeling.

## Models & Results

| Model                   | Train RMSE | Test RMSE   | Notes                            |
|-------------------------|------------|-------------|----------------------------------|
| Linear Regression       | 26.59      | 46.59       | Underfits complexity             |
| Random Forest           | 13.57      | 44.45       | Overfits; test error still high  |
| Gradient Boosting       | 15.71      | 42.53       | Overfits; moderate improvement   |
| LightGBM                | 14.57      | 39.76       | Best test RMSE; longest training |
| Autoregression (AR)     | —          | 4646.85     | Poor performance                 |

All models show a gap between train/test errors, indicating overfitting. LightGBM achieves the lowest test RMSE but at the cost of longer training time.

