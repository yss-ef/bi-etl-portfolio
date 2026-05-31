# ETL orchestration with Pentaho Data Integration

The pipeline uses a star schema architecture to optimize analytical queries.
It follows a strict dimension-first loading sequence to maintain referential
integrity.

## Core implementations

### 1. Dimension loading

- `dim-client`: Normalizes customer data and standardizes addresses.
- `dim-hotel`: Maps branch-specific attributes to the central warehouse.
- `dim-time`: Automatically generates temporal hierarchies for trend analysis.

### 2. Fact loading

- `fact-reservation`: Serves as the central metric hub, linking dimensions and
  calculating performance indicators such as net revenue and duration of stay.

### 3. Orchestration

- `hotel-etl-orchestrator.kjb`: A master job that manages the execution flow,
  including logging, error handling, and sequential transformation triggering.

## Technical details

- Tool: Pentaho Kettle (PDI)
- Patterns: Change Data Capture (CDC) simulations and surrogate key
  management.

Authored by Youssef Fellah.
Developed for the Engineering Cycle at Mundiapolis University.
