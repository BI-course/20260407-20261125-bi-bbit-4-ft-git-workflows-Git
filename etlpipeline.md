## ETL Pipelines — Brief Overview

**ETL (Extract, Transform, Load)** pipelines are a foundational concept in data engineering, used to move and prepare data from various sources into a centralized system such as a data warehouse or data lake.

### 1. Extract
This phase involves collecting raw data from multiple sources, such as:
- Databases (SQL/NoSQL)
- APIs
- Files (CSV, JSON, logs)
- Streaming systems

The goal is to gather data in its original format without altering it.

### 2. Transform
In this stage, the extracted data is cleaned and processed to make it usable:
- Data cleaning (handling missing or inconsistent values)
- Data normalization and formatting
- Aggregation and filtering
- Business logic application

This step ensures data quality and consistency for downstream use.

### 3. Load
The final phase loads the transformed data into a target system:
- Data warehouses (e.g., Snowflake, BigQuery)
- Data lakes
- Analytical databases

Loading can be done in:
- **Batch mode** (scheduled intervals)
- **Real-time/streaming mode**

### Key Benefits
- Enables centralized analytics
- Improves data quality and consistency
- Supports decision-making and reporting
- Automates data workflows

### Common Tools
- Apache Airflow (orchestration)
- Apache Spark (processing)
- Talend / Informatica (ETL platforms)
- dbt (transformation)