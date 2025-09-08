
# 📊 SQL Data Warehouse & Analytics Project

## 🚀 Overview

This repository demonstrates a **complete SQL data pipeline**:

1. **Data Warehouse (ETL)** → Build a layered **Bronze → Silver → Gold architecture** for ingesting, cleansing, and modeling data into a star schema.
2. **Data Analytics (EDA & Reporting)** → Perform **exploratory data analysis, KPIs, segmentation, and reporting views** directly from the `gold` schema.

The project showcases **SQL skills** in both **data engineering (ETL pipelines)** and **business intelligence (analytics & reporting)**.

---

## 🏗️ Architecture

### 🔹 Data Warehouse Layers

* **Bronze** → Raw ERP/CRM data ingested from CSV files.
* **Silver** → Cleaned, standardized, and business rules applied.
* **Gold** → Star schema optimized for analytics (`fact_sales`, `dim_customers`, `dim_products`).

### 🔹 Data Analytics Layers

* Schema & metadata exploration.
* Business KPIs (sales, orders, customers, products).
* Customer & product segmentation.
* Trend analysis (time series, YoY, MoM, cumulative).
* Reporting views (`gold.report_customers`, `gold.report_products`).

---

## 📂 Repository Structure

```text
E:.
│   README.md
│
├── datasets
│   ├── source_crm
│   │   ├── cust_info.csv
│   │   ├── prd_info.csv
│   │   └── sales_details.csv
│   │
│   └── source_erp
│       ├── CUST_AZ12.csv
│       ├── LOC_A101.csv
│       └── PX_CAT_G1V2.csv
│
├── EDA
│   └── scripts
│       ├── 01_database_exploration.sql
│       ├── 02_dimensions_exploration.sql
│       ├── 03_date_range_exploration.sql
│       ├── 04_measures_exploration.sql
│       ├── 05_magnitude_analysis.sql
│       ├── 06_ranking_analysis.sql
│       ├── 07_change_over_time_analysis.sql
│       ├── 08_cumulative_analysis.sql
│       ├── 09_performance_analysis.sql
│       ├── 10_data_segmentation.sql
│       ├── 11_part_to_whole_analysis.sql
│       ├── 12_report_customers.sql
│       └── 13_report_products.sql
│
├── scripts
│   ├── init_database.sql
│   ├── placeholder
│   │
│   ├── bronze
│   │   ├── ddl_bronze.sql
│   │   └── proc_load_bronze.sql
│   │
│   ├── gold
│   │   └── ddl_gold.sql
│   │
│   └── silver
│       ├── ddl_silver.sql
│       └── proc_load_silver.sql
│
└── tests
    ├── placeholder
    ├── quality_checks_gold.sql
    └── quality_checks_silver.sql
```

---

## 📑 EDA Script Catalog

| Category           | Script                       | Purpose                                                     |
| ------------------ | ---------------------------- | ----------------------------------------------------------- |
| 🔎 Exploration     | `database_exploration.sql`   | Explore schema, tables, and columns                         |
| 📅 Date Ranges     | `date_range_exploration.sql` | Find temporal boundaries (first/last orders, customer ages) |
| 📏 Measures        | `measures_exploration.sql`   | Calculate KPIs (sales, orders, customers, products)         |
| 📊 Magnitude       | `magnitude_analysis.sql`     | Aggregate metrics by country, gender, category              |
| 🏆 Ranking         | `ranking_analysis.sql`       | Rank top products/customers by revenue                      |
| 📈 Time Trends     | `change_over_time.sql`       | Monthly/Yearly sales trends                                 |
| 🧮 Cumulative      | `cumulative_analysis.sql`    | Running totals & moving averages                            |
| 📉 Performance     | `performance_analysis.sql`   | Year-over-Year & average benchmarks                         |
| 👥 Segmentation    | `segmentation_analysis.sql`  | Customer & product segmentation                             |
| 🥧 Part-to-Whole   | `part_to_whole_analysis.sql` | % contribution to total sales                               |
| 👤 Customer Report | `customer_report.sql`        | Creates `gold.report_customers` view with KPIs              |
| 📦 Product Report  | `product_report.sql`         | Creates `gold.report_products` view with KPIs               |

---

## ⚙️ Workflow

### 🏗️ Build the Data Warehouse

1. **Setup Schemas & Tables**

   ```sql
   :r scripts/bronze/ddl_bronze.sql
   :r scripts/silver/ddl_silver.sql
   :r scripts/gold/ddl_gold.sql
   ```

2. **Load Bronze Layer**

   ```sql
   EXEC bronze.proc_load_bronze;
   ```

3. **Transform to Silver Layer**

   ```sql
   EXEC silver.proc_load_silver;
   ```

4. **Create Gold Star Schema**

   ```sql
   :r scripts/gold/ddl_gold.sql
   ```

5. **Run Quality Checks**

   ```sql
   :r tests/quality_checks_silver.sql
   :r tests/quality_checks_gold.sql
   ```

---

### 📊 Run Data Analytics

Once the `gold` schema is ready, use the `EDA/scripts/` SQL files to run analyses such as:

* **Exploration** → schema, tables, columns
* **KPIs** → total sales, orders, products, customers
* **Segmentation** → VIP/Regular/New customers, product cost ranges
* **Trends** → monthly/yearly sales, cumulative growth, moving averages
* **Ranking** → top products, top customers, low performers
* **Part-to-Whole** → category contribution to total sales
* **Reports** → generate `gold.report_customers` & `gold.report_products`

---

## 📑 Example Reports

### 👤 Customer Report (`gold.report_customers`)

* Segmentation: **VIP, Regular, New**
* KPIs: **total orders, sales, products, quantity, lifespan**
* Extra metrics: **recency, avg order value, avg monthly spend**

### 📦 Product Report (`gold.report_products`)

* Segmentation: **High, Mid, Low performers**
* KPIs: **total orders, sales, customers, quantity**
* Extra metrics: **recency, avg selling price, monthly revenue**

---

## ✅ Key Features

* **End-to-End Pipeline** → raw CSV → Bronze → Silver → Gold → Analytics
* **Data Warehouse** → layered ETL with quality checks
* **Business Intelligence** → KPIs, trends, segmentation, ranking
* **Reusable Reporting Views** → customer & product dashboards

---

## 🛠️ Tech Stack

* **SQL Server** (or compatible SQL engine)
* **Stored Procedures + Views** (ETL & analytics logic)
* **CSV files** (ERP & CRM source datasets)
* **Optional BI** → Power BI / Tableau for visualization

---

## 🎯 Learning Objectives

* Build a **modern SQL Data Warehouse** with Bronze/Silver/Gold layers
* Perform **end-to-end EDA & reporting** with SQL
* Practice **window functions, aggregations, segmentation, and ranking**
* Validate pipelines with **data quality checks**

