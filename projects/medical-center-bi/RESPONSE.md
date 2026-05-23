# Rapport d'Examen : Solution BI pour Centre Médical

**Candidat :** Youssef
**Projet :** Mise en place d'une chaîne décisionnelle BI avec Pentaho, PostgreSQL et Power BI

---

## PARTIE 1 : Analyse du Besoin Décisionnel (Tâche 1)

### 1. Quel est l'objectif principal de cette solution BI ?
L'objectif principal est de centraliser et de consolider des données cliniques et financières hétérogènes (consultations, profils patients, performances des médecins, transactions) au sein d'un entrepôt de données unique (Data Warehouse). Cette centralisation vise à doter la direction du centre d'un outil de pilotage stratégique pour maximiser la rentabilité financière (analyse des marges et des remises) et optimiser la qualité de service opérationnelle (suivi des flux de rendez-vous, des retards et des annulations).

### 2. Quels sont les indicateurs clés de performance à calculer ?
Les KPI indispensables se divisent en trois grandes catégories axées sur la performance globale :
* **Financiers :** Le Chiffre d'Affaires Brut Global, le Montant Cumulé des Remises Accordées, et le Chiffre d'Affaires Net Réel.
* **Activité & Volume :** Le volume total de rendez-vous planifiés, le volume strict des consultations réellement honorées, et le décompte des patients uniques.
* **Qualité Logistique :** Le retard moyen par consultation (en minutes), le taux de consultations en retard, ainsi que les taux d'abattement (consultations annulées ou reportées).

### 3. Quelles sont les dimensions d'analyse nécessaires ?
Pour analyser les faits numériques sous tous les angles pertinents, le modèle en étoile requiert cinq dimensions cibles :
* **`dim_patient` :** Analyse par caractéristiques démographiques (âge, sexe, ville de provenance) et comportementales (catégorie : Nouveau, VIP, Régulier).
* **`dim_medecin` :** Analyse des performances par praticien, par spécialité médicale et selon le grade hiérarchique.
* **`dim_service` :** Analyse typologique selon la nature de l'acte (Consultation standard, Contrôle, Urgence, Analyse) et sa tarification.
* **`dim_paiement` :** Analyse des flux monétaires par mode de règlement et par état de recouvrement (payé, partiel, non payé).
* **`dim_temps` :** Analyse temporelle et saisonnière à une granularité fine (par jour, par semaine, par mois et par année).

### 4. Quels problèmes métiers peuvent être détectés grâce à cette solution ?
La solution permet d'identifier plusieurs anomalies organisationnelles et financières critiques :
* **Dysfonctionnements opérationnels :** Détection de goulets d'étranglement ou de surcharges de plannings si le taux de consultations en retard ou le temps d'attente moyen explose.
* **Érosion des revenus :** Identification d'un volume excessif d'annulations non rentabilisées ou d'un manque à gagner dû à une distribution non maîtrisée des taux de remise.
* **Risques de trésorerie :** Repérage des fuites de capitaux matérialisées par un taux élevé de paiements restés "non payés" ou "partiels".

### 5. Pourquoi une base de données opérationnelle classique n'est-elle pas suffisante pour ce type d'analyse ?
Une base de données transactionnelle (OLTP) est optimisée exclusivement pour des opérations d'écriture, de modification et de lecture unitaire à forte concurrence (ex: enregistrer une consultation par une secrétaire). Elle utilise des structures hautement normalisées pour éviter les redondances. L'exécution de requêtes analytiques lourdes impliquant des jointures multiples et des calculs d'agrégation (`SUM`, `AVG`) sur des historiques volumineux saturerait instantanément les ressources du serveur, bloquant ainsi l'application métier des utilisateurs opérationnels. À l'inverse, l'entrepôt de données (OLAP) sépare les usages, utilise un modèle dénormalisé (en étoile) et accélère drastiquement le temps de réponse des calculs décisionnels.

---

## PARTIE 2 : Analyse et Interprétation des Résultats (Tâche 11)

*Basé sur les indicateurs réels extraits des tableaux de bord Metabase :*

