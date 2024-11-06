# Adeyemo Oluwatoyosi Gorgeous LITA Project (Sales Data)

## Project Title: _*A Retail Store Sales Performance*_

---
### Content
---
[Project Briefing](#project-briefing)

[Data Origins](#data-origins)

[Data Tools Used](#data-tools-used)

[Data Preprocessing](#data-preprocessing)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Visual Data Presentation](#visual-data-presentation)

[Outcome](#outcome)

### Project Briefing
---
  This Data Analysis Project is aimed focused on analysing the sales record of a retail store. Exploring the sales dataset to reveal and uncover key perceptions such as the sales trends of all the products, top-selling products, regional sales trends and monthly sales trend. Generating an interactive dashboard that features these trends.
  
### Data Origins
---
  The data was provided by The Incubator Hub: Ladies in Tech.
  
### Data Tools Used
---
  - Microsoft Excel [Download here](https://www.microsoft.com)
      1. *For Data cleaning*
      2. *For Analysis*
      3. *For summarizing the sales report*
      4. *For creating addition colunm by using mathematical formular to get the Sales/Revenue*
      5. *For creating metrics that show/calculate the average sales per product and total revenue by region*
  - SQL (Structured Query Language)
      1. *For Creating a database*
      2. *For quering data*
  - Power BI
      1. *For Data Visualisation*
      2. *For transform data to show the column quality, column distribution and column profile. This is to show if there is any error, blank cell or if the columns are valid.*
      3. *For creating new measure that calculate sum of Sales and count of customers.*

### Data Preprocessing
---
  In this aspect, which is cleaning and preparation of the dataset, the following was performed;
- Data Loading
- Data Inspection
- Removal of Duplicates
- Adding of necessary column (Revenue Colunm)
- The column quality, distribution and profile were checked.
    
  ### Exploratory Data Analysis
---
Exploratory Data Analysis (EDA) is an interative process of analyzing and visualizing data to understand its fundamental structure, patterns, most importantly relationships.
  This involves the use of pivot tables and SQL commands to make an exploration of the data to answer questions about the data, such as;
  - The total sales for each product
  - The number of sales transactions in each region
  - The highest-selling product by total sales valve
  - The total revenue per product
  - The monthly sales total for the current year
  - The top 5 customers by total purchase amount
  - The percentage of total sales contributed by each region 
  - The average sales for each product
  - The total revenue for each region.

![Sales Pivot Table](https://github.com/user-attachments/assets/358618da-6e6e-4938-ad79-fcd7d2997e37)

![SQL sales 1](https://github.com/user-attachments/assets/4435c664-80af-4e5e-ad86-19a048a1fadb)

![Sql Sales 2](https://github.com/user-attachments/assets/0e2eaf8c-af32-4e69-9495-6645d5cb533e)


### Data Analysis
---
The following are some of the formulars and queries used:
```EXCEL
    =PRODUCT(F2,G2)
```
```EXCEL
    =SUMIF(D:D,K4,H:H)
```
```EXCEL
    =AVERAGEIF(C:C,K12,H:H)
```
```SQL
    Create database Gorgeous_Project
```SQL
    select SUM(Total_Sales)as Total_Sales_per_Product, [Product]
	from [dbo].[Sales Data]
	group by [Product]
```
```SQL
    select Region, 
	COUNT(*) AS Num_of_Sales_Transactions
	from [dbo].[Sales Data]
	group by 
	region
```
```SQL
    select [Product],
	max(Total_Sales) as Total_Sales_Value
	from [dbo].[Sales Data]
	group by [Product]
	order by Total_Sales_Value DESC
```
```SQL
    select[Product],
	sum([Total_Sales]) as Total_Revenue
	from [dbo].[Sales Data]
	group by [Product]
```
```SQL
    Alter Table [dbo].[Sales Data]
	add Order_Month nvarchar(50)
```
```SQL
    Update [dbo].[Sales Data]
	set Order_Month = Datename(Month,OrderDate)
```
```SQL
    Alter Table [dbo].[Sales Data]
	add Order_Year int
```
```SQL	
Update [dbo].[Sales Data]
	set Order_Year = Year(orderdate)
```
```SQL
  Select * from [dbo].[Sales Data]
```
```SQL
  Select [Order_Month],
	sum([Total_Sales]) as TotalSales
	from [dbo].[Sales Data]
	where [Order_Year] = 2024
	group by Order_Month
	order by order_Month asc
```
```SQL
  Select top 5[Customer_Id],
	sum([Total_Sales]) as TotalSales
	from [dbo].[Sales Data]
	group by Customer_Id
```
```SQL
  Select Region,
	sum(Total_Sales) as TotalSales,
	Round((sum(Total_Sales) / Nullif((Select sum(Total_Sales)
	from [dbo].[Sales Data]), 0) * 100), 2) as 
	Percentage_of_Total_Sales
	from [dbo].[Sales Data]
	group by Region
```

### Visual Data Presentation
---

![Dashboard Sales](https://github.com/user-attachments/assets/ef94ccf1-0809-4a66-bc0a-66bb0244075e)

### Outcome
---
These analyses can recommend strategies such as promotion of product, product improvement, regional marketing efficiency, proper distribution of products, customer retention strategies, price adjustment, rebranding and any other strategy that can help maximize revenue and improve customers satifaction. 
