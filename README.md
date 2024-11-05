# LITA-Capstone-Sales-Data-project
'''
Documentation of The Incubator Hub LITA Capstone Project 1

### Project Overview
'''
This project aims to generate insight of a retail store sales performance such as Top Sellimg product, monthly sales trend and regional performance.

### Data Source
'''
The primary source of the data used is Data sale.Csv

### Tools Used
'''
- Microsoft Excel for
  1. Data Cleaning
  2. Data Analysis
  3. Data Visualization
  
- SQL- Structured Query Language for Querying
  
- Power BI for
  1. Visualization
  2. Interactive Dashboard

- GitHub for Portfolio Building
 
### Data Quality and Preparation
The following operations were performed at the initial phase of the Data
 1. Data loading and inspecrion
 2. Handling missing variables
 3.  Data cleaning and formatting

### Data Analysis
'''
Some basic codes, queries and DAX functions were used during analysis

### Microsoft Excel Analysis
'''
- This is a preview of the Sales Data after it has been cleaned and transformed and some basic calculations were done to get Revenue and Total Sales.
![Sales Cleaned Data](https://github.com/user-attachments/assets/38c63a0c-48d1-497f-ba17-77e9f610cd1d)

### Microsoft Pivot Tables
'''
- Below are the images of the visualization done using pivot Tables and Charts to calculate Total Sales by products, Total Sales by Region and Total Sales by Months.
  ![Sales Pivot](https://github.com/user-attachments/assets/76b66fff-3bc4-42bd-85e3-6491555de498)

 ![Sales Pivot with Chart](https://github.com/user-attachments/assets/9e4ecf04-2ea6-4d92-a60b-80fb2431192e)

 ### SQL - Structured Query Language
 '''
 - Below are the queries used to analyse the Sales Data

   Create Database LITA_PROJECT_1

Select * From [dbo].[SALES_PROJECT_1]

1------- To retrieve total sales for each product category------
Select product, SUM(revenue) as TotalSales from [dbo].[SALES_PROJECT_1]
group by product

2------- Find the number of sales transaction in each region------
Select region, count(*) AS NumberOfSalesTransaction from [dbo].[SALES_PROJECT_1]
group by Region


3-------- Find the highest selling product by total sales value----
Select top 1 product, sum(revenue) as HighestSellingProduct from [dbo].[SALES_PROJECT_1]
group by Product


4-------- Calculate total revenue per product-------
Select product, sum(revenue) as TotalRevenue from [dbo].[SALES_PROJECT_1]
group by Product

5-------- Calculate monthly sales totals for the current year------
-------To create order month column------
Alter Table[dbo].[SALES_PROJECT_1]
Add OrderMonth nvarchar(50)

Update [dbo].[SALES_PROJECT_1]
Set OrderMonth=Datename
 (Month,OrderDate)

 Select * from [dbo].[SALES_PROJECT_1]
------To create orderyear column-----
 Alter Table[dbo].[SALES_PROJECT_1]
Add Orderyear int

Update [dbo].[SALES_PROJECT_1]
Set OrderYear=Year(OrderDate)

Select
OrderMonth,Sum(Quantity)As
TotalSales
FROM [dbo].[SALES_PROJECT_1]
Where OrderYear=2024
Group By OrderMonth

Select
    Format(Orderdate,'yyyy-mm') As sales_month,
	Sum(Revenue) As monthly_sales_total
From
    [dbo].[SALES_PROJECT_1]
	Where
	Year (OrderDate) = 2024
Group By
	Format(OrderDate, 'yyyy-mm')
Order By
	Format(OrderDate, 'yyyy-mm')


6------- find the top 5 customers by total purchase amount------
Select Top 5 Customer_Id,sum(revenue) As TotalPurchase from [dbo].[SALES_PROJECT_1]
Group By Customer_Id



7--------Calculate the percentage of totalsales contributed by each region-----
Select Region,
	Sum(Revenue)/(SUM(Quantity)*0.1) As percentage_of_TotalSales
	From [dbo].[SALES_PROJECT_1]
Group By Region
Order By Percentage_Of_TotalSales


------- Identify product with no sales in the last quarter-------
Select Product,Sum(Quantity) As Sales 
From [dbo].[SALES_PROJECT_1]
Where Month (OrderDate) Between 10 and 12             ----(October to December)
Group By Product
Having
Sum(Quantity)= 0


### Power BI Visuals and Tables used for Analysis

![Sales BI](https://github.com/user-attachments/assets/7cbdc7a5-308d-499c-a96e-62181fb4a503)




   




