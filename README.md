🚍 Analyse du Ridership des Transports Urbains — Chicago & Philadelphie

Power BI | Python (ETL) | Data Analytics | Aide à la décision

📌 Présentation du projet

Ce projet analyse le ridership (fréquentation) des réseaux de transport urbain de Chicago et Philadelphie à partir de données historiques.
L’objectif est de concevoir un dashboard Power BI interactif et orienté décision, permettant de :

Suivre l’évolution du trafic dans le temps

Comparer les performances entre villes, modes et routes

Identifier les zones d’instabilité et de sous-performance

Appuyer des recommandations stratégiques et opérationnelles

🎯 Problématique métier

Les agences de transport gèrent des réseaux complexes où la demande varie selon :

la ville,

le mode de transport (bus, rail…),

les routes (lignes) individuelles.

Sans une vue analytique fiable, il est difficile de :

anticiper la fluctuation de la demande,

optimiser l’allocation des ressources,

repérer les routes sous-performantes,

benchmarker les performances entre villes.

🛠️ Stack technique

Python (ETL)

pandas (préparation & qualité des données)

Power BI Desktop

Modélisation (schéma en étoile)

Mesures DAX & KPIs

Dashboards interactifs

🔧 ETL & préparation des données (Python)

Les sources étant hétérogènes, un pipeline de préparation a été réalisé en Python pour produire des tables propres et cohérentes avant Power BI.

Étapes principales :

Import des fichiers et consolidation (Chicago / Philadelphie)

Standardisation des champs (Année, Mois, City, Mode, Route, Ridership)

Nettoyage : doublons, valeurs manquantes, types de données, formats texte

Harmonisation inter-villes pour permettre la comparaison

Export en tables “propres” prêtes à charger dans Power BI (processed/*.csv)

Contrôles qualité :

validation des clés (période + route/mode + ville)

vérification de complétude par période et par ville

détection de valeurs aberrantes (zéros incohérents, négatifs)

🗂️ Modèle de données (Power BI)

Le modèle repose sur un schéma en étoile :

Faits

Fait_mode : ridership par mode

Fait_route : ridership par route

Dimensions

Dim_City, Dim_Mode, Dim_Route, Dim_Mois, Dim_Année

Table de mesures

DAX_Measures (centralisation des KPIs)

📊 Structure du dashboard
🔹 Page 1 — Vue d’ensemble

Objectif : vision globale du trafic.

Ridership total

Évolution temporelle (Chicago vs Philadelphie)

Répartition par mode et par ville

Volatilité de la demande

Taux d’atteinte des objectifs

🔹 Page 2 — Qualité de service (Mode vs Route)

Objectif : comparaison performance/stabilité entre modes et routes.

Parts Mode vs Route

Top 10 / Bottom 10 routes

Volatilité Mode vs Route

Graph “Performance vs Volatilité” pour une lecture décisionnelle

🔹 Page 3 — Comparaison Chicago vs Philadelphie

Objectif : benchmarking inter-villes.

KPIs Chicago vs Philadelphie + écart

Évolution comparative dans le temps

Répartition par mode et différence de stabilité (volatilité)

📈 KPIs clés

Ridership total (Mode / Route)

Part Mode % / Part Route %

Évolution mensuelle (MoM)

Volatilité (écart-type)

Top/Bottom routes

Performance vs Volatilité (Mode vs Route)

Écart Chicago vs Philadelphie (valeur et %)

💡 Insights & recommandations

Piloter la stratégie au niveau des modes (levier principal du volume)

Optimiser les routes sous-performantes (fréquence, itinéraires, priorisation)

Surveiller les segments à forte volatilité (stabilité du service)

Adapter les décisions par ville (benchmark Chicago vs Philadelphie)

📁 Contenu du dépôt

notebooks/ — notebooks Python (ETL / nettoyage)

data/processed/ — données nettoyées prêtes Power BI

PowerBI_Dashboard.pbix — rapport Power BI

README.md — documentation

---

## 🚀 Extension proposée : Site / Application d’analyse des états de synthèse comptable

Si vous souhaitez transformer ce projet en **application orientée finance/comptabilité**, voici une feuille de route pragmatique.

### 1) Objectif produit

Construire une application web qui permet de :

- importer les états financiers (bilan, compte de résultat, flux de trésorerie),
- calculer automatiquement les principaux ratios,
- détecter les tendances, anomalies et signaux de risque,
- générer un tableau de bord décisionnel + un rapport synthétique.

### 2) Fonctionnalités MVP (version 1)

- **Import multi-format** : Excel, CSV, PDF structuré
- **Normalisation comptable** : mapping automatique des rubriques
- **Analyse des ratios** : liquidité, solvabilité, rentabilité, rotation
- **Comparaison temporelle** : N vs N-1, variation absolue et %
- **Scoring santé financière** : score simple (0–100) avec seuils
- **Restitution** : dashboard interactif + export PDF du diagnostic

### 3) Stack recommandée

- **Front-end** : Streamlit (démarrage rapide) ou React + Chart.js
- **Back-end** : Python (FastAPI)
- **Data** : pandas + pydantic (validation) + SQLite/PostgreSQL
- **IA optionnelle** : résumé automatique des points d’attention

### 4) Pipeline de traitement conseillé

1. Ingestion des documents comptables
2. Nettoyage & standardisation des libellés
3. Contrôles de cohérence (totaux, équilibre actif/passif)
4. Calcul des indicateurs financiers
5. Détection d’anomalies (règles + statistiques)
6. Visualisation et génération de recommandations

### 5) KPIs/ratios à afficher en priorité

- Fonds de roulement, BFR, Trésorerie nette
- Current ratio, Quick ratio
- Marge brute, marge opérationnelle, marge nette
- ROA, ROE
- Endettement global, autonomie financière
- Couverture des charges financières

### 6) Plan de réalisation en 4 sprints

- **Sprint 1** : modèle de données + import Excel/CSV + contrôles qualité
- **Sprint 2** : moteur de calcul des ratios + API FastAPI
- **Sprint 3** : interface dashboard + filtres (période, entité)
- **Sprint 4** : scoring, export PDF, documentation et déploiement

### 7) Livrables attendus

- Application web déployée
- Jeu de données d’exemple
- Documentation utilisateur
- Guide méthodologique des ratios et seuils
