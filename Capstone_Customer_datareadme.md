# CAPSTONE CUSTOMER DATA REPORT - LITA PROGRAM
---



### Overview
---
In this capstone project, I analyzed a customer dataset provided in Excel, with a focus on cleaning, calculating key metrics, and visualizing customer insights. 
The dataset included columns such as Customer ID, Customer Name, Region, Subscription Type, Subscription Start, Subscription End, Cancelled, and Revenue.

### Data Cleaning and Preparation
---

To prepare the dataset for analysis, I:
1. Removed Duplicates: Ensured data integrity by eliminating repeated entries.
2. Created New Columns:
- Duration: Calculated for each customer based on subscription start and end dates.
- Average Duration: Derived for all customers to understand typical subscription lengths.
3. Pivot tables were also created to summarize key metrics by customer segments and regions.

### SQL Analysis
---
I performed various analyses using SQL to derive insights from the data, including:
1. Total Number of Customers by Region: Counted customers to analyze regional distribution.
2. Most Popular Subscription Type: Identified by the number of customers.
3. Cancellations within 6 Months: Found customers who canceled early.
4. Average Subscription Duration: Calculated to gauge customer retention.
5. Subscriptions Longer than 12 Months: Listed long-term customers.
6. Total Revenue by Subscription Type: Aggregated revenue by type.
7. Top 3 Regions by Cancellations: Ranked regions with the most cancellations.
8. Total Active and Canceled Subscriptions: Counted for an overview of subscription status.

###  Power BI Visualization
---
I created an interactive dashboard to visualize key customer insights, including:
1. Customer Segments and Trends: Displayed subscription patterns by segment.
2. Cancellations by Region and Duration: Visualized early cancellations and trends.
3. Subscription Types: Showed popularity and revenue by subscription type.
4. Interactive slicers were added for filtering by region, subscription type, and status.


### Data Visualization
---
##### On Excel 
---

![CC1](https://github.com/user-attachments/assets/dd0eb16c-9169-44b7-9d80-17e9160757bd)


![CC2](https://github.com/user-attachments/assets/02f3fba0-286c-46ee-be12-195a388df97c)


##### On SQL
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


##### On Power BI


![Cusomer_data](https://github.com/user-attachments/assets/c57e8311-e977-4d21-b913-fbe6834cc700)





### Feedback
---
This project highlighted my skills in data cleaning, SQL analysis, and visual storytelling using Power BI.
