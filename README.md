# Azure End-to-End Data Engineering Pipeline: Amazone_prime_title

## 📌 Project Overview
This project demonstrates the implementation of a **Modern Data Stack** on Microsoft Azure. It automates the extraction, transformation, and loading (ETL) of the dataset Amazone_prime_title
  into a centralized data warehouse using the **Medallion Architecture** (Bronze, Silver, and Gold layers).

The goal is to provide actionable business insights through a scalable and automated cloud infrastructure.

## 🏗️ Architecture
![Architecture Diagram](./architecture/architecture1.png)

## 🛠️ Tech Stack
* **Orchestration:** Azure Data Factory (ADF)
* **Data Lake:** Azure Data Lake Storage (ADLS) Gen2
* **Data Processing:** Azure Databricks (PySpark)
* **Visualization:** Power BI

## ⚡ Data Pipeline Workflow
The project follows a modular ETL approach:
1.  **Ingestion (Bronze):** Raw data is extracted from [Source] via Azure Data Factory and stored in the Bronze container in its original format.
![Architecture Diagram](./architecture/phase_ingestion_pipeline_azure.png)

2.  **Transformation (Silver):** Databricks notebooks process the raw data by cleaning, handling missing values, and enforcing schema constraints.
3.  **Aggregation (Gold):** Data is modeled into Fact and Dimension tables, ready for analytical consumption.
4.  **Loading & Serving:** The refined Gold data is loaded into Synapse Analytics to serve as the "Single Source of Truth."
5.  **Visualization:** A Power BI dashboard connects to the Gold layer to track KPIs such as [KPI 1] and [KPI 2].

## 📊 Business Insights
![Power BI Dashboard](./images/dashboard_preview.png)

## 🚀 Key Features Implemented
* **Scalability:** Managed through Databricks clusters and ADF triggers.
* **Security:** Sensitive credentials (connection strings, keys) are stored securely in **Azure Key Vault**.
* **Data Quality:** Implementation of basic data validation checks during the Silver transformation phase.
* **Automation:** End-to-end orchestration using ADF pipelines.

## 📂 Repository Structure
* `/pipelines`: Exported JSON definitions for Azure Data Factory.
* `/notebooks`: PySpark scripts used for Bronze-to-Gold transformations.
* `/sql`: DDL scripts for table creation in Synapse/SQL DB.
* `/architecture`: High-resolution system design diagrams.
* `/images`: Screenshots and visual assets for documentation.

---
**Author:** Abdallah ASSOUMANOU
*Engineering Student specializing in Data Engineering and AI*
