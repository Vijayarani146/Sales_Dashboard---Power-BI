# 🗒️ Project Notes – Sales Overview Dashboard

## 📁 File Name
**SALES OVERVIEW FINAL DASHBOARD.pbix**

---

## 🧩 Dashboard Components

### 1. Key Metrics Displayed
- Total Sales
- Total Profit
- Quantity Sold
- Profit Margin
- Top Products and Regions

### 2. Visuals Used
- Bar Charts
- Pie Charts
- Line Graphs
- Card KPIs
- Slicers (Region, Category, Time)

---

## 🏗️ Dashboard Design Logic

- **Data Model**: Cleaned and loaded data from Excel/CSV.
- **Measures Created**: 
  - `Total Sales = SUM(Sales[Sales])`
  - `Profit = SUM(Sales[Profit])`
  - `Quantity = SUM(Sales[Quantity])`
- **Time Intelligence**: Used `Date` table to enable YTD/MTD filtering.
- **Interactivity**: Enabled slicers and cross-filtering for intuitive analysis.

---

## 🧮 DAX Measures (Samples)
```DAX
Total Sales = SUM('Sales'[Sales Amount])
Profit Margin = DIVIDE(SUM('Sales'[Profit]), SUM('Sales'[Sales Amount]))
Top Category = CALCULATE([Total Sales], TOPN(1, VALUES('Sales'[Category]), [Total Sales], DESC))
