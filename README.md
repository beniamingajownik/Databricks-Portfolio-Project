# End-to-End Databricks Portfolio Project (E-commerce)

## 📌 Project Overview
This project demonstrates a comprehensive **End-to-End Data Engineering** pipeline for *Maven Fuzzy Factory*, a fictional e-commerce retailer. The goal was to transform over 1.2 million raw, messy operational records into a structured, automated, and business-ready analytical platform using the **Medallion (Lakehouse) Architecture** on Databricks.

## 🏗️ Architecture: The Medallion Approach
The solution is built on **Databricks Free Edition** using **Delta Lake** and **Unity Catalog**. The data flows through three distinct layers:

1.  **Bronze (Raw Layer):** * Raw CSV data ingested into Unity Catalog Volumes.
    * Schema evolution support and metadata auditing with `_ingested_at` timestamps.
2.  **Silver (Cleaned & Standardized Layer):**
    * **Data Cleansing:** Handled specific data quality issues, such as converting string `'NULL'` values into proper SQL `NULL`s and mapping them to business terms (`direct`, `organic`).
    * **Type Casting:** Enforced strict schema with appropriate data types (`BIGINT`, `DECIMAL`, `TIMESTAMP`).
    * **Data Quality Checks (DQC):** Implemented automated validation scripts to compare row counts between layers and verify data integrity.
3.  **Gold (Curated Analytics Layer):**
    * **Conversion Funnel:** Built a session-level fact table to identify drop-off points in the customer journey.
    * **Marketing Performance:** Analyzed ROAS and margin across marketing channels (Gsearch, Bsearch, Social).
    * **Growth Trends:** Applied Window Functions (`LAG`) to calculate month-over-month revenue growth.
    * **Market Basket Analysis:** Performed complex self-joins to identify product cross-selling opportunities.

## 🛠️ Tech Stack
* **Platform:** Databricks (Lakehouse Architecture)
* **Storage & Format:** Delta Lake, Unity Catalog Volumes
* **Language:** Spark SQL
* **CI/CD:** GitHub Integration
* **Visualization:** Databricks SQL Dashboards

## 📈 Business Insights & Results
* **Overall Conversion Rate (CVR):** Established a baseline of **6.18%**.
* **Channel Optimization:** Identified `socialbook/pilot` as underperforming (1.08% CVR) and recommended budget reallocation to high-performing `bsearch/brand` (8.86% CVR).
* **Cross-Selling Success:** Discovered a significant purchase correlation between *Mr. Fuzzy* and *The Hudson River Mini Bear* (3,126 joint orders), leading to a recommended product bundling strategy.
![dashboard](<screenshots/databricks e-comm dashboard.JPG>)
![dashboardPage2](<screenshots/databricks e-comm dashboard2.JPG>)

## 🚀 Automation & Operations (DataOps)
The entire pipeline is fully automated via **Databricks Jobs**:
* **Scheduling:** Quartz Cron expression set for daily updates at 07:30 AM.
* **Monitoring:** Configured SLA rules (Timeouts) and email alerts for job failures or duration anomalies.
![Job](<screenshots/ecomm job databricks.JPG>)

## 📁 Repository Structure
* `01_Ingestion_Bronze.ipynb` - Raw data ingestion logic.
* `02_Transformation_Silver.ipynb` - Data cleansing, casting, and DQC.
* `03_Analytics_Gold.ipynb` - Advanced business logic and aggregations.

---

### How to Use
1. Clone this repository into your Databricks Workspace.
2. Ensure Unity Catalog is enabled and create the `bronze`, `silver`, and `gold` schemas.
3. Upload source CSV files to the specified Unity Catalog Volume.

---
**Author**: Beniamin Gajownik - [Github](https://github.com/beniamingajownik) / [LinkedIn](https://www.linkedin.com/in/beniamin-gajownik)

**Date**: April 2026  