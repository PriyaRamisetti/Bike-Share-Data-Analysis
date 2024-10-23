# Bike-Share-Data-Analysis
This project analyzes bike-sharing data to assess the feasibility of increasing prices next year. The analysis is based on three datasets
- bike_share_yr_0 (2021 data) [Table 1]
- bike_share_yr_1 (2022 data) [Table 2]
- cost_table [Table 3]

**Importing Data into SQL Server Management Studio (SSMS) Using Import Flat File**

 Open SQL Server Management Studio (SSMS): Ensure your SQL Server is running, and connect to the server.

 Using Import Flat File: In SSMS, right-click on the database where you want to load the data.
- Select Tasks > Import Flat File.
- Importing Datasets: Imported each dataset (bike_share_yr_0, bike_share_yr_1, cost_table) 
- Select the data file (e.g., .csv).
- Preview the columns and data.
- Finish the import process.
- Verification: After importing, verified the data using a simple SELECT query.

SELECT TOP 1000 * FROM bike_share_yr_0;

## Run Sql Query for Table 1

![Screenshot 2024-10-22 173358](https://github.com/user-attachments/assets/547921af-ed54-4248-9e06-7b2405758892)

## Run Sql Query for Table 2

![Screenshot 2024-10-23 222110](https://github.com/user-attachments/assets/6f510ad1-3848-4069-b04b-84ad962a56ac)

## Run Sql Query for Table 3

![Screenshot 2024-10-23 222954](https://github.com/user-attachments/assets/1f0e3aca-1407-49a4-a552-70af218cf2b0)

**Objective:** 
Merge data from two tables (bike_share_yr_0 and bike_share_yr_1) to analyze bike-sharing information across different years (2021 and 2022). The UNION ALL operator is used to combine data from both tables while keeping all rows, including any duplicates.

**What is UNION ALL?**
- The UNION ALL command is used to combine the result sets of two or more SELECT queries.
- It does not remove duplicates. If there are rows that appear in both tables, they will still be present in the final result.
- This is useful when you want to include all records from both datasets, even if some are repeated.

**Project Scenario :**
In this case, we are merging two years of bike-sharing data from bike_share_yr_0 (2021) and bike_share_yr_1 (2022). Using UNION ALL, we ensure that all records, including duplicate entries for riders who might have used the service in both years, are included in the final dataset. This allows for a thorough analysis of trends across both years.

![Screenshot 2024-10-23 225719](https://github.com/user-attachments/assets/e41b96c0-3800-4b70-835d-de550797c204)

**Joining Tables Using Common Table Expression (CTE) and LEFT JOIN**

**Objective:** Combine the combined data from two tables (bike_share_yr_0 and bike_share_yr_1) with a third table (cost_table) to analyze bike-sharing metrics alongside associated costs.

**Explanation:**
**Common Table Expression (CTE):**
The WITH CTE AS (...) statement defines a temporary result set named CTE.
Within the CTE, we combine data from bike_share_yr_0 and bike_share_yr_1 using UNION ALL, which includes all rows from both tables.
**Selecting from the CTE:**
The main SELECT statement retrieves data from the CTE, represented as a.

**LEFT JOIN Operation:**
- The LEFT JOIN clause combines records from the CTE (which contains data from both years) with the cost_table.
- It matches rows from the CTE where the year (yr) corresponds to the year in the cost_table.
- If there is no match found in cost_table, the result will still include rows from the CTE, but the columns from the cost_table will be NULL.

**Purpose of the Join:**
- This approach allows for comprehensive analysis by merging bike-sharing data (from both years) with cost data, enabling you to calculate metrics such as total revenue, profit margins, and any other relevant financial analysis.
- The result set will include all bike-sharing records along with their associated costs, providing a holistic view of performance.

## SQL Query using CTE and LEFT JOIN
![Screenshot 2024-10-23 224532](https://github.com/user-attachments/assets/80aa77d5-7dcc-42a7-a45e-c46d726d591c)

**Selected Columns:** Instead of retrieving all the columns from the tables, we have selected specific columns like:dteday, 
season,yr,weekday,hr,rider_type,riders,price,COGS.

**Explanation of Calculations:**

**Revenue:**  This calculation multiplies the number of riders by the price per ride to determine the total revenue generated for each row. [riders * price AS Revenue]

**Profit:**  This calculation determines the profit by subtracting the total cost (COGS * riders) from the total revenue (riders * price). [(riders * price) - (COGS * riders) AS Profit]

![Screenshot 2024-10-23 225123](https://github.com/user-attachments/assets/ea8a5891-ffc6-4c7a-ba79-53e13656e593)

- By performing these calculations within the SQL query, we can directly analyze the financial performance of the bike-sharing service, including total revenue and profit for each entry in the dataset.

## Loading SQL Query into Power BI
- After completing the SQL query in SQL Server Management Studio (SSMS), the next step is to load the data into Power BI for further analysis and visualization. Below are the steps to accomplish this:

**1.Open Power BI:**
- Launch Power BI Desktop.
- Navigate to "Get Data":
- On the Home tab, click on Get Data and select SQL Server from the available options.

**2.Provide SQL Server Connection:**
- Enter the Server Name that you connected to in SSMS.
- Specify the Database name if needed.
- Click OK to proceed.

**3.Use Advanced SQL Options:**
- In the SQL Server Database dialog, scroll down to Advanced Options.
- Paste the SQL query into the SQL Statement field

**4.Load Data:**
- Click OK and Power BI will run the query and load the data into the model.

**5.Verify Data:**
- Go to the Data View in Power BI to verify that the data and calculations have been imported correctly, including fields like Revenue and Profit.

 ![Screenshot 2024-10-23 232638](https://github.com/user-attachments/assets/61b159b9-9420-4a51-9482-47e4ca3eebd4)
 
 ## Power BI Dashboard Explanation

After importing the SQL query into Power BI, I built several visualizations to help  Bike Share analyze their business performance. Here's a breakdown of the visuals used:

**1. Revenue and Profit Overview**

**Visualization Type:** Card
-  A **Card** displays a single number or summary metric, often used for KPIs like total sales or profit.

**Metrics:**
- **Revenue ($10M):** The total revenue generated for the year 2022, displayed using a Card.
- **Profit ($7.03M):** Total profit for the year, also visualized using a Card.
- **Insight:** These cards provide a quick snapshot of key financial figures to assess overall performance.
 
**2. KPI Over Time**
  
**Visualization Type:** Line and Clustered Column Chart

- A combination chart that uses columns to display data for one measure and a line to display another measure, making it easy to compare trends and categories.


**Metrics:**
- **Riders (Bars):** Total riders per month in 2022.
- **Average of Profit (Yellow Line):** Average profit calculated across each month.
- **Average of Revenue (Red Line):** Average revenue per month.
- **Insight:** This visual shows monthly trends and highlights seasonal fluctuations in ridership and earnings, with peaks during summer months and a decline towards the year’s end.

**3. Riders and Profit Margin Overview**

**Visualization Type:** Card
- A card is a visual element that displays a single value or metric prominently, often used to highlight key information or performance indicators.
  
 **Metrics:**
- **Riders (2M):** The total number of riders in 2022 visualized with a Card.
- **Profit Margin (0.45):** The ratio of profit to revenue displayed in another Card.
- **Insight:** This gives a high-level overview of ridership and profitability, helping assess how much profit was made per unit of revenue.

**4. Revenue by Hour**

**Visualization Type:** Matrix

- A table-like visualization that displays data in a grid format, allowing for comparisons across multiple categories and measures.
  
**Metrics:**
- **Revenue by Hour:** A Matrix visual showing revenue for each hour of the day.
- **Insight:** The matrix reveals patterns in revenue generation across different hours, helping to identify the most and least profitable times of the day.

**5. Revenue by Season**

**Visualization Type:** Clustered Bar Chart 

- A clustered bar chart is a type of chart that displays multiple sets of data side by side in separate bars grouped by categories, allowing for easy comparison of different groups across multiple series.

**Metrics:**
- **Revenue by Season:** A Stacked Bar Chart showing revenue across the four seasons.
- **Insight:** Summer (Season 3) generated the highest revenue, indicating a strong seasonal trend that can guide pricing strategies for the future.

**6. Riders by Rider Type**

**Visualization Type:** Donut Chart

- A circular chart that shows proportions by dividing data into segments, similar to a pie chart but with a blank center for better readability.

**Metrics:**
- **Registered Riders** (81.81%)
- **Casual Riders** (18.19%)
- **Insight:** This Donut Chart helps visualize the rider breakdown, showing that registered riders contribute significantly more to overall ridership, suggesting loyalty programs or other initiatives could be more profitable.

 ![Screenshot 2024-10-23 194326](https://github.com/user-attachments/assets/2ad15010-b922-4c13-bf58-9109e9291990)
 
 ![Screenshot 2024-10-23 194856](https://github.com/user-attachments/assets/74adaea1-5ea4-4b6d-93cd-2087c0714ea0)



