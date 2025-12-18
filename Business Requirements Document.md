# 📄 Business Requirements Document (BRD)

**Project:** Maven Market- Multi-National Sales & Performance Analytics\
**Tool:** Power BI, DAX, Power Query\
**Role:** Data Analyst

---

## 1. Business Background
Maven Market is a multi-national grocery chain operating across the USA, Canada, and Mexico.
The company needs a centralized analytics solution to track sales, profitability, customer behavior, and product returns across regions and time.

## 2. Business Problems
Stakeholders currently lack visibility into:
* Overall sales and transaction performance.
* Profitability by product brand and geography.
* Product return behavior and return risk.
* Month-over-month performance trends.
* Whether revenue targets are being met.

## 3. Business Objectives
The dashboard must enable stakeholders to:
* Monitor **Total Transactions, Revenue, Profit, and Return Rate**.
* Identify top-performing and underperforming **product brands**.
* Track **monthly** and **year-to-date (YTD)** trends.
* Compare actual revenue vs. **revenue targets** (5% MoM Lift).
* Analyze performance by **Country, State, and City**.
* Quickly surface notable business insights using **bookmarks**.

## 4. Data Sources
The solution will ingest data from the following structured CSV files:
* **Fact Tables:** Transaction Data (1997–1998), Returns Data.
* **Dimension Tables:** Customers, Products, Stores, Regions, Calendar (Date Dimension).

## 5. Key Metrics (KPIs)
The following measures must be calculated using DAX:
* **Total Transactions** (Count of sales)
* **Total Revenue** (Price * Quantity)
* **Total Profit** (Revenue - Cost)
* **Profit Margin** (Profit / Revenue)
* **Return Rate** (Returns / Sold)
* **Weekend Transactions %** (Impact of Sat/Sun sales)
* **YTD Revenue** (Year-to-Date cumulative)
* **Revenue Target** (Last Month * 1.05)

## 6. Dashboard Visualization Requirements
To meet the objectives, the report must include:
* **KPI Cards:** Displaying current month performance vs. targets.
* **Map Visual:** Geospatial view of sales by country.
* **Treemap:** Hierarchical breakdown of transactions (Country > State > City).
* **Column Chart:** Weekly revenue trending analysis.
* **Gauge Chart:** Real-time tracking of Revenue vs. Target.
* **Matrix Table:** Detailed view of Top 30 Product Brands by Profit & Returns.

## 7. Success Criteria
The project is considered successful if stakeholders can:
* Make data-driven decisions without writing database queries.
* Identify regional (e.g., Mexico) and product-level (e.g., High Top) risks.
* Track performance trends and targets visually.
* Use "Notes" and "Bookmarks" to communicate specific insights during reviews.
