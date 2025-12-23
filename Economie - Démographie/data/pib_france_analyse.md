# Analyse: pib_france.csv

> **Description**: Évolution PIB trimestriel France (taux de croissance)
> **Source**: INSEE - Séries IDBANK (base 2020)
> **Date d'analyse**: 2025-12-23

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 306 |
| **Période couverte** | 1949-Q2 à 2025-Q3 |
| **Fréquence** | Trimestrielle |
| **Série active** | Oui |
| **Base comptable** | 2020 |

---

## Description de la série

- **Indicateur**: Taux de croissance du PIB (variation trimestrielle en %)
- **Valorisation**: Volumes aux prix de l'année précédente chaînés
- **Correction**: CVS-CJO (corrigé des variations saisonnières et jours ouvrables)
- **Zone**: France

---

## Colonnes principales

| Colonne | Type | Description | Pertinence |
|---------|------|-------------|------------|
| TIME_PERIOD | object | Trimestre (YYYY-QN) | ESSENTIELLE |
| OBS_VALUE | float64 | Taux de croissance (%) | ESSENTIELLE |
| DATE | datetime | Date formatée | UTILE |
| SERIE_ARRETEE | bool | FALSE = série active | INFO |

---

## Statistiques OBS_VALUE (Taux de croissance %)

| Statistique | Valeur |
|-------------|--------|
| Min | -13.5% (COVID Q2-2020) |
| Max | +17.5% (rebond Q3-2020) |
| Moyenne | +0.8% |
| Médiane | +0.7% |
| Écart-type | 1.6 |

---

## Dernières observations

| Trimestre | Croissance |
|-----------|------------|
| 2024-Q4 | +0.0% |
| 2025-Q1 | +0.1% |
| 2025-Q2 | +0.3% |
| 2025-Q3 | +0.5% |

---

## Synthèse pour le traitement

### Colonnes retenues

- **TIME_PERIOD**: Clé temporelle
- **OBS_VALUE**: Taux de croissance
- **DATE**: Pour jointures temporelles

### Colonnes exclues

- Toutes les colonnes `*_label_en` (labels anglais)
- Colonnes métadonnées redondantes

### Exploitation envisagée

- Indicateur macro-économique pour contextualiser le marché immobilier
- Corrélation avec cycles immobiliers
- Base pour modèles prédictifs
