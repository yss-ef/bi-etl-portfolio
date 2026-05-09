# BI & ETL Portfolio: Hotel Data Warehouse

A professional end-to-end Business Intelligence project demonstrating an automated ETL pipeline for a multi-location Hotel Management system. This portfolio showcases expertise in data modeling (Star Schema), ETL orchestration with Pentaho, and visual intelligence preparation.

## Business Case: Hotel Chain Analytics
The system centralizes fragmented data from various hotel branches to provide unified reporting. By consolidating customer profiles, reservation history, and room availability, the pipeline enables leadership to track critical KPIs such as occupancy rates and channel-specific revenue.

## Project Architecture

The project is structured into four specialized phases:

1.  **Requirements**: Business logic definitions and analytical specification documents.
2.  **Data Sources**: Raw source data representing the operational systems (Clients, Hotels, Reservations).
3.  **ETL Pipeline**: Built using Pentaho Data Integration (PDI/Kettle).
    *   **Orchestrator**: Master job to ensure transactional consistency across the pipeline.
    *   **Transformations**: Specialized scripts for loading Dimensions and Fact tables.
4.  **Reporting & Dashboarding**: Preparation for visual intelligence and dashboard consumption.

## Tech Stack

*   **ETL Tool**: Pentaho Data Integration (Kettle)
*   **Data Modeling**: Star Schema (Dimensions & Facts)
*   **Storage**: Relational Persistence & Flat Files
*   **Visualization**: PowerBI Readiness

## Repository Structure

```text
.
├── requirements/                # Business specs & requirements
├── data-sources/                # Raw operational data
├── etl-pipeline/                # Automated ETL orchestration
│   ├── orchestrator_job/        # Master pipeline job
│   └── transformations/         # Dimension & Fact loading scripts
└── reporting-dashboards/        # KPI definitions & dashboard assets
```

---
*Authored by Youssef Fellah.*
