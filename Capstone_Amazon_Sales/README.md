# Sales Forecasting for Online Markets

#### Research Question:

How can I accurately forecast sales for various products and timeframes to optimize inventory levels and identify key drivers of sales across different product categories?

#### Data Source:

#### URL: https://data.world/anilsharma87/salesLinks

The dataset contains historical sales transactions with details on dates, product information, sales amounts, quantities sold, and promotion details.

#### Implementation Techniques: 

The primary implementation will be to use time series forecasting methods like ARIMA for sales predictions
The secondary implementation will be to use classification models like Random Forest and Gradient Boosting for identifying features that drive sales higher or lower.

#### Expected Results: 

The expectation is to achieve accurate sales forecasts for different timeframes and products, identify features driving sales volumes, and provide actionable insights for inventory optimization.

#### Importance of the Question: 

Managing inventory effectively, reducing stockouts and overstock situations, and maximizing profits through target marketing and promotional strategies.

---
## Results:

### Exploration:
The exploration of data shows the primary and secondary objectives are able to be accomplished with sales data spanding over a 3 month time period(quarterly). Due to the limited time-series information, modifying the expectations of models will be needed.

### Modeling:
##### Time-Series Models:
##### **ARIMA** - poor performance as it doesn't take into account non seasonality

##### **SARIMA** - better performance as it takes into account the fact that there is only 3 months worth of data and setting the seasonal time-frame parameter to 7 days.

##### Regression Models:
Amazing performance across all models finding correlations.
I need to implement GridSearch with the cross validation still to separate modeling performances further
