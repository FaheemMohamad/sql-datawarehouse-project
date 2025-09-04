
---

# 📊 SQL Data Warehouse Project

## 📌 Overview

This project implements a **Data Warehouse pipeline** using the **Bronze → Silver → Gold layered architecture**.
It showcases an end-to-end **ETL workflow** in SQL Server: ingesting raw ERP/CRM data, cleansing it, and preparing an **analytics-ready star schema** for reporting and BI.

* **Bronze Layer** → Raw data ingestion from CSV files.
* **Silver Layer** → Cleaned and standardized data with business rules applied.
* **Gold Layer** → Star schema (fact + dimensions) for analytics.
* **Quality Checks** → SQL validation scripts to ensure data accuracy and consistency.

---

## 📂 Repository Structure

```
sql-datawarehouse-project/
│
├── datasets/                           # Raw ERP and CRM CSV datasets
│
├── scripts/                            # SQL scripts for ETL
│   ├── bronze/                         
│   │   ├── ddl_bronze_tables.sql       # Create Bronze tables
│   │   └── proc_load_bronze.sql        # Procedure: load CSV → Bronze
│   │
│   ├── silver/                         
│   │   ├── ddl_silver_tables.sql       # Create Silver tables
│   │   └── proc_load_silver.sql        # Procedure: Bronze → Silver
│   │
│   ├── gold/                           
│       └── ddl_create_gold_views.sql   # Create Gold views (Star Schema)
│
├── tests/                              # Data validation scripts
│   ├── quality_checks_silver.sql       # Quality checks for Silver layer
│   └── quality_checks_gold.sql         # Quality checks for Gold layer
│
└── README.md                           # Project documentation
```

---

## ⚙️ Workflow

1. **Setup Schemas & Tables**
   Run DDL scripts to create tables and views in Bronze, Silver, and Gold.

   ```sql
   :r scripts/bronze/ddl_bronze_tables.sql
   :r scripts/silver/ddl_silver_tables.sql
   :r scripts/gold/ddl_create_gold_views.sql
   ```

2. **Load Bronze Layer**
   Ingest raw CSV data into Bronze tables:

   ```sql
   EXEC bronze.proc_load_bronze;
   ```

3. **Transform to Silver Layer**
   Clean, standardize, and apply business rules:

   ```sql
   EXEC silver.proc_load_silver;
   ```

4. **Create Gold Layer**
   Build star schema views (`dim_customers`, `dim_products`, `fact_sales`):

   ```sql
   :r scripts/gold/ddl_create_gold_views.sql
   ```

5. **Run Quality Checks**
   Validate uniqueness, consistency, and relationships:

   ```sql
   :r tests/quality_checks_silver.sql
   :r tests/quality_checks_gold.sql
   ```

---

## ✅ Key Features

* **Bronze/Silver/Gold Architecture** (industry standard).
* **Stored Procedures** for repeatable ETL execution.
* **Quality Checks** to validate data integrity.
* **Star Schema** (facts + dimensions) optimized for BI.
* **End-to-End Pipeline**: raw CSV → clean data → analytics-ready views.

---

## 🛠️ Tech Stack

* **SQL Server** → Data warehouse + ETL logic
* **CSV Files** → ERP & CRM source data
* **Stored Procedures + Views** → Data transformations and modeling
* **Optional BI Tools** → Power BI / Tableau for analytics

---

## 📊 Example Use Case

* **Bronze**: Raw CRM & ERP files → directly loaded.
* **Silver**: Data cleaned (no invalid dates, standardized gender/country codes).
* **Gold**: Sales star schema built with `fact_sales` joined to `dim_customers` & `dim_products`.
* **Quality Checks**: Automated SQL checks ensure trust in analytics.

---

