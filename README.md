# Bike-Share-Data-Analysis
This project analyzes bike-sharing data to assess the feasibility of increasing prices next year. The analysis is based on three datasets
- bike_share_yr_0 (2021 data)
- bike_share_yr_1 (2022 data)
- cost_table

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
#RUN SQL QUERY

![Screenshot 2024-10-22 173358](https://github.com/user-attachments/assets/547921af-ed54-4248-9e06-7b2405758892)


