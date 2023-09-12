# Northwind Trader's Analysis
## Introduction
This documentation provides a detailed overview of a Power BI dashboard created to analyze the Northwind Traders' dataset. The dashboard contains measures and visuals designed to answer specific questions related to the dataset.
## Data Source
The data source used for this analysis is the Northwind Traders' dataset, comprising the following tables:
1. **Orders:** containing information about **_orderID_**,	**_customerID_**,	**_employeeID_**,	**_orderDate_**, **_requiredDate_**,	**_shippedDate_**,	**_shipperID_**,	**_freight_**.
2. **Order details:** containing information about **_orderID_**,	**_productID_**,	**_unitPrice_**,	**_quantity_**,	**_discount_**.
3. **Employees:** containing information about **_employeeID_**,	**_employeeName_**,	**_title_**,	**_city_**,	**_country_**,	**_reportsTo_**.
4. **Customers:** containing information about **_customerID_**,	**_companyName_**,	**_contactName_**,	**_contactTitle_**,	**_city_**,	**_country_**.
5. **Categories:** containing information about **_categoryID_**,	**_categoryName_**,	**_description_**.
6. **Shippers:** containing information about **_shipperID_**,	**_companyName_**.
7. **Products:** containing information about **_productID_**,	**_productName_**,	**_quantityPerUnit_**,	**_unitPrice_**,	**_discontinued_** **_categoryID_**.
## Data Inspection
- Inspected the tables contained in the Northwind datasets.
- Identified columns, data types, and potential issues.
## Data Cleaning
1. Loaded each file using **Get data Tab**, I chose _text/csv_ -: "Based on entire dataset" 
2. Loaded the file into PowerQery Editor for cleaning using Data type detection
- Corrected data types for each column
- Renamed column headings for clarity and consistency
- Checked for missing values, duplicates and Nulls
## Data Integrity
I checked column quality, column profile and column distribution for each column in each file;
- This helps to identify and address issues like missing values, outliers, and inconsistencies, ensuring data reliability.
- It also enhance data quality and trustworthiness for accurate insights and visualizations.
## Merging Data:
In trying to make meaning out of the datasets, I used the left outer Join to
- Merged the Product dataset with Category Using **_CategoryID_** -: Table 1
- Then I merged and Orders and Order details dataset using **_OrderID_** -: Table 2
- I merged Table 2 and Shippers dataset on **_ShippersID_**-: Table 3
- Then I joined all tables and removed columns that were duplicates or not important to my analysis
- Named it Table with all order Info
## Dashboard
![](https://github.com/AnietieJohnson/Northwind-Trader-s-Analysis-Using-PowerBi/blob/main/Dashboard.png)

## Key Metrics
The above Power BI dashboard presents essential metrics in card visuals, including:
### 1. Total Number of Customers
This calculates the total number of unique customers in the dataset, using the aggregate function **COUNT(DISTINCT)** from Customer Table.
### 2. Distinct Number of Customers That Made Purchases through the Years
This calculates the distinct count of customers who have made purchases in multiple years, using the aggregate function **COUNT(DISTINCT)** from Orders Table.
### 3. Total Orders Across the Years
This calculates the total number of distinct orders placed by customers across the three years i.e from 2013 to 2015, Using the aggregate function **COUNT(DISTINCT)**.
### 4. Countries Covered
This counts the number of unique countries covered in the dataset, using the aggregate function **COUNT(DISTINCT)**
### 5. Average Processing Interval for Shipment
This calculates the average processing interval (in days) for shipments,using the aggregate function **Average**
- I created a New column
- With **DATEDIFF** as function, I calculated the date difference between order date and shipment date
> Processing interval = DATEDIFF('Table with all order info'[OrderDate],'Table with all order info'[ShippedDate],DAY) 
### 6. Products in Store  
This count the number of unique products available in the store, using the aggregate function **COUNT(DISTINCT)**
### 7. Product Categories
This count the number of unique product categories available in the store, using the aggregate function **COUNT(DISTINCT)** 
### 8. Average Freight
This calculates the average freight for all orders, using the aggregate function **Average**
## Charts and Table Visuals
The dashboard also includes insightful visualizations:
### 1. Top Ten Customers by Sales
The **_Table visual_** displays the top ten customers by *SUM of sales*, representing them with their company names.
- I created a new column
- wrote an expression to generate sales before creating the visual
> Sales = 'Table with all order info'[UnitPrice] * 'Table with all order info'[Quantity]
- I used the Filter Pane
- Editted for Top N using the Company name column
### 2. Sales Made from Each Product Category
The **_Bar chart_** shows the *SUM of sales* generated from each product category, helping identify the most profitable categories.
### 3. Sales Generated Each Year
The **_Line visual_** presents a year-wise breakdown of *SUM of sales*, allowing for the analysis of sales trends over time.
### 4. Customer's Shipping Preference
The **_Donut chart_** provides insights into the shipping preferences of customers i.e *COUNT of customers* by shipping company.
## Model
![](https://github.com/AnietieJohnson/Northwind-Trader-s-Analysis-Using-PowerBi/blob/main/Model.png)

## Conclusion
This Power BI dashboard offers valuable insights into the Northwind Traders' dataset, enabling us to analyze customer demographics, sales trends, shipping preferences, and more. It provides a user-friendly interface for exploring and understanding the data, supporting data-driven decision-making and business strategies.
## Insights
- **Best Performing Customers across Years:** By examining the top ten sales-producing clients over time, Quick Stop, Ernst Handel, and Save a lot markets are businesses that consistently ranked in the top ten from 2013 to 2015. Calculating the total number of customers who placed orders also revealed that two of the total customers had not made a purchase in the three years.
- **Best-Performing Product:** After examining the sales generated by each Product Category, we discover that Beverages generated the highest sales and Grains and Cereals produced the lowest sales.
- **Customer Preference for Shipping:** According to the pie chart, 40% of all customers choose United Package as their preferred shipping provider. whereas 30% is shared by Federal Shipping and Speedy Express.






