# CAPSTONE SALES DATA PROJECT REPORT - LITA PROGRAM 
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
 ALTER table s1 RENAME TO Sales_data
  ;
  
  
  -- ALTER TABLE Sales_data change  `Customer Id`  customerid text;  

  /* Q1:Total numbers of sales for each region 
  We would select product for each region and group the data by product*/
  
  SELECT product, 
  sum(revenue) total_sales
  FROM Sales_data 
  group by product;
  
  
  /* Q2:number of sales in each region 
  we count by order id and group by the region*/
  
  SELECT region, 
  count(orderid) sales_transaction
  From sales_data
  group by region;
  
  
  
  -- Q3: highest selling product : select product and group by product and order by total sales value)
  SELECT product,
  sum(revenue) total_sales 
  From sales_data
  group by product
  order by total_sales desc
  ;
  
  
  -- Q4:Total revenue by product, group answer by product
  SELECT product,
  sum(revenue) total_revenue
  from sales_data
  group by product;
  
  
  -- Q5:monthly sales total for the current year: group the order date by month
  SELECT month(orderdate) as month,
  sum(quantity * UnitPrice) as monthly_sale
  from sales_data
  where year(OrderDate)=year(curdate())
  group by month(orderdate)
  order by month;
  
  
  -- Q6: top 5 customers by total purchase: group by customerid with limit of 5 
  SELECT customerid,
  sum( quantity * unitprice) total_purchase
  from sales_data
  group  by customerid
  order by total_purchase desc
  limit 5;
  

-- Q7: 

SELECT region,
sum(quantity * unitprice) region_sales,
ROUND((sum(quantity* unitprice) / (select sum(quantity * unitprice)
from sales_data) * 100 ) ) as percentage_sales
from sales_data
group by region;


-- Q8: Product with no sale 
SELECT distinct product
from sales_data
where Product not in (
	select product
    from sales_data
    where orderdate >= TIMESTAMPDIFF(quarter, -1, current_date()))
    ;
```

###### On Power BI

![Sales_data analysis 1](https://github.com/user-attachments/assets/4a73d4c2-d473-492c-8ee8-f23d3305c4ee)



![Sales_data analysis 2](https://github.com/user-attachments/assets/a7f9d0c9-f094-4c8c-8800-f6490214f827)




### Feedback
---
This project successfully showcased my ability to clean data, perform in-depth analysis using SQL, and visualize insights effectively in Power BI.

