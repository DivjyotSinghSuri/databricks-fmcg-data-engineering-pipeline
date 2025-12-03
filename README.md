# 🚀 End-to-End Data Engineering Pipeline Using Databricks and Amazon S3

This project implements a production-style data engineering pipeline using **Databricks**, **Spark SQL**, and **Amazon S3**.  
It supports full-load ingestion, daily incremental updates, Bronze–Silver–Gold architecture, workflow automation, UPSERT logic, and analytics-ready fact/dimension tables.

---

# 🧱 Architecture Overview

## Bronze → Silver → Gold Architecture  
**Path:** ![Medallion Architecture](architecture/Medallion Architecture.png)


---

# 📦 Dataset Overview

The pipeline uses four key datasets:

- customers  
- products  
- gross_price  
- orders (full load + incremental)

---

# ⚙️ Tech Stack

- Databricks Community Edition  
- Spark SQL / PySpark  
- Amazon S3  
- Databricks Workflows  
- Lucidchart (ERD)  
- Databricks Dashboard  
- Genie  

---

# 📂 Repository Structure

/architecture → ERD, workflow diagram, BSG architecture
/notebooks → SQL notebooks for Bronze, Silver, Gold
/sample-data → Sample CSVs (5–10 rows only)
/pipeline → Databricks workflow JSON
/appendix → Certificates + code snippets

---

# 🔁 Pipeline Workflow (ETL Orchestration)

This project uses a **Databricks Workflow** to orchestrate the entire ETL pipeline.  
It automates ingestion, cleaning, modeling, and merging of incremental daily files.

## Pipeline Image  
**Path:** `architecture/Data Model.png`

---

## Workflow Stages

**Path:** `architecture/Workflow Diagram.jpg`

### 1. Bronze Stage
- Raw ingestion from S3  
- Stores unmodified data  
- Basic schema inference  

### 2. Silver Stage
- Removes duplicates  
- Handles nulls and invalid rows  
- Enforces data types  
- Standardizes dates  
- Filters inconsistent values  

### 3. Gold Stage
- Creates fact/dimension tables  
- dim_customers, dim_products, dim_gross_price  
- fact_orders  
- Parent–child table UPSERT  

---

## Workflow Schedule & Automation

- Runs nightly at **11 PM**  
- Executes all notebooks in sequence  
- Sends **email alerts** on failure  
- Fully automated incremental ETL

*(Insert workflow schedule screenshot)*  
**Path:** `architecture/workflow_schedule.png`

---

# 🧩 Data Model (ER Diagram)
 
**Path:** `architecture/Data Model.png`

Includes:
- fact_orders  
- dim_customers  
- dim_products  
- dim_gross_price  

---

# 🔁 Incremental Load Processing

Daily incremental files:
- `orders_2025_12_30.csv`  
- `orders_2025_12_31.csv`

The pipeline:
- Detects new files  
- Loads them to Bronze  
- Cleans them in Silver  
- Merges them in Gold using UPSERT  

---

# 🧪 Technical Results

## Data Quality Improvements
- ~4.8% duplicate rows removed  
- ~3.1% null/invalid rows corrected  
- 100% standardized date formats  
- Consistent schema enforced  

## Pipeline Performance
- ~35% faster transformation after SQL optimization  
- 100% successful workflow runs  
- UPSERT resolved ~6% mismatched rows  

---

# 📊 Dashboards (Optional)

*(Insert dashboard screenshot showing Gold-layer results)*  
**Path:** `architecture/dashboard_overview.png`

---

# 🧠 Key Learnings

- Medallion architecture (Bronze–Silver–Gold)  
- Incremental ETL  
- Data quality enforcement  
- Fact/dimension modeling  
- UPSERT logic  
- Workflow automation  
- Spark SQL optimization  

---

# 🛠️ How to Run the Pipeline

### 1. Upload data to S3

s3://child-company-sportbar-divjyot/

### 2. Import Databricks Notebooks
Run in order:
1. Bronze  
2. Silver  
3. Gold  

### 3. Import Workflow JSON
- Set schedule to 11 PM  
- Enable email alerts  

### 4. Validate Gold tables
- Check row counts  
- Validate joins  
- View dashboards  

---

# ⭐ Why This Project Matters

This repo demonstrates real-world data engineering skills:
- Cloud-based ETL  
- Automated workflows  
- Dimensional modeling  
- Incremental loads  
- Data quality processing  
- Scalable pipeline design

