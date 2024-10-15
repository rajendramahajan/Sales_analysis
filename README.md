# Sales Analysis Project

The **Sales Insights Data Analysis** project is designed to analyze sales data using MySQL for data extraction and processing, and Power BI for advanced visualization and reporting. This project provides a comprehensive overview of sales performance across multiple markets, including product-specific sales, market trends, and overall revenue generation, with a focus on delivering actionable insights to inform business decisions.

## Project Overview

This project involves the use of MySQL for querying the dataset and Power BI for creating visual insights. The analysis covers various aspects of sales, such as customer data, market-specific transactions, and revenue generation.

### Key Objectives:
- **Product-wise Sales**: Analyze sales by product category to identify top-performing products.
- **Market Trends**: Evaluate sales performance across different markets.
- **Revenue Insights**: Generate actionable insights to optimize revenue growth.

## Prerequisites
- MySQL installed on your local machine.
- Power BI Desktop for data visualization.
- Basic understanding of SQL queries.

## Getting Started

### Step 1: Database Setup
- Download the `db_dump.sql` file from this repository.
- Import the SQL dump into your local MySQL database.

### Step 2: Data Analysis Using MySQL
**Show all customer records**  
 SELECT * FROM customers;

**Show the total number of customers**
 SELECT COUNT(*) FROM customers;

**Show transactions for the Chennai market (market code: Mark001)**
SELECT * FROM transactions WHERE market_code = 'Mark001';

**Show distinct product codes sold in Chennai**
SELECT DISTINCT product_code FROM transactions WHERE market_code = 'Mark001';

**Show transactions where currency is US Dollars (USD)**
SELECT * FROM transactions WHERE currency = 'USD';

**Show transactions for the year 2020 (joined with the date table)**
SELECT transactions.*, date.* 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020;

**Show total revenue for the year 2020**
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND (transactions.currency = 'INR' OR transactions.currency = 'USD');

**Show total revenue for January 2020**
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND date.month_name = 'January' 
AND (transactions.currency = 'INR' OR transactions.currency = 'USD');

**Show total revenue for 2020 in the Chennai market**
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND transactions.market_code = 'Mark001';

**Step 3: Data Visualization Using Power BI**
After performing the SQL queries, the data is loaded into Power BI for further analysis and visualization.

**Normalization Formula:**
This formula normalizes the sales amount to INR if the currency is in USD.
Table.AddColumn(#"Filtered Rows", "norm_amount", 
each if [currency] = "USD" then [sales_amount] * 75 else [sales_amount], type any)

**Interactive Dashboards:**
Visualize the sales trends, market-specific revenues, and customer behavior in Power BI.

### Tools & Technologies
MySQL: For querying and data extraction.
Power BI: For advanced reporting and data visualization.







   