### 1. Quelles sont les spécialités les plus rentables ?
D'après l'analyse du graphique *Chiffre d'Affaires par Spécialité*, la **Médecine Générale** s'impose comme la spécialité la plus rentable du centre, culminant à plus de **110 000 MAD** de Chiffre d'Affaires Net. Elle est immédiatement suivie par la **Gynécologie** (approchant les 94 000 MAD) et la **Radiologie** (environ 87 000 MAD). À l'inverse, l'Endocrinologie, la Gastro-entérologie et l'ORL constituent les services générant le moins de revenus nets.

### 2. Quels médecins réalisent le plus de consultations ?
Le graphique *Top 5 des Médecins (Volume)* indique que le **Dr. Amina Bennani** est le praticien le plus actif du centre, avec un volume remarquable de près de **76 consultations** prises en charge. Elle devance le **Dr. Ahmed Raji** (54 consultations), suivi de près par le **Dr. Amina El Fadili** (50 consultations). Le Dr. Ahmed Bouzid et le Dr. Adil Lahlou complètent ce Top 5 avec des volumes d'activité respectifs d'environ 44 et 38 consultations.

### 3. Quelles villes génèrent le plus d'activité médicale ?
L'analyse géographique des patients montre une concentration majeure sur **Casablanca**, qui génère le plus gros volume d'activité avec **261 consultations**. Elle est suivie par **Rabat** (177 consultations) et **Mohammedia** (126 consultations). Ces trois villes constituent le cœur de la zone de chalandise du centre médical, les patients en provenance de Marrakech et Meknès complétant le top 5.

### 4. Quel est le taux de consultations annulées ?
Le taux de consultations annulées s'élève à **9,75%**. Bien que ce chiffre puisse paraître modéré, il représente un manque à gagner certain, car ces créneaux horaires restent souvent inexploités. Dans notre processus ETL, ces consultations sont traitées avec un montant net forcé à 0 pour ne pas fausser le chiffre d'affaires réel.

### 5. Les retards de consultation sont-ils importants ?
**Oui, les retards au sein du centre sont particulièrement critiques et alarmants.** Les indicateurs de qualité de service révèlent que le **Taux de Consultations en Retard atteint 59,58%**. Cela signifie que plus d'un patient sur deux ne passe pas à l'heure prévue. Bien que le **Retard Moyen global soit de 9,43 minutes**, ce chiffre masque des disparités et témoigne d'un problème structurel récurrent dans la gestion de l'ordre de passage ou d'une sous-estimation du temps réel par consultation.

### 6. Quels modes de paiement sont les plus utilisés ?
L'analyse du graphique *Chiffre d'Affaires par Mode de Paiement* montre une répartition équilibrée entre les différents canaux. Les **Espèces** se placent en tête, générant un montant net d'environ **180 000 MAD**. La **Carte bancaire** et le **Virement** suivent de très près (chacun oscillant autour de 174 000 MAD), tandis que l'**Assurance** ferme la marche à environ 164 000 MAD. Cette diversification montre que le centre offre une excellente flexibilité transactionnelle à ses usagers.

### 7. Le taux de paiements non payés est-il acceptable ?
Le taux de paiements "Non payés" s'élève à **21,92%**. Ce niveau est jugé **non acceptable** car il fragilise la trésorerie disponible du cabinet médical. Près d'un quart des prestations ne font l'objet d'aucun recouvrement immédiat, ce qui nécessite la mise en place de mesures correctives urgentes.

### 8. Quelles recommandations peut-on proposer à la direction du centre médical ?
Au vu des données récoltées, trois axes d'actions stratégiques sont proposés :

1. **Refonte de la planification horaire :** Face à un taux de retard de près de 60%, il faut impérativement réajuster les plages de rendez-vous dans le logiciel métier, notamment pour la Médecine Générale et les praticiens les plus sollicités (comme le Dr. Bennani), en augmentant la durée moyenne allouée par consultation.
2. **Optimisation du recouvrement :** Avec plus de 21% de non-payés, le centre devrait instaurer un système d'acompte obligatoire lors de la réservation ou renforcer les procédures de suivi des paiements en attente.
3. **Stratégie de fidélisation sur les pôles d'excellence :** La Gynécologie, la Radiologie et la Médecine Générale étant les piliers financiers, des forfaits de bilans de santé annuels pourraient y être adossés pour pérenniser ces flux de revenus.
