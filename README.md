# LITA_PROJECT_SALESDATA
### Project Title: Sales Data Analysis

### Project Overview 
---
This project provides an in-depth analysis of sales data to uncover key trends, highlight top-performing products, and understand regional sales distribution. The analysis employs SQL and Power BI to visualize sales insights, identify product and regional performance, and track sales trends over time.

### Data Sources
---
The Primary source of Data used here is SalesData that was provided by Ladies in Tech Africa also known as the Incubator Hub

### Tools Used
---
- Microsoft Exel [Dowload Here](https://www.microsoft.com)
    1. For Data cleaning
    2. For Analysis
    3. For Pivot Tables
- SQL - Structured Query Language for Querying of Data
- Power BI or Visualization
- Github for Portifilio Building

### Data Cleaning and Preparation
---
In the initial phase of the Data cleaning and preparations, I perform the following action;
1. Data loading and Inspection
2. Handling missing variables
3. Data Cleaning and formating

### Exploratory Data Analysis
---
EDA involves the exploring of the Data to answer some question about the Data such as; 
- What is the Total sales by Product, Region, and Month
- What is the Average Sales per Product
- What is Total Revenue by Region
- What is the overall sales trend
- What is the monthly sales
- Top 5 selling product
- What is the quantity sold by product

### SQL-Based Queries:
---
- Retrieve the total sales for each product category. 
- Find the number of sales transactions in each region. 
- Find the highest-selling product by total sales value. 
- Calculate total revenue per product. 
- Calculate monthly sales totals for the current year. 
- Find the top 5 customers by total purchase amount. 
- Calculate the percentage of total sales contributed by each region. 
- Identify products with no sales in the last quarter.

### Power BI Dashboard
---
Visualized key insights like:
- sales overview
- Top-performing products
- Regional breakdowns.
- Sum of quantity by products
- Sales Trend

### Data Analysis
---
This is where I included some basic Excel formulars, some line of code or queries, DAX expressions used during my analysis;

```Excel Formular
Revenue =F2*G2
```

```Excel Formular
Average Sales/Product =AVERAGEIF(C:C,C2,H:H)
```

```Excel Formular
Total Revenue by Region =SUMIF(D:D, D2, H:H)
```

```SQL
Total Sales for each product
SELECT Product, SUM(Revenue) AS TotalSales
FROM SalesData
GROUP BY Product
Order BY 2 desc
```

```SQL
Find the number of sales transactions in each region
SELECT Region, Count(Revenue) AS No_of_Sales_By_Region
FROM SalesData
GROUP BY Region
```

```SQL
Find the highest-selling product by total sales value
SELECT TOP 1 Product, SUM(Revenue) AS TotalSales
FROM SalesData
GROUP BY Product
ORDER BY TotalSales DESC;
```

```SQL
Calculate total revenue per product-
SELECT Product, SUM(Revenue) AS TotalRevenue
FROM SalesData
GROUP BY Product;
```

```SQL
Calculate monthly sales totals for the current year
SELECT 
    DATENAME(MONTH, OrderDate) AS SalesMonth, 
    SUM(Revenue) AS MonthlySales
FROM SalesData
WHERE YEAR(OrderDate) = 2024
GROUP BY DATENAME(MONTH, OrderDate), MONTH(OrderDate)
ORDER BY MONTH(OrderDate);
```

```SQL
Find the top 5 customers by total purchase amount
SELECT TOP 5 Customer_Id, SUM(Revenue) AS TotalSales
FROM SalesData
GROUP BY Customer_Id
ORDER BY 2 DESC;
```

```SQL
Calculate the percentage of total sales contributed by each region
SELECT 
    Region, 
    SUM(Revenue) AS Region_Sales,
    (SUM(Revenue) * 100.0 / (SELECT SUM(Revenue) FROM SalesData) ) AS Sales_Percentage
FROM SalesData
GROUP BY Region;
```

```SQL
Identify products with no sales in the last quarter
SELECT p.Product
FROM (SELECT DISTINCT Product FROM SalesData) p
LEFT JOIN SalesData s ON p.Product = s.Product 
AND s.OrderDate >= '2023-10-01' AND s.OrderDate < '2024-01-01'
WHERE s.Product IS NULL;
```

### Data Visualization

![Excel Formulars](https://github.com/user-attachments/assets/ac78c1f7-447d-4cb0-9753-e34582de8d2f)

#### Pivot Table

![SalesData Pivot Table](https://github.com/user-attachments/assets/3674e6d2-b0ea-4506-b889-34e7b92f51f0)
