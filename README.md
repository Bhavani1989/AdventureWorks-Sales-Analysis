# AdventureWorks-Sales-Analysis
# 📈 Adventure Works Sales Data Analysis

This project focuses on analyzing and reporting sales data from the **Adventure Works** dataset using Power BI and DAX. The model uses a **star schema** design and is ideal for exploring sales performance, return trends, product insights, and customer behavior across various business dimensions.

---

## 📁 Dataset & Data Model Overview

The data is structured around a **Fact Table** (`Sales Data`) and multiple **Dimension Tables** (Lookup Tables), allowing comprehensive slice-and-dice capabilities.

### 🧾 Fact Tables

| Table         | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `Sales Data`  | Records individual sales transactions. Includes keys linking to dimension tables. |
| `Returns Data`| Tracks product returns by date, product, and territory.                    |

#### Key Fields in `Sales Data`:
- `OrderLineItem`, `OrderQuantity`, `OrderNumber`
- `ProductKey`, `CustomerKey`, `TerritoryKey`
- `OrderDate`, `StockDate`

#### Key Fields in `Returns Data`:
- `ProductKey`, `ReturnDate`, `ReturnQuantity`, `TerritoryKey`

---

### 🗂️ Dimension (Lookup) Tables

| Table                          | Description                                           | Key Fields              |
|--------------------------------|-------------------------------------------------------|--------------------------|
| `Product Lookup`               | Details like SKU, price, cost, and product name.     | `ProductKey`             |
| `Product Subcategories Lookup` | Groups of related products.                          | `ProductSubcategoryKey`  |
| `Product Categories Lookup`    | Higher-level product categories.                     | `ProductCategoryKey`     |
| `Customer Lookup`              | Customer info and demographic data.                  | `CustomerKey`            |
| `Territory Lookup`             | Sales region data.                                   | `SalesTerritoryKey`      |
| `Calendar Lookup`              | Date breakdowns (day, month, year, etc.).            | `Date`                   |

---

## 🔗 Data Model Relationships

The model follows a **one-to-many (1:*) relationship** pattern from each dimension table to the fact tables.

- `Product Categories` → `Product Subcategories` → `Product Lookup` → `Sales Data`
- `Customer Lookup` → `Sales Data`
- `Territory Lookup` → `Sales Data`, `Returns Data`
- `Calendar Lookup` → `Sales Data[OrderDate]`
- `Returns Data` connects to `ProductKey` and `TerritoryKey`

---

## 📊 Analytical Use Cases

- Sales performance tracking by **product**, **region**, and **date**
- Customer segmentation and purchasing analysis
- Product return trends and return rate calculations
- Profitability insights and pricing impact analysis
- Target vs Actual KPIs with trend comparisons

---

## 🧰 Tools & Technologies

- **Power Query Editor** (for Extract, Transform and Load)
- **Power BI** (primary BI tool for modeling and visualization)
- **DAX (Data Analysis Expressions)** for KPI calculations

---

## 🧮 DAX Measures

### 📊 Key Performance Indicators (KPIs)

| Measure                    | Description                                                   |
|---------------------------|---------------------------------------------------------------|
| `Bikes Sold`              | Total quantity of bikes sold.                                  |
| `Bike Return Rate`        | `Bikes Returned / Bikes Sold`.                                 |
| `All Returns`             | Total quantity of all returned items.                          |
| `All Orders`              | Total number of orders across categories.                      |
| `% of Orders`             | Share of a category’s orders vs all orders.                    |
| `% of Returns`            | Share of a category’s returns vs all returns.                  |
| `Overall Avg Retail Price`| Average retail price across all products.                      |
| `Total Cost`              | Total cost of goods sold.                                      |
| `Total Revenue`           | Total sales revenue.                                           |
| `Total Profit`            | Profit = Revenue - Cost.                                       |
| `YTD Revenue`             | Year-to-date revenue using `DATESYTD`.                         |

### 📅 Time Intelligence Measures

| Measure                   | Description                                                   |
|--------------------------|---------------------------------------------------------------|
| `Previous Month Revenue` | Revenue from the previous month.                               |
| `Revenue Target`         | Target = Previous Month Revenue × 1.1                          |
| `10-day Rolling Revenue` | Rolling 10-day revenue.                                        |
| `Previous Month Profit`  | Last month’s profit.                                           |
| `Previous Month Orders`  | Orders placed last month.                                      |
| `Previous Month Returns` | Product returns from last month.                               |
| `Order Target`           | Target orders = Last Month Orders × 1.1                        |
| `Profit Target`          | Target profit = Last Month Profit × 1.1                        |
| `90-Day Rolling Profit`  | Aggregated profit over the last 90 days.                       |

### 🧮 Derived Metrics

| Measure                      | Description                                       |
|-----------------------------|---------------------------------------------------|
| `Avg Revenue per Customer`  | Total Revenue ÷ Total Customers                   |
| `Order Target Gap`          | Orders – Order Target                             |
| `Revenue Target Gap`        | Revenue – Revenue Target                          |
| `Profit Target Gap`         | Profit – Profit Target                            |

