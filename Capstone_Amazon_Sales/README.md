# Target Marketing for Amazon Sales

### <u>Research Question:</u>
- How can I accurately forecast sales for various products and timeframes to optimize inventory levels and identify key drivers of sales across different product categories?

### <u>Data Source:</u>
#### URL: https://data.world/anilsharma87/salesLinks
- The dataset contains historical sales transactions with details on dates, product information, sales amounts, quantities sold, and promotion details. An explanation of the columns is listed below:
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
23. **Unnamed: 22**: An unnamed column that appears to be empty.

### Data Implementation: 
- The primary implementation will be to use time series forecasting methods to capture seasonal and non-seasonal patterns for sales predictions
- The secondary implementation will be to use feature importance to identify features that drive sales higher or lower alongside date-time patterns.
  
---
# Data Exploration Results:
After exploring the sales dataset, these were my findings:
The dataset is an Amazon Sales Report with the following columns:
### Summary Statistics for Numerical Columns:
- **Qty (Quantity)**: The mean quantity of items per order is approximately 0.9, with a minimum of 0 and a maximum of 15. Most orders (75%) contain 1 item.
- **Amount**: The average amount per order is around 648.56 INR, with a wide range from 0 to 5584 INR. The distribution suggests most orders fall below 788 INR.
- **Ship-Postal-Code**: The postal codes range from 110001 to 989898, indicating a broad geographic distribution of shipments.

### Missing Values:
- **Currency** and **Amount** each have 7,795 missing values, suggesting some orders might be missing price data.
- **Promotion-Ids** has 49,153 missing values, indicating that many orders were not associated with any promotions.
- **Fulfilled-By** has 89,698 missing values, possibly indicating missing information on who fulfilled the order.
- **Courier Status** has 6,872 missing values, which could imply missing tracking information for some orders.
- **Ship-City**, **Ship-State**, **Ship-Postal-Code**, and **Ship-Country** each have 33 missing values, showing a small number of orders lacking complete shipping address information.
- The **Unnamed: 22** column appears to be entirely empty or non-informative for the subset of data viewed, with 49,050 missing values.

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

These insights suggest varied buyer preferences and the importance of efficient fulfillment processes. Next, we could look into sales trends over time to understand any temporal patterns or seasonal influences on sales. Would you like to proceed with this analysis or focus on another aspect?

In summary, the exploration of the sales data shows the primary and secondary objectives are able to be accomplished with sales data spanning over a 3 month time period(quarterly). Due to the limited time-series information, modifying the expectations of models will be needed.


What are the chances that the model works as intended vs not as intended
Ethical aspects
