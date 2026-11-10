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

- **Result Column:** Created a Result column using IF(Profit<0, "Loss", "Profit") to flag loss-making orders.
- **Pivot Table:** "Pivot table of Profit by Sub-Category showed 3 loss-making sub-categories: Bookcases(-3472.556), Supplies(-1189.0995) and Tables(-17725.4821).
## Step 3: Helper Columns
- **Year, Month:** Created from Order Date using YEAR() and MONTH() to analyse by period.
- **Profit Margin:** Profit / Sales, so large and small orders can be compared fairly.
- **Result:** =IF(Profit<0,"Loss","Profit") to flag loss-making orders.

## Step 4: Profit by Sub-Category (Pivot Table)
- Total profit: $286,409 (after cleaning). Average discount across all sales: 16%.
- 3 of 17 sub-categories lose money:

| Sub-Category | Total Profit | Avg Discount |
|---|---|---|
| Tables | -17,725 | 26% |
| Bookcases | -3,473 | 21% |
| Supplies | -1,189 | 8% |

## Observations
- Tables and Bookcases have above-average discounts (26% and 21% vs 16%), which may be hurting profit.
- Supplies loses money even with a low discount (8%), so discount is not the only cause.
- Binders has the highest average discount (37%) but is still profitable, so average discount alone does not explain losses.
- **Next:** check profit at each discount level to find where discounts start causing losses.
## Step 5: Profit by Discount Level (Pivot Table)
- Discounts up to 20% are profitable (about +421,773 in total).
- Every discount level from 30% upwards loses money (about -135,364 in total).
- The biggest losses are at 70% (-40,075) and 80% (-30,539) discounts.
- **Finding:** Profit turns negative once the discount goes above 20%.
- **Caution:** This shows a link, not proof. Products and categories also differ, so it should be checked further.