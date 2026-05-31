# Medical center BI solution

This project implements a complete decision-making chain for a medical center.
It allows for the analysis of consultations, physician performance, patient
satisfaction, and financial health.

## Project overview

The solution follows a standard data warehouse architecture:
1. Sources: CSV files containing patient, physician, service, payment, and
   consultation data.
2. ETL: Pentaho Data Integration (PDI) for cleaning, transformation, and
   loading.
3. Storage: PostgreSQL database using a star schema.
4. Visualization: Power BI for decision-making reports.

## Directory structure

- `data/`: Source CSV files.
- `etl/`: Pentaho transformations.
- `scripts/`: SQL scripts for database creation.
- `docs/`: Documentation, schemas, and reports.
- `RESPONSE.md`: Detailed responses to project requirements.

## Configuration and installation

### 1. Database setup

Run the SQL scripts to initialize the data warehouse structure, including the
dimension tables (`dim_patient`, `dim_medecin`, `dim_service`, `dim_paiement`,
`dim_temps`) and the fact table (`fact_consultation`).

### 2. ETL process

Execute the Pentaho transformations to load the dimension tables and the fact
table. The process includes calculations for net amounts and delivery delays.

### 3. Visualization

Connect Power BI to the PostgreSQL instance to view reports on activity,
specialties, and service quality.

## Key performance indicators

- Global net revenue: Approximately 346,000 MAD.
- Delay rate: 59.58%.
- Non-payment rate: 21.92%.
- Leading specialty: General Medicine.
- Most active physician: Dr. Amina Bennani.

Authored by Youssef Fellah.
Business Intelligence project.
