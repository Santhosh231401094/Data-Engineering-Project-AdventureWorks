# AdventureWorks Medallion Architecture Data Engineering Project

## Project Overview
This project demonstrates an end-to-end data engineering solution using the Medallion Architecture. The workflow processes data from the AdventureWorks dataset, which is hosted on GitHub, through multiple Azure services. Starting from raw data ingestion to final reporting using Power BI, this project implements a structured and scalable ETL pipeline.

## Medallion Architecture Layers

### Bronze Layer:

Raw data is ingested into the Azure Data Lake using Azure Data Factory (ADF) pipelines.
The dataset is accessed via a Linked Service created for GitHub (HTTP Linked Service) and the Azure Data Lake.
Dynamic pipelines use ForEach and LookUp activities to load multiple CSV files (10 files in this project).

### Silver Layer:

Data is transformed using Azure Databricks.
Cleaning, validation, and enrichment processes are performed, and the processed data is stored in the Silver container.

### Gold Layer:

Azure Synapse Analytics is used to create an external table schema named Gold.
Data in the Silver container is made accessible as regular tables using the OPENROWSET() function.
Aggregated and analytics-ready data is stored in the Gold container.

### Visualization:

Power BI is integrated with Azure Synapse Analytics to visualize the analytics-ready data.
Interactive dashboards provide insights, such as sales analysis, from the AdventureWorks dataset.

## Architecture Diagram
The workflow follows the Medallion Architecture pattern:

![diagram-export-1-16-2025-2_40_39-AM](https://github.com/user-attachments/assets/d205bbf3-0715-46cc-976e-205c726b282b)

## Technical Stack
The project utilizes the following technologies:

Azure Data Factory: For data ingestion and pipeline creation.
Azure Data Lake: For data storage in Bronze, Silver, and Gold containers.
Azure Databricks: For data transformation and enrichment.
Azure Synapse Analytics: For querying and managing external tables.
Power BI: For data visualization and reporting.

## Dataset
AdventureWorks Dataset:
Source: GitHub
Type: CSV files (10 files ingested)
Contains sales data used for reporting and analysis.

## ETL Pipeline

### Data Ingestion:

ADF dynamically ingests CSV files from GitHub into the Bronze container.
Uses parameterized pipelines for scalability.

### Data Transformation:

Databricks performs cleaning and transformations.
Data is saved in the Silver container for further analysis.

### Data Preparation for Analytics:

Synapse Analytics enables querying of data from the Silver container.
Finalized analytics-ready data is saved in the Gold container.

### Visualization:

Power BI connects to Synapse to create interactive dashboards for insights.

## Solution Highlights
Dynamic Pipelines: Parameterized pipelines in ADF automate the ingestion process.
Efficient Transformations: Databricks ensures data quality through transformation logic.
Seamless Querying: Synapse Analytics provides easy access to data using OPENROWSET().
Interactive Dashboards: Power BI offers a user-friendly visualization layer for reporting.

## Key Features
Implements Medallion Architecture for structured data processing.
Integrates multiple Azure services for an end-to-end solution.
Creates an extensible framework for large-scale data processing and analytics.
Visualizes sales data insights using Power BI.