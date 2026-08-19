# SQL_query
📊 Sales Data Analysis using SQL
📌 Project Overview
This project focuses on analyzing sales data using SQL to extract meaningful business insights related to products, sales representatives, regions, product categories, payment methods, and sales performance.
The project demonstrates practical SQL skills such as aggregate functions, subqueries, GROUP BY, CASE statements, Common Table Expressions (CTEs), and window functions.
________________________________________
🎯 Project Objectives
The main objectives of this project are:
•	Analyze overall sales performance.
•	Identify highest and lowest-selling products.
•	Find the second and third highest sales/quantity values.
•	Rank regions based on total sales.
•	Rank product categories based on sales.
•	Identify high-performing payment methods.
•	Analyze Sales Representative performance.
•	Find top-performing Sales Reps by region.
•	Categorize Sales Rep performance.
•	Analyze regional sales performance.
________________________________________
🗂️ Dataset
The project uses a sales dataset named:
sales_data
Important Columns
Column	Description
Product_ID	Unique product identifier
Product_Category	Category of the product
Sales_Channel	Channel through which the sale occurred
Region	Sales region
Sales_Rep	Sales representative
Sales_Amount	Amount generated from the sale
Quantity_Sold	Number of units sold
Payment_Method	Payment method used
________________________________________
🔍 SQL Analysis Performed
1. Product Analysis
•	Counted distinct Product IDs.
•	Identified products with the highest sales amount.
•	Identified products with the lowest sales amount.
•	Found the second-highest sales amount.
2. Regional Analysis
•	Calculated total sales by region.
•	Calculated average sales by region.
•	Ranked regions according to total sales.
•	Identified the highest-selling transaction in each region.
3. Product Category Analysis
•	Ranked product categories based on total sales.
•	Found the highest quantity sold for each category.
•	Found the second-highest quantity sold.
•	Identified the third-highest quantity sold within each category.
4. Sales Representative Analysis
•	Calculated total sales for each Sales Rep.
•	Calculated total quantity sold by each Sales Rep.
•	Identified the top 3 Sales Reps.
•	Found Sales Reps with sales greater than 100,000.
•	Categorized Sales Rep performance as:
o	Excellent
o	Good
o	Low
•	Analyzed individual Sales Rep performance by region.
•	Identified the top 2 Sales Reps in each region.
5. Payment Method Analysis
Payment methods were ranked based on their total sales contribution to identify which payment methods generated the highest sales.
________________________________________
🛠️ SQL Concepts Used
This project demonstrates the following SQL concepts:
•	SELECT
•	WHERE
•	DISTINCT
•	COUNT()
•	SUM()
•	AVG()
•	MAX()
•	MIN()
•	GROUP BY
•	ORDER BY
•	Subqueries
•	Common Table Expressions (WITH)
•	CASE WHEN
•	DENSE_RANK()
•	ROW_NUMBER()
•	PARTITION BY
•	Aggregate functions
•	Window functions
•	Filtering ranked results
________________________________________
📈 Key SQL Techniques
Ranking Regions
SELECT
    Region,
    SUM(Sales_Amount) AS Total_Sales,
    DENSE_RANK() OVER (
        ORDER BY SUM(Sales_Amount) DESC
    ) AS Sales_Rank
FROM sales_data
GROUP BY Region;
Top 2 Sales Reps in Each Region
WITH rankby_totsales AS (
    SELECT
        Sales_Rep,
        Region,
        SUM(Sales_Amount) AS Total_Sales,
        DENSE_RANK() OVER (
            PARTITION BY Region
            ORDER BY SUM(Sales_Amount) DESC
        ) AS Sales_Rank
    FROM sales_data
    GROUP BY Sales_Rep, Region
)
SELECT
    Sales_Rep,
    Region,
    Total_Sales,
    Sales_Rank
FROM rankby_totsales
WHERE Sales_Rank <= 2;
________________________________________
💡 Business Insights
The analysis can help businesses understand:
•	Which products generate the highest revenue.
•	Which regions contribute the most to total sales.
•	Which product categories perform better.
•	Which Sales Reps are contributing the most revenue.
•	Which payment methods are associated with higher sales.
•	Which Sales Reps perform best within individual regions.
•	Where sales performance may need improvement.
________________________________________
📁 Project Structure
Sales-Data-Analysis/
│
├── sales_data.csv
├── Sales_Data_Analysis.sql
└── README.md
________________________________________
🚀 Skills Demonstrated
SQL | Data Analysis | Business Intelligence | Data Cleaning | Aggregation | Window Functions | Subqueries | CTE | Ranking | Business Insights
________________________________________
👩‍💻 Author
Anusharani Balraj
This project was created as part of my Data Analytics / SQL learning portfolio to demonstrate practical SQL querying and business analysis skills.
