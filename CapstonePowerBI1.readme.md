# CAPSTONE SALES PROJECT REPORT - LITA PROGRAM 
---



### Overview
---
This capstone project involved analyzing a sales dataset provided in Excel. 
The primary objectives were to clean the data, calculate key metrics both on Excel and SQL, and visualize insights using Power BI. 
The dataset included the following columns: CustomerID, Product, Region, OrderDate, Quantity, and UnitPrice.



### Data Cleaning and Preparation
---
The initial step was to clean the sales datasheet by:
1. Removing Duplicates: Ensured data integrity by eliminating redundant entries.
2. Creating New Columns:
- Total Revenues: Calculated by multiplying Quantity by UnitPrice.
- Average Sales per Product: Derived from total sales data.
3. Pivot tables were created on Excel to summarize sales data and facilitate further analysis.



### SQL Analysis
---
Using SQL, I conducted several key analyses, including:
1. Total Sales by Product Category: Retrieved sales totals to understand category performance.
2. Sales Transactions by Region: Counted transactions to assess regional activity.
3. Highest-Selling Product: Identified the product with the highest total sales value.
4. Total Revenue per Product: Calculated revenue for each product.
5. Monthly Sales Totals for Current Year: Aggregated sales data month by month.
6. Top 5 Customers: Found customers with the highest total purchase amounts.
7. Percentage of Total Sales by Region: Analyzed regional contributions to overall sales.
8. Products with No Sales in Last Quarter: Identified underperforming products.

#### The final step involved creating visualizations in Power BI to present the insights derived from the cleaned dataset and SQL analysis. 



### Data Visualization
---
##### On Excel
---

![CS1](https://github.com/user-attachments/assets/1e7b9c2e-fd06-4a80-9e1e-158fb7a54016)

![CS2](https://github.com/user-attachments/assets/d3d465e2-63fc-46cb-9388-9d3e24bad1f5)

##### 0n SQL 
---
```SQL 
 SELECT * FROM capstone_project.customers_data;

-- Q1: Total number of customers from each region
SELECT region, 
COUNT(customerid) AS total_customers
FROM customers_data
GROUP BY region
;


-- Q2: Most popular subscription type by number of customer: we return 1 row using limit=1
SELECT subscriptiontype, 
COUNT(customerid) AS customer_count
FROM customers_data
GROUP BY subscriptiontype
ORDER BY customer_count DESC
LIMIT 1
;


-- Q3: Customers who cancelled their subscription within 6 months
SELECT customerid, 
customername, 
subscriptionstart, 
subscriptionend, 
canceled
FROM customers_data
WHERE canceled = 'True'  AND duration <= 6
;


-- Q4: Calculate the average subscription for all customers
SELECT AVG(duration) AS average_subscription_duration
FROM customers_data
;


-- Q5: Customers with subscription longer than 12 months
SELECT customerid, 
customername, 
duration
FROM customers_data
WHERE duration > 12
;

-- Q6: Total revenue by subscription type
SELECT subscriptiontype,
SUM(revenue) AS total_revenue
FROM customers_data
GROUP BY subscriptiontype
;


-- Q7: Top 3 regions by subscription cancellations.
SELECT region, 
COUNT(customerid) AS cancelations
FROM customers_data
WHERE canceled = 'True'
GROUP BY region
ORDER BY cancelations DESC
LIMIT 3;

-- Q8: Total number of active and canceled subscriptions
SELECT canceled, COUNT(customerid) AS subscription_count
FROM customers_data
GROUP BY canceled;
```

###### On Power BI








### Feedback
---
This project successfully showcased my ability to clean data, perform in-depth analysis using SQL, and visualize insights effectively in Power BI.

