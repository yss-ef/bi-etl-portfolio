# BI and ETL portfolio: data engineering and analytics

This repository contains a collection of Business Intelligence (BI) and ETL
laboratories and assignments. These projects demonstrate end-to-end data
warehousing solutions.

## Repository structure

```text
.
├── labs/                        # Academic labs (Hotel BI project)
│   ├── lab1/                    # BI foundations
│   ├── lab2/                    # Data modeling and star schemas
│   ├── lab3/                    # ETL processes and Pentaho basics
│   └── lab4/                    # Final hotel data warehouse
│       ├── business-requirements-04.pdf
│       └── hotel-data-warehouse/ # Hotel analytics system
│           ├── data-sources/    # Raw operational data
│           ├── etl-pipeline/    # PDI/Kettle orchestration
│           └── reports/         # KPI dashboards
├── projects/                    # Major projects and assignments
│   ├── e-commerce-bi-assignment/ # E-Commerce sales and logistics analysis
│   │   ├── data/                # Raw CSV sources
│   │   ├── etl/                 # Pentaho ETL transformations
│   │   ├── sql/                 # Database schema (PostgreSQL)
│   │   └── docs/                # Final report and visualizations
│   └── medical-center-bi/       # Medical center analytics
│       ├── data/                # Healthcare CSV datasets
│       ├── etl/                 # Pentaho ETL transformations
│       ├── scripts/             # SQL schema and scripts
│       └── docs/                # Reports and dashboard screenshots
└── LICENSE                      # Project license
```

## Featured projects

### 1. Hotel data warehouse (Lab 4)

- Location: `labs/lab4/hotel-data-warehouse/`
- Focus: Centralizes fragmented hotel data into a unified star schema for
  operational reporting.
- Tech: Pentaho Data Integration, Star Schema, PowerBI.

### 2. E-Commerce sales and logistics assignment

- Location: `projects/e-commerce-bi-assignment/`
- Focus: Analyzes sales performance and logistics efficiency for an e-commerce
  platform. This includes customer segmentation and carrier performance
  tracking.
- Tech: PostgreSQL, Pentaho (PDI), Metabase Dashboarding.

### 3. Medical center BI analysis

- Location: `projects/medical-center-bi/`
- Focus: Provides an end-to-end BI solution for a medical center, analyzing
  consultations, patient flow, and payment tracking.
- Tech: Pentaho Data Integration, Star Schema, Metabase Dashboarding.

Authored by Youssef Fellah.
Developed for the Engineering Cycle at Mundiapolis University.
