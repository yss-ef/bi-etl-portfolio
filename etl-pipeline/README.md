# ETL Orchestration — Pentaho Data Integration

## Pipeline Architecture
The pipeline is designed using a **Star Schema** architecture to optimize analytical queries. It follows a strict "Dimension-first, Fact-last" loading sequence to maintain referential integrity.

## Core Implementations

### 1. Dimension Loading
*   **dim-client**: Normalizing customer data, handling unique identities, and address standardization.
*   **dim-hotel**: Mapping branch-specific attributes to the central warehouse.
*   **dim-time**: Automated generation of temporal hierarchies (Year, Quarter, Month, Day) for trend analysis.

### 2. Fact Loading
*   **fact-reservation**: The central metric hub, linking dimensions and calculating performance indicators (Net Revenue, Duration of Stay).

### 3. Orchestration
*   **hotel-etl-orchestrator.kjb**: A master job that manages the execution flow, including logging, error handling, and sequential transformation triggering.

## Technical Details
*   **Tool**: Pentaho Kettle (PDI)
*   **Patterns**: Change Data Capture (CDC) simulations and surrogate key management.

---
*Authored by Youssef Fellah.*
*Developed for the Engineering Cycle - Mundiapolis University.*
