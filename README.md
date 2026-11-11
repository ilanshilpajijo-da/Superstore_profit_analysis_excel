# Superstore Profit & Loss Analysis (Excel)

<img width="1463" height="681" alt="Screenshot 2026-11-11 165421" src="https://github.com/user-attachments/assets/a8b7b03c-f48d-440c-84bd-2862851561b1" />

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

**Found a circular reference in U25 (=[@Profit]), caused by an accidental formula. Restored the original value from the backup sheet and refreshed the pivots
## Step 6: Profit by Region (Pivot Table)
- All four regions are profitable, but margins differ a lot.
- West has the best margin (14.9%) and Central the weakest (7.9%).
- Central has higher sales than South (501K vs 392K) but lower profit.
Overall profit margin is 12.5% (total profit ÷ total sales).
- **Next:** check whether higher discounts in Central explain the low margin.
## Step 7: Region vs Discount
- Central gives the highest average discount (24.0%) and has the lowest profit margin (7.9%).
- West gives the lowest average discount (10.9%) and has the best margin (14.9%).
- Company-wide: average discount 15.6%, profit margin 12.5%.
- **Finding:** Regions with higher discounts tend to have lower margins.
- **Caution:** Only 4 regions, and product mix differs, so this shows a pattern, not proof.
## Step 8: Yearly Trend (Pivot Table)
- Sales grew from $483,966 (2014) to $733,215 (2017), about +52%.
- Profit grew from $49,556 to $93,439, about +88%.
- Profit margin rose from 10.2% (2014) to 13.4% (2016), then dipped to 12.7% in 2017.
- **Finding:** Sales kept growing, but margin slipped in 2017, so growth did not translate fully into profit.

## Step 9: Dashboard
- Built a one-page dashboard with total sales, total profit and profit margin.
- It has three charts (profit by discount level, profit by sub-category, sales and profit by year), a region table and the key findings.
- Charts are linked to pivot tables. The region table was pasted as values.

## Key Findings
1. **Discounts above 20% lead to losses.** Discount levels up to 20% made about $421,773 profit. Every level from 30% upwards lost money, about $135,364 in total. The biggest losses were at 70% (-$40,075) and 80% (-$30,539).
2. **Three sub-categories lose money:** Tables (-$17,725), Bookcases (-$3,473) and Supplies (-$1,189). Tables and Bookcases also have above-average discounts (26% and 21% vs 16% overall). Supplies loses money even with a low discount (8%), so discount is not the only cause.
3. **Central region is the weakest.** It has the highest average discount (24.0%) and the lowest profit margin (7.9%). West has the lowest discount (10.9%) and the best margin (14.9%).
4. **Growth is good, but margin slipped in 2017.** Sales grew from $483,966 (2014) to $733,215 (2017), about +52%. Profit grew from $49,556 to $93,439. Margin was 13.4% in 2016 and 12.7% in 2017.

## Recommendations
1. Keep discounts at 20% or below, since profit turns negative after that.
2. Review the prices and discounts of Tables and Bookcases.
3. Look into why Supplies loses money even with a low discount.
4. Review the discount policy in the Central region.

## Excel Skills Used
- Data cleaning: Text to Columns, Remove Duplicates, checking for missing values
- Formulas: YEAR, MONTH, IF, and basic maths for Profit Margin
- Pivot tables and pivot charts
- Dashboard design

## Files in this Repository
- `Superstore_Analysis.xlsx` - the full workbook (backup of raw data, pivot tables, charts, dashboard)
- `Dashboard.png` - screenshot of the dashboard
- The original CSV is not included. Please download it from Kaggle (link above).

## Limitations
- This is a sample dataset from a fictional store, so the findings show the method, not a real business.
- The results show patterns, not proof. Product mix and other factors also affect profit.
