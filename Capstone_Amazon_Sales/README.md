---
# Marketing with Amazon Sales
## Sales Performance, Feature Importance and Forecasting
---
### Goal:
The goal of the project is to leverage historical sales data to unearth patterns, trends, and seasonality in sales performances across various categories, fulfillment methods, and sales channels. The insights garnered from this analysis aim to accurately predict future sales, thereby assisting in strategic decision-making related to inventory management and sales optimization.

### Data Source:
**URL:** https://data.world/anilsharma87/sales

- The dataset contains historical sales transactions with details on dates, product information, sales amounts, quantities sold, and promotion details from an e-commerce business partnered with Amazon.
- The dataset (Amazon Sales Report) contains the following columns:

1. **Order ID**: Unique identifier for each order.
2. **Date**: The date on which the order was placed.
3. **Status**: Current status of the order (e.g., Cancelled, Shipped, Delivered).
4. **Fulfilment**: Whether the item was fulfilled by the merchant or Amazon.
5. **Sales Channel**: The platform through which the sale was made.
6. **Ship-Service-Level**: Shipping service level (e.g., Standard, Expedited).
7. **Style**: Style identifier for the product.
8. **SKU**: Stock Keeping Unit, a unique identifier for each product.
9. **Category**: Category of the product (e.g., Set, Kurta, Western Dress).
10. **Size**: Size of the product.
11. **Color**: Color of the product.
12. **Quantity**: Number of units sold in the order.
13. **Item Price**: Price of the item.
14. **Currency**: Currency of the transaction.
15. **Amount**: Total amount of the order.
16. **Ship-City**: City where the product was shipped.
17. **Ship-State**: State where the product was shipped.
18. **Ship-Postal-Code**: Postal code of the shipping address.
19. **Ship-Country**: Country where the product was shipped.
20. **Promotion-Ids**: IDs of any promotions applied to the order.
21. **B2B**: Indicates if the order was a business-to-business transaction.
22. **Fulfilled-By**: Specifies who fulfilled the order (e.g., Easy Ship).
23. **Unnamed: 22**: An unnamed column that is Empty

### Data Problem:
Handling the dataset's complexity, including the variety of product categories, fulfillment methods, and sales channels, poses a significant challenge. The data may contain missing values, outliers, or inconsistencies that need to be meticulously cleaned and processed. Additionally, accurately modeling time-series data requires dealing with seasonality, trend components, and potential shifts in consumer behavior over time.

### Business Problem:
The project addresses the critical business need to forecast sales accurately, facilitating optimized inventory management, effective resource allocation, and strategic planning. Incorrect forecasts could lead to inventory issues, such as stockouts or overstocking, negatively impacting customer satisfaction and financial performance.

### Risks:
- **Overfitting**: Models may perform well on historical data but fail to generalize to future data.
- **Underestimation of External Factors**: Changes in market conditions, consumer behavior, or unforeseen events (like a pandemic) can significantly affect sales trends.
- **Data Quality**: Inaccurate or incomplete data can lead to misleading insights and predictions.

### Assumptions:
- Historical sales trends and patterns will continue into the future, making past data a reliable indicator of future sales.
- The dataset adequately represents the market and consumer behavior, without significant biases.
- External factors not included in the dataset (e.g., economic conditions, competitor actions) will have a consistent impact over the forecast period.

### Expected Results:
- A comprehensive analysis of sales trends, identifying key drivers of sales across different categories and fulfillment methods.
- Accurate sales forecasts for various product categories, enabling better inventory planning and resource allocation.
- Insights into the impact of different sales channels and fulfillment methods on sales performance, guiding strategic decisions.

### Machine Learning Models:
The chosen machine learning models were:

- **DecisionTreeRegressor**: Good for capturing nonlinear relationships, though prone to overfitting if not properly constrained.
- **XGBRegressor**: Effective for various types of regression tasks, offering high performance and the ability to handle complex interactions between features.
- **LGBMRegressor**: Efficient for large datasets, with the 'force_col_wise' parameter enhancing its ability to manage data effectively, particularly useful for handling categorical features.
- **GradientBoostingRegressor**: Offers flexibility in optimizing different loss functions, beneficial for improving the accuracy of predictions.
- **RandomForestRegressor**: An ensemble method that can improve prediction accuracy and robustness by averaging multiple decision trees, reducing the risk of overfitting.

