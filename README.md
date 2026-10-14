# Online Retail II – Data Cleaning with Excel Power Query

A data cleaning project that turns a raw retail transactions file into an analysis-ready dataset using **Microsoft Excel (Power Query)**.

**Dataset:** [UCI Online Retail II](https://archive.ics.uci.edu/dataset/502/online+retail+ii) (sheet: Year 2010–2011)

## Results

| | Before | After |
|---|---|---|
| Rows | 541,910 | **391,146** |
| Rows without Customer ID | 135,080 | **0** |
| Duplicate rows | 5,268 | **0** |

Final dataset: **4,333 customers · 18,400 invoices · 3,658 products · 37 countries**, about **8.49M** in total sales (Dec 2010 – Dec 2011).

## Problems found and how they were fixed

| Problem | Fix |
|---|---|
| Rows without a Customer ID | Removed (needed for customer-level analysis) |
| Cancelled invoices (start with `C`) and negative quantities | Removed |
| Duplicate rows | Removed using **all columns** as the key |
| Zero prices | Filtered out (`Price > 0`) |
| Non-product codes: `POST`, `M`, `C2`, `DOT`, `BANK CHARGES`, `PADS` | Removed |
| Extreme quantities (74,215 and 80,995) that were cancelled later | Removed (`Quantity < 10,000`) |
| Stock codes with letters (e.g. `85123A`) turned into numbers | Kept `Stock_Code` as text and upper-cased it |
| Extra spaces in product names | Trim + replace double spaces |
| Same product code with different names | Kept the most frequent name per code (Group By + `Table.Max`) |
| Inconsistent country names (`Usa`, `Rsa`) | Upper-cased all country names |
| Date and time in one column | Split into `Invoice_Date` and `Invoice_Time` |

A `Total_Price` column (`Quantity × Price`) was added for analysis.

## Files

- `online_retail_II.xlsx` – raw data
- `online_retail_II_Clean.xlsx` – cleaned data

## Tools

Microsoft Excel · Power Query (M language)

## Author

**Basmala Amgad** – Data Entry & Data Cleaning
