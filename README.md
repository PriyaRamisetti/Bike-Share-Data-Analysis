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

## Run Sql Query for Table 3

**Objective:** 
Merge data from two tables (bike_share_yr_0 and bike_share_yr_1) to analyze bike-sharing information across different years (2021 and 2022). The UNION ALL operator is used to combine data from both tables while keeping all rows, including any duplicates.

**What is UNION ALL?**
- The UNION ALL command is used to combine the result sets of two or more SELECT queries.
- It does not remove duplicates. If there are rows that appear in both tables, they will still be present in the final result.
- This is useful when you want to include all records from both datasets, even if some are repeated.

**Project Scenario :**
In this case, we are merging two years of bike-sharing data from bike_share_yr_0 (2022) and bike_share_yr_1 (2023). Using UNION ALL, we ensure that all records, including duplicate entries for riders who might have used the service in both years, are included in the final dataset. This allows for a thorough analysis of trends across both years.

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

**Selected Columns:** Instead of retrieving all the columns from the tables, we have selected specific columns like:dteday, 
season,yr,weekday,hr,rider_type,riders,price,COGS.

**Explanation of Calculations:**

**Revenue:**  This calculation multiplies the number of riders by the price per ride to determine the total revenue generated for each row. [riders * price AS Revenue]

**Profit:**  This calculation determines the profit by subtracting the total cost (COGS * riders) from the total revenue (riders * price). [(riders * price) - (COGS * riders) AS Profit]

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



