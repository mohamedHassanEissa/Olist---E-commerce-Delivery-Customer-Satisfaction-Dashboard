# E-commerce Delivery & Customer Satisfaction Analysis

Analysis of the Olist Brazilian e-commerce public dataset (2016–2018, 99,441 orders) to identify what drives delivery delays and low customer satisfaction, with an interactive Power BI dashboard and data-backed recommendations.

## 🔑 Key Findings

- **Late deliveries devastate satisfaction**: orders delivered late average a **2.26/5** review vs. **4.28/5** for on-time orders. **62.9%** of late orders get a 1–2 star review, vs. only **9.5%** of on-time orders.
- **6.8%** of all delivered orders arrive late overall — but the rate is not constant: it spikes to **19%** in March 2018, **14%** in February 2018, and **12%** in November 2017 (Black Friday period), against a low-single-digit baseline most other months.
- **A small set of sellers drives disproportionate delay** — the worst-performing seller averages 9.6 days late across 36% of their orders, while most sellers ship close to on time, meaning delay is a targeted problem, not a marketplace-wide one.
- **State-level satisfaction stays in a narrow band** (MA, AL, PA report the lowest average review scores), suggesting delivery performance — not geography — is the primary driver of customer satisfaction.
- **health_beauty**, **watches_gifts**, and **bed_bath_table** are the top three product categories by revenue.

## 📌 Business Question

Which regions or sellers are driving delivery delays, and how do delays relate to customer satisfaction — in a way a non-technical stakeholder can act on?

## 🛠 Tools

- **Excel / Power Query** — data consolidation, cleaning, delivery-delay calculation
- **SQL (SQLite)** — relational analysis across 8 tables
- **Power BI** — interactive dashboard (star-schema model, DAX measures)

## 📁 Repository Structure
├── data/ # Raw CSV source files (Olist public dataset)
├── excel/
│ └── Orders_Delivery_Clean.xlsx # Cleaned, merged data + delay calculation
├── sql/
│ ├── 01_data_exploration_and_cleaning.sql
│ ├── 02_avg_review_by_state.sql
│ ├── 03_seller_delivery_delays.sql
│ ├── 04_pct_late_by_month.sql
│ ├── 05_top_categories_by_revenue.sql
│ └── 06_late_delivery_vs_review_score.sql
├── powerbi/
│ └── Olist_Dashboard.pbix
├── Data_Quality_Log.docx # Every cleaning/data decision, documented
├── Insight_Summary.pdf # One-page findings + 3 recommendations
└── README.md


## 📊 Dashboard

The Power BI dashboard includes:
- KPI cards: total orders, average review score, % late deliveries, total revenue
- Geographic view by state
- Monthly late-delivery trend
- Top categories by revenue
- Worst-performing sellers table
- Filters: state, product category, date range

## 📝 Methodology Notes

- Duplicate reviews (559 rows / 555 orders with multiple reviews) resolved by keeping the most recent review per order.
- "Late" is defined at the calendar-date level (same-day delivery = on time), since the estimated delivery date carries no time component.
- Full data-cleaning decisions and reasoning are documented in `Data_Quality_Log.docx`.

## 📄 Data Source

[Olist Brazilian E-Commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — real, anonymized orders from a Brazilian multi-vendor marketplace, 2016–2018.
