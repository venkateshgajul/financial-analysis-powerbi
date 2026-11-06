# Financial Data Analysis Dashboard (Power BI)

An interactive 7-page Power BI dashboard analyzing the income statements, balance sheets and cash flows of ~4,400 companies (FY2016 to FY2019).



## Objective
Give analysts a single view of company performance: revenue and profit trends, cash flow health, balance sheet risk, and which companies show consistent growth.

## Dataset
Six CSV files (annual and quarterly income statement, balance sheet and cash flow), about 100,000 rows in total, identified by company ticker.

| File | Rows |
|---|---|
| Income statement (annual / quarterly) | 17,511 / 17,657 |
| Balance sheet (annual / quarterly) | 17,511 / 17,657 |
| Cash flow (annual / quarterly) | 17,511 / 17,657 |

## Tools
Power BI Desktop, Power Query (M), DAX

## Process
1. **Data preparation:** set data types, removed duplicate rows (6 in the quarterly income file), added Year and YearQuarter columns, removed mostly empty columns.
2. **Modeling:** merged the three statements into annual and quarterly fact tables (`Fact_Annual`, `Fact_Quarterly`); built a star schema with `Dim_Date` and `Dim_Company`.
3. **Measures:** 40+ DAX measures, including free cash flow, margins, debt-to-equity, year-over-year growth, and consistent-growth flags.
4. **Design:** custom theme, synced Year and Stock slicers, KPI cards, and page navigation.

## Data model
```
Dim_Company (1) ──► (*) Fact_Annual    ◄── (1) Dim_Date
Dim_Company (1) ──► (*) Fact_Quarterly ◄── (1) Dim_Date
```

## Dashboard pages
| Page | What it shows |
|---|---|
| Executive Overview | Revenue, net income, free cash flow, total assets, margins |
| Company Performance | Revenue by company and year, quarterly revenue, retained earnings |
| Income Statement | Gross margin heat map, cost of revenue, operating income trend |
| Profitability | Revenue vs net income scatter, companies with net losses |
| Cash Flow | Cash flow waterfall, CapEx, financing, negative free cash flow |
| Balance Sheet | Assets vs liabilities, debt-to-equity, declining assets |
| KPI Scorecard | Consistent growers, year-over-year growth, net income leaders |

## Key insights
- AAPL leads net income at roughly $209bn, followed by JPM, MSFT and Alphabet.
- Gross margin is about 37%, but net margin is only about 8%.
- About 2,400 companies reported a net loss in at least one year.
- Only about 474 companies grew their cash balance every year from 2016 to 2019.
- WMT has the highest cost of revenue (about $1.1 trillion over the period).

## Limitations
- Quarterly data covers a short period (mostly 2019 to 2020).
- Some companies have missing years, shown as blanks.
- Balance sheet figures are year-end snapshots, so they are not summed across years.
- Company names are not in the dataset; companies are identified by ticker.
- Later years include more companies than earlier years, so some growth in totals reflects coverage, not only business growth.

## Repository files
- `Financial_Analysis.pbix`: the Power BI dashboard
- `Screenshots/`: images of each dashboard page
- `Dashboard.pdf`: PDF export of the report
- `Theme_B_Ocean_Fresh.json`: custom Power BI theme

## How to use
1. Download `Financial_Analysis.pbix`.
2. Open it in Power BI Desktop.
3. Use the Year and Stock slicers and the page navigator to explore.

## Author
**[Venkatesh Gajul]** | [https://www.linkedin.com/in/venkateshgajul/] | [venkateshgajul783@gmail.com]
