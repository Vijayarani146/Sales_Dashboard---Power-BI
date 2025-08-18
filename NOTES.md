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
``` DAX
Total Sales = SUM('Sales'[Sales Amount])
Profit Margin = DIVIDE(SUM('Sales'[Profit]), SUM('Sales'[Sales Amount]))
Top Category = CALCULATE([Total Sales], TOPN(1, VALUES('Sales'[Category]), [Total Sales], DESC))

---

# Power BI Dashboard - Sales & Orders Analysis  

## 📌 Project Overview  
This project showcases an interactive **Power BI dashboard** designed to analyze sales, orders, customer profiles, and returns. It leverages custom DAX measures and calculated columns to provide actionable insights for decision-making.

---

### 📂 Dataset Used  
- **Final_Sales** – Order details including product price, order quantity, and sales.  
- **DateTable** – Custom date dimension for time intelligence calculations.  
- **Returns** – Return orders with quantities.  
- **Customers Table** – Customer demographics, including income and family details.  
- **Price Adjustment(%)** – Adjustment factors for dynamic product pricing.  

### 🎯 Dashboard Goals  
- Track **monthly and yearly sales performance**  
- Monitor **order trends and KPIs**  
- Calculate **returns and profitability metrics**  
- Classify customers by **income and family status**  
- Apply **dynamic pricing logic** for weekend sales  

---

# Power BI Dashboard - DAX Measures & Columns  

This repository contains the DAX measures and calculated columns used in my Power BI Dashboard project.

---

## 📊 DAX Measures  

1. **% Sales**
``` DAX
%sales = [TotalSales] / [TotalSalesAll1]
```

2. **Adjusted Sales**
``` DAX
Adjusted Sales = 
    SUMX(
        Final_Sales,
        Final_Sales[ProductPrice] * 
        (1 + 'Price Adjustment(%)'[Price Adjustment(%) Value] / 100) * 
        Final_Sales[OrderQuantity]
    )
```

3. **Orders KPI Title Card**
``` DAX
Orders_KPI Title Card = 
    FORMAT(MAX(DateTable[YearMonth]), "mmm-yyyy") & " Orders"
```

4. **Previous Month Orders**
``` DAX
Previous Month Orders 1 = 
    CALCULATE(
        DISTINCTCOUNT(Final_Sales[OrderNumber]),
        DATEADD(DateTable[Date], -1, MONTH)
    )
```

5. **Previous Year Sales**
`` `DAX
PreviousYearSales =
    CALCULATE(
        SUM(Final_Sales[Sales]),
        DATEADD(DateTable[Date], -1, YEAR)
    )
```

6. **Returns %**
``` DAX
Returns % = 
    SUM(Returns[ReturnQuantity]) / DISTINCTCOUNT(Final_Sales[OrderNumber])
```

7. **Total Return**
`` `DAX
Total Return = SUM(Returns[ReturnQuantity])
```

8. **Orders Count**
``` DAX
Orders Count = COUNT(Final_Sales[OrderNumber])
```

9. **New Product Price**
```DAX
newproductprice =
VAR checkweekend = FORMAT(Final_Sales[OrderDate], "ddd") IN {"Sat", "Sun"}
VAR newproductprice = Final_Sales[ProductPrice] * 1.5
VAR oldproductprice = Final_Sales[ProductPrice]
RETURN IF(checkweekend, newproductprice, oldproductprice)
```

---

## 🏷️ Calculated Columns

1. **Full Name**
``` DAX
Full Name = 'Customers Table'[FirstName] & " " & 'Customers Table'[LastName]
```

2. **Parent Status**
```DAX
ParentStatus = IF('Customers Table'[TotalChildren] = 0, "Not Parent", "Parent")
```

3. **Status**
`` `DAX
Status = 
    IF(
        'Customers Table'[AnnualIncome] >= 100000, 
        "High Income", 
        IF(
            'Customers Table'[AnnualIncome] > 70000, 
            "Medium Income", 
            "Low Income"
        )
    )
