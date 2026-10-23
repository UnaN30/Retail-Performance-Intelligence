# Retail Performance Intelligence 2013 Sales vs Target

A two-page Power BI report analysing 2013 online retail performance for Adventure Works: whether territories are meeting sales targets, which product categories drive value, and what each territory manager is allowed to see.

Built as a capstone project for FMTALI Data Analytics.

## Report preview

**Page 1: Executive performance overview**
![Executive performance overview]

**Page 2: Target variance detail**
![Target variance detail]

## Business questions answered

| Question | Where it is answered |
|---|---|
| Are sales meeting monthly targets? | Page 1: monthly Sales vs Target Sales, KPI cards |
| Which territories need attention? | Page 1 territory ranking; Page 2 target variance by territory |
| Which products and categories drive value? | Page 2: sales, gross profit and margin by product category |
| What does each territory manager see? | Row-level security (static and dynamic), tested with View as |

## Headline results (2013, seven territories)

- Total Sales: R16.34M against a Target Sales of R16.29M, a variance of +R48.7K
- Gross Margin: 41.4%
- Orders: 21,260
- Australia is the top-selling territory; Canada is the lowest
- Bikes generate most revenue (about R15.3M of R16.3M) at a 40.5% margin; Accessories have the highest margin at 62.6%

## Tools and skills

Power BI Desktop, Power Query (M), DAX, SQL Server (AdventureWorksDW2022), Excel, Microsoft Fabric Lakehouse, star-schema modelling, row-level security.

## What I built

- **Data sources:** SQL Server for sales and product data, Excel for targets and security mapping, Fabric Lakehouse for customer profile data
- **Power Query:** RangeStart/RangeEnd parameterised date filter, territory filter, data typing, column clean-up, merged product / subcategory / category queries, and an append of H1 and H2 targets into one targets fact table
- **Star schema:** DimDate, DimProduct and DimSalesTerritory filter two fact tables (FactInternetSales and FactSalesTargets); single-direction relationships and no fact-to-fact link
- **DAX measures:** Total Sales, Total Cost, Gross Profit, Gross Margin %, Target Sales, Target Variance, Order Count, plus a `MonthlyTerritorySummary` calculated table
- **Security:** a static role (`Australia_Static`) and a dynamic role (`Dynamic_Territory`) driven by `USERPRINCIPALNAME()` and a disconnected access table
- **Design:** navy, teal, gold and pale blue palette, with red reserved for negative exceptions

