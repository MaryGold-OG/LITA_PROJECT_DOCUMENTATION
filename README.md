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
---
![Excel Formulars](https://github.com/user-attachments/assets/ac78c1f7-447d-4cb0-9753-e34582de8d2f)

#### Pivot Table
---
![SalesData Pivot Table](https://github.com/user-attachments/assets/3674e6d2-b0ea-4506-b889-34e7b92f51f0)

#### SQL Queries
---
![Query 1](https://github.com/user-attachments/assets/76920eb3-faee-4b6a-b6bf-79763f9cbab2)

![Query 2](https://github.com/user-attachments/assets/90196381-80b3-4403-bf2f-143f31dc59b0)

![Query 3](https://github.com/user-attachments/assets/84b54f88-8f50-4b04-89f4-94b3fceb5487)

![Query 4](https://github.com/user-attachments/assets/69a32098-2d49-4187-b757-233a034a365a)

![Query 5](https://github.com/user-attachments/assets/893bd317-1837-4641-8480-b651c64f0ff4)

![Query 6](https://github.com/user-attachments/assets/b6701631-bfa3-42b0-a004-482f73b5b778)

![Query 7](https://github.com/user-attachments/assets/b3d1d6c1-2d0b-402f-b981-d9f90371e6d7)

![Query 8](https://github.com/user-attachments/assets/ffb4f786-21fb-4793-9a60-ce26c1770fb0)

### Power BI Dashboard
---

![Sales Data Dashboard](https://github.com/user-attachments/assets/0d43b9b0-0576-4c20-9176-1f9b6a7c45b5)


### Key Insights
---
- Top Products by Sales Value
    1. Shoes: ₦613,380
    2. Shirt: ₦485,600
    3. Hat: ₦316,195
- Top Products by Quantity Sold
    1. Hat: 15,929 units
    2. Shoes: 14,402 units
    3. Shirt: 12,388 units
#### Regional Breakdown
- Top 3 Regions by Sales Revenue:
    1. South: ₦927,820
    2. East: ₦485,925
    3. North: ₦387,000
    4. Lowest Revenue Region: The West with ₦300,345
#### Quarterly Sales Patterns
- No Sales in Last Quarter: Shoes, Hat, and Shirt showed no sales in the most recent quarter.
#### Sales Trends
- Highest Revenue Year: 2024, with peak sales recorded in February 2024.
- Lowest Sales Period: April 2023 saw the lowest sales performance.

### Recommendation
---
- Given that Shoes, Shirts, and Hats are top-performing products, allocate additional marketing resources to further boost their sales. This could involve bundled offers, discounts, or loyalty incentives to capitalize on their high revenue potential. Meanwhile, Gloves, Socks, and Jackets, which showed lower performance, may benefit from a rebranding strategy. Repositioning these items with refreshed designs, targeted marketing efforts, or promotional campaigns to increase their visibility and appeal in the market can be considered.

- With the West region showing the lowest revenue, implementing a targeted strategy could help boost sales. Start by analyzing customer preferences within this region to identify potential gaps in product offerings or delivery channels. Addressing these gaps—whether by adjusting the product lineup, optimizing delivery options, or creating region-specific promotions—may significantly enhance sales performance in this underperforming area.

- Since Shoes, Hats, and Shirts had no sales in the last quarter, investigating potential causes, such as seasonal demand shifts, stock issues, or reduced marketing efforts during this period is essential. it is also important to plan marketing/sales strategy towards that season to help sustain sales momentum

- With February 2024 as the peak sales month, I will recommend planning of promotions and inventory in advance for early 2025 to maximize sales during this high-performing period.

- Since April 2023 had the lowest sales, considering strategies to boost demand during this slow month, such as limited-time offers, increased product visibility, or new product launches will help increase sales.
