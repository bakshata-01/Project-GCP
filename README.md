# Project-GCP
Scalable RCM Data Lake on GCP to centralize, process, and analyze healthcare data using modern ETL, Medallion architecture, and CI/CD.

1. Data Ingestion (Local → GCS - Bronze Layer)
Local System Files (EMR Data)
Hospital datasets (CSV/JSON) are uploaded from the local system to Google Cloud Storage (GCS).
Flat Files (Claims Data)
Monthly claims data is directly placed into GCS (Landing Zone).
Public APIs (CPT, NPI, ICD)
API data is fetched and stored in GCS.

2. Data Processing (GCS → Dataproc → GCS)
Dataproc (PySpark) reads raw data from GCS:
Data cleaning (nulls, duplicates, formats)
Data validation
Applying transformations
Implementing SCD Type 2 for history tracking

3. Data Transformation (Silver → Gold)
Further transformations using PySpark:
Creation of Fact and Dimension tables
Applying Common Data Model (CDM)
Business-level aggregations

4. Data Loading (GCS → BigQuery)
Gold layer data is loaded into BigQuery:
Structured tables for analytics
Optimized for reporting queries

5. Orchestration (Workflow Management)
Cloud Composer (Airflow):
Schedules ETL jobs
Maintains pipeline dependencies
Automates end-to-end workflow.


