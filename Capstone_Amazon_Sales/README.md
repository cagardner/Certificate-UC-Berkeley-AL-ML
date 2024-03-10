# Marketing with Amazon Sales
### Sales Performance Analysis and Forecasting

#### Goal:
The goal of the project is to leverage historical sales data to unearth patterns, trends, and seasonality in sales performances across various categories, fulfillment methods, and sales channels. The insights garnered from this analysis aim to accurately predict future sales, thereby assisting in strategic decision-making related to inventory management and sales optimization.

#### Data Source:
**URL:** https://data.world/anilsharma87/sales

The dataset contains historical sales transactions with details on dates, product information, sales amounts, quantities sold, and promotion details from an e-commerce business partnered with Amazon.

#### Data Problem:
Handling the dataset's complexity, including the variety of product categories, fulfillment methods, and sales channels, poses a significant challenge. The data may contain missing values, outliers, or inconsistencies that need to be meticulously cleaned and processed. Additionally, accurately modeling time-series data requires dealing with seasonality, trend components, and potential shifts in consumer behavior over time.

#### Business Problem:
The project addresses the critical business need to forecast sales accurately, facilitating optimized inventory management, effective resource allocation, and strategic planning. Incorrect forecasts could lead to inventory issues, such as stockouts or overstocking, negatively impacting customer satisfaction and financial performance.

#### Risks:
- **Overfitting**: Models may perform well on historical data but fail to generalize to future data.
- **Underestimation of External Factors**: Changes in market conditions, consumer behavior, or unforeseen events (like a pandemic) can significantly affect sales trends.
- **Data Quality**: Inaccurate or incomplete data can lead to misleading insights and predictions.

#### Assumptions:
- Historical sales trends and patterns will continue into the future, making past data a reliable indicator of future sales.
- The dataset adequately represents the market and consumer behavior, without significant biases.
- External factors not included in the dataset (e.g., economic conditions, competitor actions) will have a consistent impact over the forecast period.

#### Expected Results:
- A comprehensive analysis of sales trends, identifying key drivers of sales across different categories and fulfillment methods.
- Accurate sales forecasts for various product categories, enabling better inventory planning and resource allocation.
- Insights into the impact of different sales channels and fulfillment methods on sales performance, guiding strategic decisions.

#### Machine Learning Models:
The chosen models are well-suited for regression tasks and can handle the dataset's complexity:

- **DecisionTreeRegressor**: Good for capturing nonlinear relationships, though prone to overfitting if not properly constrained.
- **XGBRegressor**: Effective for various types of regression tasks, offering high performance and the ability to handle complex interactions between features.
- **LGBMRegressor**: Efficient for large datasets, with the 'force_col_wise' parameter enhancing its ability to manage data effectively, particularly useful for handling categorical features.
- **GradientBoostingRegressor**: Offers flexibility in optimizing different loss functions, beneficial for improving the accuracy of predictions.
- **RandomForestRegressor**: An ensemble method that can improve prediction accuracy and robustness by averaging multiple decision trees, reducing the risk of overfitting.

---
# Findings
