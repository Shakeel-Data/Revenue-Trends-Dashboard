# 📈 Market Trends & Sales Insight | • SQL • Tableau 

Market trends and sales insights play a key role in uncovering actionable patterns within business data. By analyzing category performance, regional demand, and growth trends over time, organizations can make smarter decisions, optimize strategies, and drive sustainable revenue through predictive and data-driven planning.

## 📘 Project Overview
This interactive Revenue Trends Dashboard showcases a comprehensive analysis of sales, profit, and quantity trends across product categories and U.S. states using data-driven insights. Built using Tableau, this project demonstrates the complete data analytics lifecycle — from data sourcing and SQL-based transformation to advanced data visualization and storytelling.

## 📁 Data resources used
- Kaggle 
  - <a href="https://github.com/Shakeel-Data/Revenue-Trends-Dashboard/blob/main/Sales.csv">csv</a>
  - <a href="https://github.com/Shakeel-Data/Revenue-Trends-Dashboard/blob/main/Hexmap.xlsx">map</a>

- SQL
  - <a href="https://github.com/Shakeel-Data/Revenue-Trends-Dashboard/blob/main/Sales.sql">Queries</a>

- SQL exported data
  - <a href="https://github.com/Shakeel-Data/Revenue-Trends-Dashboard/blob/main/Sales.txt">csv</a>


# 🪟 Dashboard
![Dashboard overview](https://github.com/user-attachments/assets/f2732274-267e-41e1-aeaf-c48c5dd17929)

## 🎯 Project Goals
- Developed a comprehensive **Market Trends & Sales Insight dashboard** to uncover key business insights and support **strategic decision-making**.
- Utilized **Microsoft SQL Server for advanced data cleaning, exploration, and transformation** of raw sales data sourced from Kaggle.
- Executed complex SQL queries to calculate essential KPIs such as **total sales, profit margins, quantity sold, and year-over-year growth**.
- Exported refined datasets to CSV format and integrated them into **Tableau for interactive data visualization**.
- Designed and deployed an interactive Tableau dashboard with **dynamic filters and drill-down capabilities, enabling stakeholders to explore category performance, regional sales, and time-series trends**.
- Provided clear visual insights into **high-performing product segments, underperforming regions, and monthly sales fluctuations**.
- Demonstrated full-cycle data analytics skills—from raw data ingestion and SQL-based transformation to **business intelligence reporting and data storytelling**.


## 📈 Key Features
- **End-to-End Pipeline** : Full-cycle project from raw data ingestion to dashboard deployment.
- **SQL Mastery** : Leveraged T-SQL for data wrangling, KPI calculations, and creating export-ready datasets.
- **Interactive Visualization** : Drill-down analysis using Tableau’s parameters and filters.
- **Business Insights** : Uncovered high-performing product segments and top revenue-generating states, aiding in strategic decision-making.



## 🔧 Project Workflow
### 1. 📥 Data Collection & Import
Sourced a publicly available sales dataset from Kaggle, reflecting typical retail transactions. The dataset was imported into Microsoft SQL Server, setting the foundation for structured querying and analysis.

### 2. 🧹 Data Cleaning & Transformation
Using SQL, the raw data was cleaned by handling missing values, correcting inconsistent entries, formatting dates, and optimizing column structures. This ensured that the data was reliable, consistent, and ready for analysis.

```sql
                                                       ---🟢 Exploration Queries---
-- Basic Record Count

SELECT COUNT(*) AS Total_Records FROM Sales;
```
![image](https://github.com/user-attachments/assets/9dc6d1ba-360f-4573-85a3-c3d54ef143a7)

```sql
-- Check for Null Values in Key Columns

SELECT 
     SUM(CASE WHEN [Sales] IS NULL THEN 1 ELSE 0 END) AS Null_Sales,
     SUM(CASE WHEN [Order_Id] IS NULL THEN 1 ELSE 0 END) AS Null_Order_ID
FROM Sales;
```

```sql
-- Total Sales

SELECT SUM(Sales) AS Total_Sales FROM Sales;

```

![image](https://github.com/user-attachments/assets/4ba97531-cf18-4760-b8fa-55e18a615224)



```sql
                                                     ---🟡 Analysis Queries ---
-- Regional Sales Distribution

SELECT [Region], SUM(Sales) AS Region_Sales
FROM Sales
GROUP BY [Region]
ORDER BY Region_Sales DESC;

```
![image](https://github.com/user-attachments/assets/34d301e6-bfa2-4cc4-af5b-266796aa64e4)

```sql
-- Monthly Sales Trend

SELECT FORMAT([Order_Date], 'yyyy-MM') AS Month, SUM(Sales) AS Monthly_Sales
FROM Sales
GROUP BY FORMAT([Order_Date], 'yyyy-MM')
ORDER BY Month;

```

```sql
-- Top 10 Best-Selling Products

SELECT [Product_Name], SUM([Quantity]) AS Units_Sold
FROM Sales
GROUP BY [Product_Name]
ORDER BY Units_Sold DESC
OFFSET 0 ROWS FETCH NEXT 10 ROWS ONLY;
```
![image](https://github.com/user-attachments/assets/819fa2f5-172c-4dc5-ae62-dace5726c49e)

### 3. 🔍 Exploratory Data Analysis (EDA)
Performed in-depth data exploration using a series of SQL queries to uncover key patterns, trends, and outliers. Advanced queries were used to segment data by category, region, and time to better understand business performance from multiple perspectives.

```sql
                                               --- 🔴 Exploratory queries ---

-- Sales, Quantity, and Profit by Category

SELECT 
  [Category],
  SUM(Sales) AS Total_Sales,
  SUM([Quantity]) AS Total_Quantity,
  SUM([Profit]) AS Total_Profit
FROM Sales
GROUP BY [Category]
ORDER BY Total_Sales DESC;

```
![image](https://github.com/user-attachments/assets/2585dd2f-7d77-4f22-82b8-36e66fcc4d6f)

```sql

-- Identify Top Performing Customers

SELECT TOP 10 [Customer_Name], SUM(Sales) AS Total_Sales
FROM Sales
GROUP BY [Customer_Name]
ORDER BY Total_Sales DESC;
```

```sql

-- Yearly Performance Overview

SELECT 
  YEAR([Order_Date]) AS Year,
  COUNT(DISTINCT [Order_ID]) AS Orders,
  SUM(Sales) AS Total_Sales,
  SUM([Profit]) AS Total_Profit
FROM Sales
GROUP BY YEAR([Order_Date])
ORDER BY Year;
```
![image](https://github.com/user-attachments/assets/81adb05c-e385-4ced-af11-f59f3a290722)

```sql

-- Profit Margin by Region and Segment

SELECT 
  [Region], 
  [Segment], 
  AVG([Profit]) AS Avg_Profit_Margin
FROM Sales
GROUP BY [Region], [Segment]
ORDER BY Avg_Profit_Margin DESC;

```

![image](https://github.com/user-attachments/assets/c713a9f5-2fe3-45b5-b41d-3934a36b029e)









