```

---

### 🚀 Usage

These measures and columns were created to enhance reporting and analytics within the Power BI dashboard. They support insights into:

- Sales performance tracking  
- Orders analysis (monthly/yearly trends)  
- Customer profiling  
- Product pricing strategies  
- Return management  

---

📌 *This README file documents the logic used in the Power BI project for better understanding, collaboration, and version control.*







:

🗒️ Project Notes – Sales Overview Dashboard
📁 File Name

SALES OVERVIEW FINAL DASHBOARD.pbix

🧩 Dashboard Components
1. Key Metrics Displayed

Total Sales

Total Profit

Quantity Sold

Profit Margin

Top Products and Regions

2. Visuals Used

Bar Charts

Pie Charts

Line Graphs

Card KPIs

Slicers (Region, Category, Time)

🏗️ Dashboard Design Logic

Data Model: Cleaned and loaded data from Excel/CSV.

Measures Created:

Total Sales = SUM(Sales[Sales])  
Profit = SUM(Sales[Profit])  
Quantity = SUM(Sales[Quantity])  


Time Intelligence: Used Date table to enable YTD/MTD filtering.

Interactivity: Enabled slicers and cross-filtering for intuitive analysis.

🧮 DAX Measures (Samples)
Total Sales = SUM('Sales'[Sales Amount])  
Profit Margin = DIVIDE(SUM('Sales'[Profit]), SUM('Sales'[Sales Amount]))  
Top Category = CALCULATE([Total Sales], TOPN(1, VALUES('Sales'[Category]), [Total Sales], DESC))  

📊 Power BI Dashboard - Sales & Orders Analysis
📌 Project Overview

This project showcases an interactive Power BI dashboard designed to analyze sales, orders, customer profiles, and returns. It leverages custom DAX measures and calculated columns to provide actionable insights for decision-making.

📂 Dataset Used

Final_Sales – Order details including product price, order quantity, and sales.

DateTable – Custom date dimension for time intelligence calculations.

Returns – Return orders with quantities.

Customers Table – Customer demographics, including income and family details.

Price Adjustment(%) – Adjustment factors for dynamic product pricing.

🎯 Dashboard Goals

Track monthly and yearly sales performance

Monitor order trends and KPIs

Calculate returns and profitability metrics

Classify customers by income and family status

Apply dynamic pricing logic for weekend sales

📊 DAX Measures

% Sales

%sales = [TotalSales] / [TotalSalesAll1]


Adjusted Sales

Adjusted Sales = 
    SUMX(
        Final_Sales,
        Final_Sales[ProductPrice] * 
        (1 + 'Price Adjustment(%)'[Price Adjustment(%) Value] / 100) * 
        Final_Sales[OrderQuantity]
    )


Orders KPI Title Card

Orders_KPI Title Card = 
    FORMAT(MAX(DateTable[YearMonth]), "mmm-yyyy") & " Orders"


Previous Month Orders

Previous Month Orders 1 = 
    CALCULATE(
        DISTINCTCOUNT(Final_Sales[OrderNumber]),
        DATEADD(DateTable[Date], -1, MONTH)
    )


Previous Year Sales

PreviousYearSales =
    CALCULATE(
        SUM(Final_Sales[Sales]),
        DATEADD(DateTable[Date], -1, YEAR)
    )


Returns %

Returns % = 
    SUM(Returns[ReturnQuantity]) / DISTINCTCOUNT(Final_Sales[OrderNumber])


Total Return

Total Return = SUM(Returns[ReturnQuantity])


Orders Count

Orders Count = COUNT(Final_Sales[OrderNumber])


New Product Price

newproductprice =
VAR checkweekend = FORMAT(Final_Sales[OrderDate], "ddd") IN {"Sat", "Sun"}
VAR newproductprice = Final_Sales[ProductPrice] * 1.5
VAR oldproductprice = Final_Sales[ProductPrice]
RETURN IF(checkweekend, newproductprice, oldproductprice)

🏷️ Calculated Columns

Full Name

Full Name = 'Customers Table'[FirstName] & " " & 'Customers Table'[LastName]


Parent Status

ParentStatus = IF('Customers Table'[TotalChildren] = 0, "Not Parent", "Parent")


Status

Status = 
    IF(
        'Customers Table'[AnnualIncome] >= 100000, 
        "High Income", 
        IF(
            'Customers Table'[AnnualIncome] > 70000, 
            "Medium Income", 
            "Low Income"
        )
    )

🚀 Usage

These measures and columns were created to enhance reporting and analytics within the Power BI dashboard. They support insights into:

Sales performance tracking

Orders analysis (monthly/yearly trends)

Customer profiling

Product pricing strategies

Return management

📌 This README file documents the logic used in the Power BI project for better understanding, collaboration, and version control.
