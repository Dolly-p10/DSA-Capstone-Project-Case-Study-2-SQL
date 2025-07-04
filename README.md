# DSA-Capstone-Project-Case-Study-2-SQL

## Kultra Mega Stores Inventory Analysis

### Project Overview

This project focuses on analyzing KMS order data using SQL queries. The goal is to derive meaningful insights and findings by answering key business questions related to customer behavior, shipping efficiency, product performance, and regional sales patterns.

### Data Sources

The dataset was sourced from a Digital Learning Management System (LMS) platform as part of a case study project.

### Project Problem

Kultra Mega Stores (KMS) is seeking to understand how customer behavior, product preferences, and shipping choices impact revenue, returns, and operational efficiency. However, they lack structured insight from historical order data to make data-informed decisions.

### Project Objective

To analyze KMS's sales and order data using SQL, identify revenue drivers and inefficiencies, uncover customer trends, and deliver actionable insights that can guide strategy and improve overall business performance.

### Steps Followed

- Data Understanding – Reviewed table structures, fields, and key relationships.
- Query Development – Wrote SQL queries to analyze customer behavior, product sales, discounts, shipping mode efficiency, and more.
- Performance Optimization – Applied efficient SQL practices using GROUP BY, JOIN, DISTINCT, WHERE and filtering logic.
- Data Validation – Ensured data integrity and correctness of logic through sample cross-checks and breakdowns.
- Insights & Reporting – Interpreted results, documented insights, and proposed practical business recommendations.

### Tools Used
MS SQL Server
- For querying and analysis
- For data import and exploration

### Exploratory Data Analysis

Key business questions answered:
- What are the Top 3 and Bottom 3 regions in terms of sales?
- Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
- Who are the most valuable customers, and what products or services do they typically purchase?
- Which customer returned items, and what segment do they belong to?
- Which Corporate customer placed the most number of orders between 2009 and 2012?
- If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority?

###  Key Insights
- Technology was the highest revenue-generating category with over 5.98 million in sales.
- The West, Ontario, and Prarie were the top performing regions by total sales.
- The Corporate segment had the highest number of returns (167 customers).
- Delivery Truck was heavily used even for low-priority orders, leading to potentially excessive shipping costs.
- Emily Phan was the most profitable consumer customer, generating 34,005.44 in profit.

### Data Analysis Techniques

Here are the SQL Queries used:

``` SQL
---Most valuable customers
select top 10 Customer_Name, sum(Sales) as [Total Revenue]
       from [dbo].[KMS Sql Case Study]
group by Customer_Name
order by [Total Revenue] desc

select distinct k.Customer_Name, k.Customer_Segment
from [dbo].[KMS Sql Case Study] as k
join [dbo].[Order_Status] as s
   on k.Order_ID = s.Order_ID
where s.Status = 'Returned'
