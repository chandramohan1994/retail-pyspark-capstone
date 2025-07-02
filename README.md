# retail-pyspark-capstone
# 🛍️ Retail Sales Analytics Capstone Project (PySpark + Databricks)

## 📌 Overview

This project simulates a real-time retail sales analytics pipeline using PySpark in Databricks Community Edition. It demonstrates how raw CSV data is transformed into enriched, query-optimized Delta tables for business insights and potential Power BI integration.

## 🧰 Tech Stack

- 🧠 Apache Spark (PySpark)
- 💾 Delta Lake
- ☁️ Databricks Community Edition
- 📊 Optional: Power BI for reporting

---

## 📁 Dataset Overview

The dataset is a simulated retail daily sales log with the following schema:

| Column     | Type         | Description                        |
| ---------- | ------------ | ---------------------------------- |
| sale_date  | DATE         | Date of the sale                   |
| quantity   | INT          | Units sold                         |
| stock      | INT          | Remaining inventory                |
| price      | DECIMAL(5,2) | Unit price of the product          |

Source: Uploaded manually to Databricks DBFS.

---

## 🧱 Data Pipeline Architecture

### 🟫 Bronze Layer
- Raw CSV data (`retail.csv`) ingested using PySpark.
- Stored as Delta table: `bronze_daily_sales`.

### 🟪 Silver Layer
- Transformation:
  - Derived column: `revenue = quantity * price`.
- Stored as Delta table: `silver_daily_sales`.

### 🟨 Gold Layer
- Business-ready enrichments:
  - 📈 Rolling 7-day average of quantity sold
  - ⚠️ Low stock flag (`stock < 500`)
  - 💸 Price tier classification:
    - Low: `< 1.10`
    - Medium: `1.10 - 1.20`
    - High: `> 1.20`
- Stored as Delta table: `gold_daily_sales`.

---

## 🔍 Sample Business Insights

- Days with high revenue or demand
- Identifying dates/items triggering low-stock alerts
- Performance of products based on pricing tiers
- Trends in rolling average sales

---

## 📂 Project Structure
retail-pyspark-capstone/
├── bronze_layer.py # Ingest raw CSV and save as Bronze Delta table
├── silver_layer.py # Add revenue and save as Silver table
├── gold_layer.py # Business transformations for Gold table
├── data/
│ └── retail.csv # Sample input data (uploaded to DBFS)
├── notebooks/
│ └── retail_capstone_databricks.ipynb # Optional unified notebook
├── screenshots/
│ └── bronze_to_gold_flow.png

