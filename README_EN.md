# 🛒 E-Commerce Data Engineering Pipeline (Olist)

🌎 [Read in English](README_EN.md) | 🇧🇷 [Ler em Português](README.md)

This project is an End-to-End Data Engineering pipeline built to process real data from a Brazilian e-commerce (Olist). The goal was to apply market best practices by structuring data in the **Medallion Architecture (Bronze, Silver, and Gold)**.

## 📊 Final Dashboard (Gold Layer)
*(The data below was pre-aggregated in PySpark to ensure millisecond performance)*

<div align="center">
  <img src="9f2f639a-76e3-4352-bbfc-d57c7eaf1c6c.jpg" width="900">
</div>

## 🛠️ Technologies and Architecture
- **Environment:** Databricks (Cloud)
- **Language:** Python (PySpark) and SQL
- **Storage:** Delta Lake (Optimized Format)
- **Architecture:** Medallion Architecture

## 🚀 The Pipeline Process

1. **🥉 Bronze Layer (Raw Data):** - Ingestion of pure transactional data (Orders, Customers, Products, Items).
   - Conversion from CSV format to **Delta**, ensuring Schema Enforcement (`overwriteSchema`) and historical tracking.

2. **🥈 Silver Layer (Cleansed & Conformed):**
   - Data cleansing and typing (converting strings to Timestamps).
   - Business rule filtering (only `delivered` orders).
   - Multiple *Joins* for data enrichment.
   - *Troubleshooting:* Strict use of DataFrames with *Aliases* to avoid the classic PySpark `Ambiguous Reference` error.

3. **🥇 Gold Layer (Business Aggregations):**
   - Creation of business views focused on BI performance.
   - Efficient aggregations (`groupBy`, `sum`, `count`) to generate the tables that feed the final Dashboard (Monthly Seasonality, Revenue by State, Top Categories).

## 💡 Key Learnings
As a professional focused on continuous improvement, this project allowed me to tackle real data infrastructure challenges. I dealt with permission restrictions in the Databricks File System (DBFS), bypassed classic Spark errors with complex *joins*, and understood the importance of applying *Schema Enforcement* when overwriting critical tables.
