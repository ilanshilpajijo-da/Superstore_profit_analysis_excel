# Superstore_profit_analysis_excel
# Superstore Profit & Loss Analysis (Excel)

## Project Overview
Analysing Superstore sales data in Excel to find where the business loses profit.

## Dataset
- **Name:** Superstore Dataset (Sample - Superstore.csv)
- **Source:** Kaggle, uploaded by Vivek Chowdhury (vivek468)
- **Link:** https://www.kaggle.com/datasets/vivek468/superstore-dataset-final
- **Note:** Data originally from Tableau sample data, "for educational purposes only"
- **Size:** 9,994 rows, 21 columns
- **Tool:** Microsoft Excel

## Step 1: Loading Data
- Downloaded the CSV and loaded it into Excel using Data > From Text/CSV.
- Kept the original CSV untouched and worked in a separate .xlsx file.

## Step 2: Data Cleaning (so far)
- **Problem:** Order Date and Ship Date looked like dates but were stored as text (=ISNUMBER() returned FALSE).
- **Why it matters:** Text dates cannot be grouped by month or year.
- **Fix:** Used Text to Columns with date format MDY (US format) on both columns.
- **Check:** =ISNUMBER() now returns TRUE for both columns.
Problem: Order Date and Ship Date looked like dates but were stored as text (checked with =ISNUMBER(), result was FALSE).
Why it matters: Text dates cannot be grouped by month or year.
Fix: Used Text to Columns with date format MDY (US format) on both columns.
Check: =ISNUMBER() now returns TRUE for both columns.
Checked Sales, Discount and Profit columns: all 9,994 rows filled, no missing values."

- **Missing values:** Checked Sales, Discount and Profit columns. All 9,994 rows were filled, no missing values.
- **Duplicates:** Used Remove Duplicates on all columns except Row ID (Row ID is unique for every row and would hide real duplicates). 1 duplicate row was removed, leaving 9,993 rows.
- **Backup:** Kept an untouched copy of the original data in a separate sheet.
"Created Year and Month columns from Order Date using YEAR() and MONTH(), to analyse profit by period."
-**Result Column:** "Created a Result column using IF(Profit<0, "Loss", "Profit") to flag loss-making orders."
