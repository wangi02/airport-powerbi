# SkyHub Airport — Power BI Dashboard

Dashboard Power BI d'analyse opérationnelle et commerciale pour **SkyHub**, une compagnie aérienne fictive basée à l'aéroport de Francfort (FRA).

Projet réalisé par **Wangi IKOLI & Anis Zouari** — Février 2025

---

## Aperçu

Ce projet transforme **9 fichiers bruts hétérogènes** (CSV, Excel, TSV) couvrant 3 ans d'activité (2022–2024) en un dashboard interactif à destination des décideurs de la compagnie. Le dataset comprend plus de **65 000 enregistrements** sur les opérations de vol, la satisfaction client, les performances commerciales et la gestion des bagages.

---

## Contenu du dashboard

Le rapport comprend une page d'accueil et **5 pages analytiques**, chacune répondant à une question métier précise :

| Page | Question métier |
|------|----------------|
| **Vue Globale** | Comment se porte la compagnie globalement ? |
| **Opérations Aériennes** | Nos vols sont-ils ponctuels et efficaces ? |
| **Performance Commerciale** | Quelles routes et segments sont les plus rentables ? |
| **Expérience Client** | Les passagers sont-ils satisfaits ? |
| **Bagages** | Comment gérons-nous les incidents bagages ? |

---

## Stack technique

- **Power BI Desktop** — modélisation, DAX, visualisations
- **Power Query** — nettoyage, transformation ETL, consolidation multi-feuilles
- **Modèle en étoile (Star Schema)** — `flights_2022_2024` comme table de faits centrale
- **22 mesures DAX** nommées, organisées par domaine analytique

---

## Sources de données

| Fichier | Type | Description |
|---------|------|-------------|
| `flights_2022_2024.csv` | Fait | ~12 000 vols sur 3 ans |
| `passengers.xlsx` | Fait | 43 807 enregistrements passagers (multi-feuilles) |
| `ticket_sales.csv` | Fait | Ventes de billets par route et classe |
| `satisfaction_surveys.csv` | Fait | Enquêtes NPS et satisfaction |
| `delays_incidents.csv` | Fait | Incidents et causes de retard |
| `baggage_claims.txt` | Fait | Réclamations bagages |
| `destinations.csv` | Dimension | 30 destinations |
| `fleet.csv` | Dimension | 25 appareils |
| `crew.xlsx` | Dimension | 210 membres d'équipage (multi-feuilles) |

---

## Points clés de la méthodologie

- **Détection des formats de date** : 741 dates au format européen (DD/MM) correctement parsées via locale française pour éviter une corruption silencieuse des agrégations mensuelles
- **Consolidation multi-feuilles** : sans traitement, 71% des données crew et 85% des données passagers auraient été perdues
- **Dimension calendrier** : table `DIM_Date` créée en DAX (`CALENDAR`) comme source unique pour tous les filtres temporels
- **Choix du star schema** : optimisé pour le moteur VertiPaq de Power BI, propagation monodirectionnelle des filtres, maintenance simplifiée

---

## Structure du projet

```
projet power bi/
├── Airport v2.pbix              # Fichier Power BI principal
├── SkyHub_Methodology_Report.docx  # Rapport méthodologique complet
├── PROJECT_INSTRUCTIONS.pdf     # Cahier des charges
└── dataset_skyhub_airport/      # Sources de données brutes
```

---

## Lancer le projet

1. Ouvrir `Airport v2.pbix` avec **Power BI Desktop**
2. Si nécessaire, rediriger les sources vers le dossier `dataset_skyhub_airport/`
3. Actualiser les données (Accueil > Actualiser)
