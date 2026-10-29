# BioVanguard Therapeutics — Life Sciences Commercial Analytics

## Project Overview
An end-to-end data engineering and analytics project built using Databricks to analyse oncology prescription demand, sales performance, territory alignment, and engagement channel effectiveness.

## Business Problems
- **Territory Alignment Drift:** Preserve historical sales attribution when representatives change territories.
- **Channel Effectiveness:** Compare prescription volume and sales across engagement channels.
- **Incremental Data Processing:** Load daily prescription records while avoiding duplicate fact records.

## Technology Stack
- Databricks
- Apache Spark / PySpark
- Spark SQL
- Delta Lake
- Databricks AI/BI Dashboards
- Medallion Architecture

## Architecture
**Source CSVs → Bronze → Silver → Gold → Denormalised View → Dashboard**

The Gold layer includes five dimensions (`Dim_Date`, `Dim_HCP`, `Dim_HCO`, `Dim_Product`, `Dim_Sales_Rep`) and the `Fact_Daily_Commercial_Sales` fact table.

## Key Implementations
- SCD Type 2 for historical sales representative and territory tracking.
- Incremental fact loading using staging tables and `MERGE`.
- Gross sales, rebate, and net sales calculations.
- Denormalised dashboard view: `life_sciences_analytics.gold.vw_commercial_sales_dashboard`.

## Data Validation
- Silver-layer stratification: Compare TRx, NRx, and units between Bronze and Silver.
- Gold-layer referential integrity: Validate all five dimension keys.
- SCD Type 2 tests: Check active records, latest source versions, attribute consistency, and historical record closure.

## Dashboard
The interactive dashboard includes:
- Executive Overview
- Commercial Trends
- Territory Realignment
- Channel Effectiveness
- Product & Brand Intelligence
- Accounts & Providers

## Business Value
The solution enables commercial teams to explore sales and prescription trends, compare engagement channels, and analyse historical territory performance using effective-dated representative assignments.

## Limitations
The available prescription batches cover May 1 and May 16, 2026. Longer-term trend analysis and marketing ROI require broader historical data, campaign costs, and interaction-level data.
