# Solution BI - Centre Médical Privé

Ce projet consiste en la mise en place d'une chaîne décisionnelle complète pour un centre médical, permettant d'analyser les consultations, les performances des médecins, la satisfaction (retards) et la santé financière (CA et recouvrement).

## Aperçu du Projet
Le projet suit l'architecture classique d'un entrepôt de données (Data Warehouse) :
1.  Sources : Fichiers CSV (patients, médecins, services, paiements, consultations).
2.  ETL : Pentaho Data Integration (PDI) pour le nettoyage, la transformation et le chargement.
3.  Stockage : Base de données PostgreSQL (Modèle en étoile).
4.  Visualisation : Power BI pour le reporting décisionnel.

## Structure du Répertoire
```text
/
├── data/                    # Fichiers sources CSV
├── etl/                     # Transformations (.ktr)
├── scripts/                 # Scripts SQL de création des tables
├── docs/                    # Documentation, schémas et rapports PDF
├── README.md                # Documentation principale
└── RESPONSE.md              # Réponses détaillées aux questions de l'examen
```

## Configuration et Installation

### 1. Base de Données (PostgreSQL)
Exécutez les scripts présents dans scripts/sql/ pour créer la structure du Data Warehouse :
-   Création des dimensions : dim_patient, dim_medecin, dim_service, dim_paiement, dim_temps.
-   Création de la table de faits : fact_consultation.

### 2. ETL (Pentaho)
Les transformations se trouvent dans le dossier etl/. 
Elles doivent être exécutées pour :
1.  Charger les dimensions.
2.  Charger la table de faits (avec calculs du montant net et des retards).

### 3. Visualisation (Power BI)
Connectez Power BI à votre instance PostgreSQL pour visualiser les 3 pages de rapport :
-   Page 1 : Vue globale de l'activité (CA, Volume).
-   Page 2 : Analyse par Spécialité et Médecin.
-   Page 3 : Qualité de service (Retards) et Paiements.

## Indicateurs Clés (KPI)
-   CA Net Global : ~346k MAD.
-   Taux de Retard : 59.58% (Point critique identifié).
-   Taux de Non-Paiement : 21.92%.
-   Spécialité leader : Médecine Générale.
-   Médecin le plus actif : Dr. Amina Bennani.

## Auteur
- Youssef - Projet de Business Intelligence 2026
