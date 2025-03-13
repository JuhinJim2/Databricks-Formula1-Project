# Formula 1 Motor Racing Data | Azure Databricks and Data Factory End to End Data Engineering

# Introduction

# Project Requirement

## Data Ingestion Requirements
1. Ingest all files into the Data Lake.
2. Ingested data must have the schema applied.
3. Ingested data must have audit columns.
4. Ingested data must be stored in columnar format (i.e., Parquet).
5. Must be able to analyze the ingested data via SQL.
6. Ingestion logic must be able to handle incremental load.

## Data Transformation Requirements
1. Join the key information required for reporting to create a new table.
2. Join the key information required for analysis to create a new table.
3. Transformed tables must have audit columns.
4. Must be able to analyze the transformed data via SQL.
5. Transformed data must be stored in columnar format (i.e., Parquet).
6. Transformation logic must be able to handle incremental load.

## Reporting Requirements
1. Driver Standings
2. Constructor Standings

## Analysis Requirements
1. Dominant Drivers
2. Dominant Teams
3. Visualize the outputs
4. Create Databricks Dashboards

## Non Functional Requirements
1. Schedule to run every Sunday 10PM.
2. Ability to monitor the pipelines.
3. Ability to re-run fialed pipelines.
4. Ability to set-up alerts on failures.

## Other Non-Functional Requirements
1. Ability to delete individual records (To satisfy user privacy laws such as GDPR).
2. Ability to see history and time travel.
3. Ability to roll back to previous version.

# Architecture

Solution Architecture:

<img src= "Solution Architecture.png">

These architectural solution is heavily based on this Microsoft documentation: https://learn.microsoft.com/en-us/azure/architecture/solution-ideas/articles/azure-databricks-modern-analytics-architecture

<img src= "Solution Architecture - Azure.png">




## Technology Used

# Formula1 Data Source & Data Overview

<b> Entity Relation Diagram:</b>
<img src= "ergast_db.png">

More info about dataset can be found here:
1. Current 3rd Party Developer API:  https://ergast.com/mrd/
2. Proposed Successor can be used as a drop-in replacement: https://github.com/jolpica/jolpica-f1

# Solutions Architecure