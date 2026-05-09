# Hotel Data Warehouse & BI Pipeline

A complete Business Intelligence project demonstrating an end-to-end ETL pipeline for a Hotel Management system. This project extracts raw data from multiple sources, transforms it into a dimensional model (Star Schema), and prepares it for PowerBI reporting.

## 🏗 Project Architecture

The project is divided into four main phases:

1.  **Requirements**: Original project specifications and academic exercises.
2.  **Data Sources**: Raw CSV files representing the source system (Clients, Hotels, Reservations, etc.).
3.  **ETL Pipeline**: Built using Pentaho Data Integration (PDI).
    *   **Orchestrator**: Master job to run the entire pipeline.
    *   **Transformations**: Individual scripts to load Dimensions and Fact tables.
4.  **Reporting & Dashboarding**: PowerBI data preparation and visualization.

## 🛠 Tech Stack

*   **ETL Tool**: Pentaho Data Integration (Kettle)
*   **Source Data**: Flat files (CSV)
*   **Data Modeling**: Star Schema (Dimensions & Facts)
*   **Reporting**: PowerBI

## 📂 Repository Structure

```text
.
├── requirements/                # Project instructions and exercises
├── data_sources/                # Raw input data
├── etl_pipeline/                # Pentaho ETL logic
│   ├── orchestrator_job/        # Master job (KJB)
│   └── transformations/         # ETL scripts (KTR)
└── reporting_and_dashboarding/  # Dashboard assets
```

## ⚖️ License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
