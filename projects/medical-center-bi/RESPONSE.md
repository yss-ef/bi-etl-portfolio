# Medical center BI solution report

This report describes the implementation of a Business Intelligence solution
for a medical center using Pentaho, PostgreSQL, and Power BI.

## Business requirements analysis

The primary objective is to centralize clinical and financial data within a
single data warehouse. This provides management with tools to maximize
profitability and optimize service quality.

### Key performance indicators

- Financial: Global net revenue and total discounts.
- Activity: Total appointments and unique patient counts.
- Quality: Average delay per consultation and late consultation rates.

### Analysis dimensions

- `dim_patient`: Demographic and behavioral analysis.
- `dim_medecin`: Performance analysis by practitioner and specialty.
- `dim_service`: Analysis by consultation type and pricing.
- `dim_paiement`: Financial flow analysis by payment method and status.
- `dim_temps`: Temporal and seasonal analysis.

## Results and interpretation

### Specialty performance

General Medicine is the most profitable specialty, followed by Gynecology and
Radiology.

### Physician activity

Dr. Amina Bennani is the most active practitioner, handling the highest volume
of consultations.

### Patient demographics

Casablanca generates the highest volume of medical activity, followed by Rabat
and Mohammedia.

### Service quality

The data reveals a critical delay rate of 59.58%, indicating that over half of
all consultations do not start on time.

### Financial status

The non-payment rate stands at 21.92%, which is considered high and requires
corrective measures to improve cash flow.

## Recommendations

- Schedule optimization: Adjust appointment slots to account for actual
  consultation durations.
- Payment management: Implement deposit requirements or strengthen payment
  follow-up procedures.
- Strategic focus: Prioritize high-performing specialties for patient
  retention.

Authored by Youssef Fellah.
Business Intelligence project.
