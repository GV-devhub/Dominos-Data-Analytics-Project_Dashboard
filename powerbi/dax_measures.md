# DAX Measures – Domino’s Analytics Project

These measures power the KPIs and visuals in the Power BI report.

---

**## 🔹 Revenue Measures**

****### Total Revenue****
```DAX
Total Revenue = SUM(FactSales[total_price])

****###Total Orders****
Total Orders = DISTINCTCOUNT(FactSales[order_id])

**Average Order Value (AOV)**
AOV = DIVIDE([Total Revenue], [Total Orders])

**Revenue This Month**
Revenue This Month =
CALCULATE(
    [Total Revenue],
    MONTH(FactSales[order_date]) = MONTH(TODAY())
)

**Revenue YTD**
Revenue YTD =
TOTALYTD(
    [Total Revenue],
    DimDate[Date]
)

**Revenue by Category**
Revenue by Category = [Total Revenue]
