# Sales Analysis on Educational Dataset

## Table of contents

- [Project Overview](#project-overview)
- [Data Soures](#data-sources)
- [Tools](#tools)
- [Data Transformation](#data-transformation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results](#results)
- [Recommendations](#recommendations)
- [Limitations](#limitations)


### Project Overview
---

The objective of the data analysis project is to gain comprehensive insights into the sales performance of an education company throughout the previous year. Through a thorough examination of diverse aspects of the sales data, the goal is to pinpoint trends, formulate recommendations based on data, and develop a profound comprehension of the company's performance spanning the last six years.

### Insights

<img width="591" alt="image" src="https://github.com/Aliyu-Kuburat/Sales-Project/assets/156312358/e5c594d6-ff9e-4675-9f00-6fea8daeefde">

<img width="590" alt="image" src="https://github.com/Aliyu-Kuburat/Sales-Project/assets/156312358/37ea4524-52ae-4f41-8612-fc7dd7ffcafe">


### Data Sources

Sales data: The primary dataset used for this analysis is the "sales. cvs" file of the company, containing detailed information about each sale made.

## Tools

- Excel (Data cleaning) 
- SQL (Data Analysis)
- Power BI (Data cleaning and creating reports)

### Data Transformation

A)  In the initial data preparation phase, the following tasks were performed
 
1. Data loading and inspection
2. Handling missing value
3. Data cleaning and formatting

B) 
 **Basic Data Transformation**

1. I commenced the data cleaning process with a dataset containing 60,127 entries. The following steps were undertaken:

   - Conducted data profiling to assess data quality, ensuring confirmation of accuracy and completeness.
   - Reviewed the table view of the data before any transformations.
   - Identified and addressed issues within specific columns:
   - Removed rows with 2 blank values in the 'ID' column.
   - Eliminated rows with 1689 date values and N/A entries in the 'title' and 'email' columns.
   - Deleted rows with 2 blank values in the 'pricetotal', 'priceQa', 'priceCustomer', and 'created' columns.
   - Removed rows with 1689 date values and N/A entries in the 'category' and 'buyerName' columns.
   - Eliminated rows with 1689 date values and N/A entries in the 'buyerPhone' column.
   - Retained null values (1687) in the 'buyerEmail' column without deletion, considering the presence of values in other columns.
   
The dataset has undergone cleaning, resulting in a refined dataset comprising 54,432 entries.

2. Checked Data Types
3. Eliminated empty and erroneous datasets based on specified conditions.
4. Renamed Columns to: 'Order Id,' 'Material Title,' 'Partners Email,' 'Cost of Material,' 'Company Shares,' 'Partners Share,' 'Date,' 'Category Code,' 'Customer Name,' 
   'Customer Email,' 'Customer Phone,' and 'Material Category.'
5. Created three tables: 'Material,' 'Partners,' and 'Customer.'
   
**Breaking into multiple tables**

To create a well-structured data model in Power BI, it's a good practice to split your data into multiple tables, 
typically into lookup tables and fact tables. The goal is to reduce redundancy, improve data integrity, 
and enhance the efficiency of queries and visuals. 

**Breakout tables and columns**

**Material Table**:
Columns: Order ID, Material Title, Category Code, Material Category
**Partners Table**:
Columns: id, Partners Email
**Customer  Table**:
Columns: ID, Customer Name, Customer Email, Customer Phone
**Date Table**
Columns: Date, Year, Month, hour
**Sales Table**:
Columns: id, Date, Cost of Material, Company Shares of Sales, Partners Share of Sales

**Cleaning of breakout tables and columns**

**Material Table**:
Select the columns "Material Title", "Category" and "Category Code."
Remove duplicates.

**Partners Table**:
Follow similar steps for the "Partners Email" column.

**Buyer Table**:
Follow similar steps for the columns related to buyers.

**Date Table**
Columns: Date, Year, Month, hour, Day No, Month No

**Sales Table**:
Select the columns related to sales: "Date," "Cost of Material," "Company Shares of Sales," and "Partners Share of Sales."

### Load data for modelling.
 Connect Tables if it doesn't connect automatically and check relationships

### Exploratory Data Analysis

 - Analyzed the overall sales trend by month and year
 - Identified the top 10 educational materials by month and year
 - Determined peak sales periods based on the hour of the day.
 - Examined the cost of materials by month and year.
 - Explored revenue generated by the day of the week.
 - Calculated the total revenue.
 - Evaluated the company's profit.
 - Counted the number of customers.
 - Tabulated the number of orders.
 - Classified materials by category.
 - Assessed the number of orders by the day of the week.
 - Calculated the average order per day.
 - Calculated the average order by month.
 - Counted the number of partners.
 - Calculated the total partners' revenue.
 - Analyzed the cost of materials by category.
 - Tabulated the number and sum of orders by year.
 - Computed the running total.

### Data Analysis

I primarily employed Excel and Power BI for this project. The utilization of SQL was limited to extracting counts and sums of materials by months and years through the following query:
```sql
WITH RankedMaterials AS (
    SELECT
        Month,
        Year,
        MaterialTitle,
        ROW_NUMBER() OVER (PARTITION BY Month, Year ORDER BY SalesAmount DESC) AS Rank
    FROM
        YourTableName -- Replace with your actual table name
)
SELECT
    Month,
    Year,
    MaterialTitle
FROM
    RankedMaterials
WHERE
    Rank <= 10;
``` 

### Results
- 

### Recommendations

Based on the analysis, the following recommendations are proposed:

1. Address inconsistencies in the data collection process for the 'Material Category' column. Standardize naming conventions to ensure uniformity. For example, resolve 
   variations such as 'O level/ A level' being represented in five different ways, and 'Business/Career' having three different representations.
  for instance;
  - O level/ A level is named in 5 different ways, O level/ A level, O Level/A level, O Level/ A Level, O level/A level.
  - Business/Career is named 3 different ways, Business, Business/career, Business/Business/Career
2. Implement a detailed customer order information system. Introduce partner ID and order details ID
3. Introduce a 'BuyerID' labelled as 'Order Details ID' to facilitate easy customer identification.
4. Establish a 'Material ID' for improved material tracking.
5. Introduce a 'Partners ID' for effective partner identification.
6. Incorporate an expense tracking system for comprehensive financial insights.

### Limitations

- Some Blank columns with relevant information was replaced with zero
- Eliminated null values that lacked relevant information
### References 


