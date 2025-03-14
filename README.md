# Formula 1 Racing Data Pipeline: End-to-End Engineering with Azure Databricks & Data Factory

# Introduction

An end-to-end data engineering project to create a fully monitored data pipeline which involves designing and implementing a robust system that automates the flow of data from its raw source to insightful reporting and analysis. This pipeline must handle data ingestion and transformation while ensuring data quality, auditing, and compliance with regulatory standards.

Additionally, the system should include mechanisms for monitoring the pipeline’s health, enabling real-time tracking, error detection, and recovery. By leveraging scalable cloud technologies, efficient data formats like Parquet to Delta Lake, and powerful tools for orchestration, transformation, and visualization, this project aims to deliver an efficient, reliable, and fully monitored data pipeline capable of supporting both operational needs and strategic decision-making.

# Project Requirement

## Data Ingestion Requirements
    * Ingest all files into the Data Lake.
    * Ingested data must have the schema applied.
    * Ingested data must have audit columns.
    * Ingested data must be stored in columnar format (i.e., Parquet).
    * Must be able to analyze the ingested data via SQL.
    * Ingestion logic must be able to handle incremental load.

## Data Transformation Requirements
    * Join the key information required for reporting to create a new table.
    * Join the key information required for analysis to create a new table.
    * Transformed tables must have audit columns.
    * Must be able to analyze the transformed data via SQL.
    * Transformed data must be stored in columnar format (i.e., Parquet).
    * Transformation logic must be able to handle incremental load.

## Reporting Requirements
    * Driver Standings
    * Constructor Standings

## Analysis Requirements
    * Dominant Drivers
    * Dominant Teams
    * Visualize the outputs
    * Create Databricks Dashboards

## Non Functional Requirements
    * Schedule to run every Sunday 10PM.
    * Ability to monitor the pipelines.
    * Ability to re-run fialed pipelines.
    * Ability to set-up alerts on failures.

## Other Non-Functional Requirements
    * Ability to delete individual records (To satisfy user privacy laws such as GDPR).
    * Ability to see history and time travel.
    * Ability to roll back to previous version.

# Formula1 Data Source & Data Overview

<b> Entity Relation Diagram:</b>
<img src= "ergast_db.png">

More info about dataset can be found here:
1. Current 3rd Party Developer API:  https://ergast.com/mrd/
2. Proposed Successor can be used as a drop-in replacement: https://github.com/jolpica/jolpica-f1

# Architecture

Solution Architecture:

<img src= "Solution Architecture.png">

These architectural solution is heavily based on this Microsoft documentation: https://learn.microsoft.com/en-us/azure/architecture/solution-ideas/articles/azure-databricks-modern-analytics-architecture

<img src= "Solution Architecture - Azure.png">

## Ingestion

    1. Data is ingested through a Databricks Notebook from the Ergast website via a full load (Historical Data) and an incremental load (Weekly Data).
    2. The data is stored in an ADLS container named 'processed.'
    3. Data in this layer will have the schema applied and be stored in a columnar format.
    4. Partitions will be applied where applicable.
    5. Additional information for audit purposes, such as the ingestion date and data source, will be included.
    6. Initially, this data will be stored in Parquet format.
    7. The data will later be converted to Delta Lake to meet GDPR requirements and enable time travel.

## Tranformation

    1. Processed data will then be transformed using a Databricks Notebook.
    2. The results will be stored in another ADLS container named 'Presentation.'
    3. Similar to the ingested data, the transformed data will initially be in Parquet format.
    4. The data will later be converted into Delta Lake.

# Load

    1. These notebooks will use data from both the processed and presentation containers.
    2. We then use Databricks notebooks to analyze and load the data to created dashboards to satisfy our analysis requirements.

## Technology Used