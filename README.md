# Health Data Integration Pipeline

An end-to-end data pipeline that extracts health data from MongoDB, transforms it in Databricks using PySpark, models it into governed, analytics-ready tables in Snowflake, and surfaces insights through Power BI dashboards.

## Overview

This project demonstrates a modern ELT architecture for healthcare data: automated extraction from a NoSQL source, scalable transformation using distributed compute, warehouse-native modeling for governed analytics, and business-facing reporting.

## Architecture

1. **Extraction** — Airbyte connects to MongoDB and automates syncing of raw health records into a centralized data lake, handling incremental updates without custom connector code.
2. **Transformation** — Databricks notebooks (PySpark) clean and standardize the raw data: deduplication, schema normalization, type casting, and enforcement of business validation rules.
3. **Modeling & Storage** — Transformed data is loaded into Snowflake using a medallion-style structure (Bronze/Silver/Gold), producing governed, analytics-ready tables.
4. **Reporting** — Power BI connects directly to Snowflake's Gold layer to deliver dashboards on key health metrics.

## Tech Stack

| Layer | Tool |
|---|---|
| Source | MongoDB |
| Ingestion | Airbyte |
| Transformation | Databricks (PySpark) |
| Warehouse | Snowflake |
| Reporting | Power BI |

## Key Features

- Automated, incremental data syncing from MongoDB via Airbyte — no manual extraction scripts.
- PySpark-based cleaning pipeline handling deduplication, schema normalization, and business rule validation.
- Medallion-style (Bronze/Silver/Gold) modeling in Snowflake for governed, analytics-ready data.
- Power BI dashboards for health metrics reporting, connected directly to curated Snowflake tables.

## Data Flow

1. Raw health records land in MongoDB.
2. Airbyte syncs collections into the pipeline on a scheduled basis.
3. Databricks (PySpark) reads raw data, applies cleaning/transformation logic, and writes standardized output.
4. Snowflake ingests the cleaned data and models it into curated Silver/Gold tables.
5. Power BI queries Snowflake directly to power reporting dashboards.

## Getting Started

### Prerequisites
- MongoDB instance with health data collections
- Airbyte (self-hosted or cloud)
- Databricks workspace
- Snowflake account
- Power BI Desktop

### Setup
1. Configure an Airbyte connection from MongoDB to your staging destination.
2. Import the PySpark transformation notebooks into your Databricks workspace and configure source/target paths.
3. Set up Snowflake tables and load logic (COPY INTO / MERGE) for the curated layer.
4. Connect Power BI to Snowflake and load the provided dashboard template.

## Future Improvements

- Add automated data quality testing (e.g., Great Expectations) between pipeline stages.
- Orchestrate the full pipeline with Apache Airflow for end-to-end scheduling and monitoring.
- Add CI/CD for Databricks notebook deployment.

## Author

Pavan Thollamadugu
