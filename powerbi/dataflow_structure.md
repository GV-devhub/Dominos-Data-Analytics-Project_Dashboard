
# Dataflow Structure – Domino’s Analytics Project

This document describes the structure of the Power BI Dataflow used to prepare the dataset.

---

## 1. Source Files
- `pizza_sales.csv` (Kaggle)

---

## 2. Tables Created

### 🔹 FactSales
Imported directly from pizza_sales.csv.

**Columns**
- order_id
- order_date
- pizza_name
- category
- size
- quantity
- unit_price
- total_price

**Transformations**
- Converted order_date → Date type
- Converted quantity → Whole Number
- Converted unit_price & total_price → Decimal
- Trimmed text fields
- Renamed table to FactSales

---

## 3. DimDate Table (Created in Power BI Desktop)

```DAX
DimDate =
ADDCOLUMNS (
    CALENDAR ( MIN(FactSales[order_date]), MAX(FactSales[order_date]) ),
    "Year", YEAR([Date]),
    "MonthNumber", MONTH([Date]),
    "MonthName", FORMAT([Date], "MMM"),
    "DayOfWeek", FORMAT([Date], "ddd")
)
