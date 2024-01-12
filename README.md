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

The data analysis project aims to provide insight into the sales performance of an education company over the past year. By analzing various aspects of the sales data, I seek to identify trends, make data-driven recommendatios and gain a deeper understanding pf the company's performance over the past 6 years.

### Data Sources

Sales data: The primary dataset used for this analysis is the "sales.cvs" file, containg detailed information about each sales made by the company

## Tools

- Excel (Data cleaning) 
  - [Download here](https://github.com/)
- SQL (Data Analysis)
- Power BI (Data cleaning and creating report)

### Data Transformation

 In the initial data preparation phase, the following tasks was performed
 
1. Data laoding and inspection
2. Handling missing value
3. Data cleaning and formating 

### Exploratory Data Analysis

- What is the overall sales trend?
- What are the top 10 educational Materials?
- What are the peak sales period

### Data Analysis

Include the codes used or features

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


### Recommendations

Based on the anaysis, I recommend the following actions

### Limitations

Remove null values. 

### Refrences 
