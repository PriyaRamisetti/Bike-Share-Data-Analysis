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

## Objective: 
Merge data from two tables (bike_share_yr_0 and bike_share_yr_1) to analyze bike-sharing information across different years (2021 and 2022). The UNION ALL operator is used to combine data from both tables while keeping all rows, including any duplicates.

**What is UNION ALL?**
- The UNION ALL command is used to combine the result sets of two or more SELECT queries.
- It does not remove duplicates. If there are rows that appear in both tables, they will still be present in the final result.
- This is useful when you want to include all records from both datasets, even if some are repeated.

**Project Scenario :**
In this case, we are merging two years of bike-sharing data from bike_share_yr_0 (2022) and bike_share_yr_1 (2023). Using UNION ALL, we ensure that all records, including duplicate entries for riders who might have used the service in both years, are included in the final dataset. This allows for a thorough analysis of trends across both years.





