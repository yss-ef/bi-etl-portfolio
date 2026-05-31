# Operational data sources

This directory contains raw operational data exported from the hotel
management system. These files serve as the primary input for the ETL
pipeline.

## Data schema

- `clients.csv`: Customer demographic and identity data.
- `hotels.csv`: Branch location and infrastructure metadata.
- `chambres.csv`: Room inventory and categorization.
- `reservations.csv`: The transactional log of all bookings.
- `canaux.csv`: Mapping of booking channels (Expedia, Booking.com, Direct,
  etc.).
- `temps.csv`: Raw temporal data for dimensional expansion.

Authored by Youssef Fellah.
Developed for the Engineering Cycle at Mundiapolis University.