##### Reasoning:
- I chose to go with these models due to the data timeframe being less than 3 months.
---
# Findings pt.1
## Exploration of Sales Performance:
---

#### Summary Statistics for Numerical Columns:
- **Qty (Quantity)**: The mean quantity of items per order is approximately 0.9, with a minimum of 0 and a maximum of 15. Most orders (75%) contain 1 item.
- **Amount**: The average amount per order is around 648.56 INR, with a wide range from 0 to 5584 INR. The distribution suggests most orders fall below 788 INR.
- **Ship-Postal-Code**: The postal codes range from 110001 to 989898, indicating a broad geographic distribution of shipments.

#### Missing Values:
- **Currency** and **Amount** each have 7,795 missing values, suggesting some orders might be missing price data.
- **Promotion-Ids** has 49,153 missing values, indicating that many orders were not associated with any promotions.
- **Fulfilled-By** has 89,698 missing values, possibly indicating missing information on who fulfilled the order.
- **Courier Status** has 6,872 missing values, which could imply missing tracking information for some orders.
- **Ship-City**, **Ship-State**, **Ship-Postal-Code**, and **Ship-Country** each have 33 missing values, showing a small number of orders lacking complete shipping address information.
- The **Unnamed: 22** column appears to be empty or non-informative for the subset of data viewed, with 49,050 missing values.

### Distribution Insights
#### Order Status:
- The majority of orders are marked as **Shipped** (77,804), followed by **Shipped - Delivered to Buyer** (28,769), indicating successful fulfillment and delivery for a significant portion of orders.
- **Cancelled** orders account for 18,332, highlighting a notable amount of transactions not reaching completion.
- Smaller categories like **Shipped - Returned to Seller** (1,953) and **Shipped - Picked Up** (973) suggest occasional issues with orders or changes in buyer decisions.

#### Fulfilment:
- A significant majority of orders are fulfilled by **Amazon** (89,698), suggesting a strong reliance on Amazon's fulfillment services.
- **Merchant**-fulfilled orders are less common but still significant, with 39,277 occurrences, indicating a mix of fulfillment strategies among sellers.

#### Product Category:
- **Set** (50,284) and **Kurta** (49,877) are the most popular categories, showing a strong preference for these types of apparel.
- **Western Dress** (15,500) and **Top** (10,622) follow, indicating a diverse range of fashion preferences among buyers.
- Categories like **Ethnic Dress**, **Blouse**, **Bottom**, **Saree**, and **Dupatta** represent more niche markets within the dataset.

These insights suggest varied buyer preferences and the importance of efficient fulfillment processes.

---
# Findings pt.2
## Evaluating Feature Importance:
---
#### ML Models & Model Scoring:
- The baseline model to beat was the decision tree regressor. After evaluation of the baseline models without cross-validation, the decision tree regressor was overfitting. The two models performed the best regarding efficiency and accuracy; XGBRegressor & LGBMRegressor comparably performed almost the same.

| Model                       | RMSE Train Set | RMSE Test Set | MAE Train Set | MAE Test Set | R2 Train Set | R2 Test Set | Time(sec) |
|---------------------------- |----------------|---------------|---------------|--------------|--------------|-------------|-----------|
| DecisionTreeRegressor       | 2.060973       | 2.115008      | 1.439068      | 1.466884     | 0.591185     | 0.570640    | 0.102439  |
| XGBRegressor                | 2.063418       | 2.087704      | 1.442005      | 1.461708     | 0.590215     | 0.581654    | 0.204608  |
| LGBMRegressor               | 2.074023       | 2.083649      | 1.449042      | 1.461766     | 0.585992     | 0.583277    | 0.171876  |
| GradientBoostingRegressor   | 2.094923       | 2.098785      | 1.469020      | 1.477932     | 0.577606     | 0.577201    | 4.776895  |
| RandomForestRegressor       | 2.063998       | 2.087109      | 1.441569      | 1.462649     | 0.589984     | 0.581893    | 5.873551  |


-  After a grid search on the top 2 performing models, the difference in RMSE score to confirm the best model was by  
- 
---
# Next Steps pt.3
## Unsupervised Modeling & Target Pricing:
---
#### Business Deployment:
Deploying the model as is would result in a mean average percentage error (MAPE) of 17.43%. One of the challenges of forecasting marketing data is when there is not a full year's worth of data points. Although this model is trained without a full year of data points, the model's performance is outstanding. This
