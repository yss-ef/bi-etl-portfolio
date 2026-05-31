# Project report: BI decision chain implementation

This report details the implementation of a Business Intelligence solution
designed to centralize and model e-commerce data for sales and logistics
analysis.

## Business needs and metrics

The objective is to provide transverse visibility into commercial and
operational performance. The solution implements eight key performance
indicators:

- Total revenue
- Total orders
- Total quantity sold
- Average basket value
- Revenue by category and city
- Cancellation rate
- Late delivery rate
- Average delivery delay

## Data warehouse modeling

A star schema optimizes query execution. The model includes dimensions for
clients, products, carriers, and time, centered around a sales fact table.

### Logical schema

```mermaid
erDiagram
    dim_client ||--o{ fact_commande : "places"
    dim_produit ||--o{ fact_commande : "concerns"
    dim_transporteur ||--o{ fact_commande : "delivers"
    dim_temps ||--o{ fact_commande : "on"

    dim_client {
        int client_pk PK
        string id_client
        string nom_client
        string ville
        string pays
        string segment
    }

    dim_produit {
        int produit_pk PK
        string id_produit
        string nom_produit
        string categorie
        string marque
        float prix_unitaire
    }

    dim_transporteur {
        int trans_pk PK
        string id_transporteur
        string nom_transporteur
        string type_livraison
    }

    dim_temps {
        int temps_pk PK
        date date_complete
        int annee
        int mois
        int jour
    }

    fact_commande {
        int fact_id PK
        int client_pk FK
        int produit_pk FK
        int trans_pk FK
        int temps_pk FK
        string id_commande
        int quantite
        float montant_brut
        float montant_remise
        float montant_net
        int retard_jours
        int indicateur_livraison_en_retard
    }
```

## ETL process with Pentaho

The ETL process involves two main stages:
1. Dimension loading: Extracts, cleans, and loads data into dimension tables.
2. Fact loading: Performs joins and calculates metrics like net amount and
   delivery delays.

## Findings and recommendations

Analysis of the data reveals critical logistical points, such as a 29% delay
rate for certain carriers. Strategic recommendations include renegotiating
carrier contracts and focusing marketing efforts on high-performing product
categories.

Authored by Youssef Fellah.
Developed for the Engineering Cycle at Mundiapolis University.