### 💲 Pricing & Adjustment Measures

| Measure                    | Description                                                   |
|---------------------------|---------------------------------------------------------------|
| `Adjusted Price`          | Price after applying a % adjustment for scenario analysis.     |
| `Adjusted Revenue`        | Adjusted Price × Quantity                                     |
| `Adjusted Profit`         | Adjusted Revenue – Cost                                       |
| `Price Adjustment % Value`| Dynamic % value used for pricing simulations.                 |

---

## ✅ Business Scenarios Enabled

- 📈 **Revenue Forecasting** and YoY growth
- 💰 **Profitability Tracking** and Target Gaps
- 🧾 **Return Rate Analysis** by Product/Region
- 📊 **Customer-level Revenue Insights**
- 🧪 **What-If Analysis** using price adjustments

---

## 🚀 Getting Started

1. Load all tables into Power BI or Excel Power Pivot.
2. Define relationships between tables as outlined above.
3. Create DAX measures in a dedicated **Measure Table**.
4. Build visuals using:
   - Line/bar charts for trends
   - Matrix for cross-tabs
   - Slicers for filtering by time, product, or region

---

## 📊 Adventure Works Dashboard Overview
Overview
The Main Dashboard serves as the central hub for analyzing sales performance, product trends, and return rates. It provides a high-level summary of key metrics, interactive slicers, and navigation options for deeper insights.

📌 Key KPIs:
Revenue: $24.9M

Profit: $10.5M

Orders: 25.2K

Return Rate: 2.2%

📈 Visuals:
Weekly Revenue Trend with forecast

Monthly Comparisons for revenue, orders, and returns

Top 10 Products by orders and return %

Orders by Product Category (Accessories, Bikes, Clothing)

Monthly Performance Metrics – Revenue, orders, returns, and % changes.

Most Ordered Product,  Most Returned Product 


📌 Slicer Panels:
- Located on the left side, allowing users to filter data by date, product category, and region.

📌 Page Navigations:
- Tabs at the bottom for switching between Dashboard, Map, Product Detail, and Customer Insights.

Purpose
This dashboard provides a comprehensive snapshot of business performance, enabling stakeholders to track KPIs, analyze trends, and navigate seamlessly between different analytical views.

 ![Image](https://github.com/user-attachments/assets/5199494e-12a4-4e30-b5f4-07a7235106f9)
 
---
## 🌎 Geographic Sales Dashboard 
Overview
The Geographic Sales Dashboard provides a regional breakdown of sales volume across different territories, allowing comparative analysis by country.
Key Features
- Sales Performance Map analyzing revenue distribution globally.
- Regional Filters: Europe, North America, Pacific.
- Top Cities & Countries by Sales.
- Interactive Bubble Map for visualizing sales hotspots.
- Sales Trends per Region comparing revenue over time.
Purpose
This dashboard enables businesses to monitor international sales trends, optimize regional strategies, and visualize sales performance by territory.

---
## 🛍️ Product Performance Dashboard 
Overview
This Power BI dashboard provides an interactive analysis of the AWC Logo Cap product's performance, including revenue, orders, profit, and returns. It enables stakeholders to track KPIs against targets and evaluate trends.
Key Features
- Dynamic Price Adjustment to analyze profit impact.
- Monthly Performance Gauges comparing orders, revenue, and profit to set targets.
- Trend Visualization showing total and adjusted profit over time.
- Comprehensive Metrics including revenue, profit, orders, returns, and return percentage.
- Interactive Navigation with tabs for Dashboard, Map, Product Detail, and Customer Insights.
Purpose
This dashboard supports product performance monitoring, trend identification, and strategy optimization for better profitability.

---

## 👥 Customer Analytics Dashboard 
Overview
This Power BI dashboard analyzes customer data, offering insights into unique customers, revenue per customer, and purchasing patterns. It helps businesses understand demographics, order distribution, and top buyers.
Key Features
- Customer Metrics displaying unique customers and revenue per customer.
- Trend Analysis showcasing total customers and revenue per customer from 2020 to 2022.
- Order Distribution Insights:
- Breakdown by Income Level (High, Medium, Low).
- Breakdown by Occupation (Management, Professional, Skilled Manual).
- Top Customer Details highlighting high revenue-generating individuals.
- Dynamic Filtering allowing date-based analysis.
Purpose
This dashboard enables businesses to identify key customers, analyze revenue trends, and tailor strategies for enhanced engagement and profitability.

---

## 📌 Notes

- This model uses synthetic data and is ideal for **learning**, **training**, and **demo** purposes.
- It demonstrates core **data modeling**, **DAX calculations**, and **dashboarding** skills used in business analytics.

---

## 📝 Future Enhancements

- Add **forecasting models** using Power BI built-in forecasting or Python integration.
- Include **RLS (Row-Level Security)** for multi-user reporting environments.
- Integrate **external benchmarking datasets** for comparative analysis.
- Deploy the report to Power BI Service for automated refresh and sharing.

---
