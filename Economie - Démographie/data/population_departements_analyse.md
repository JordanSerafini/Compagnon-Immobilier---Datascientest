# Analyse: population_departements.csv

> **Description**: Données population et logements par département
> **Source**: INSEE - Recensement de la Population 2018 via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/4515549
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 2,003 |
| **Nombre de colonnes** | 10 |
| **Taille fichier** | 238.4 KB |
| **Taux de données manquantes global** | 9.1% |

---

## Analyse des colonnes

| Colonne | Type | NA | NA% | Uniques | Pertinence |
|---------|------|-----|-----|---------|------------|
| CODEGEO | object | 0 | 0.0% | 101 | Clé de jointure - ESSENTIELLE |
| NIVGEO | object | 203 | 10.1% | 1 | Niveau géo - SUPPRIMABLE |
| UNIT_label_fr | object | 203 | 10.1% | 3 | Compréhension - UTILE |
| UNIT | object | 203 | 10.1% | 3 | Filtrage données - IMPORTANTE |
| STOCD | object | 203 | 10.1% | 6 | Statut occupation - IMPORTANTE |
| OBS_VALUE | float64 | 203 | 10.1% | 1800 | Donnée principale - ESSENTIELLE |
| STOCD_label | object | 203 | 10.1% | 1 | Redondant - SUPPRIMABLE |
| DATASET_VERSION | object | 203 | 10.1% | 1 | Métadonnée - SUPPRIMABLE |
| DATASET_NAME | object | 203 | 10.1% | 1 | Métadonnée - SUPPRIMABLE |
| DATA_DATE | float64 | 203 | 10.1% | 1 | Année données - CONTEXTE |

---

## Données manquantes

| Colonne | Lignes NA | % NA | Recommandation |
|---------|-----------|------|----------------|
| NIVGEO | 203 | 10.1% | Supprimer les lignes NA |
| UNIT_label_fr | 203 | 10.1% | Supprimer les lignes NA |
| UNIT | 203 | 10.1% | Supprimer les lignes NA |
| STOCD | 203 | 10.1% | Supprimer les lignes NA |
| OBS_VALUE | 203 | 10.1% | Supprimer les lignes NA |
| STOCD_label | 203 | 10.1% | Supprimer les lignes NA |
| DATASET_VERSION | 203 | 10.1% | Supprimer les lignes NA |
| DATASET_NAME | 203 | 10.1% | Supprimer les lignes NA |
| DATA_DATE | 203 | 10.1% | Supprimer les lignes NA |

---

## Statistiques OBS_VALUE

| Statistique | Valeur |
|-------------|--------|
| Min | 679.27 |
| Max | 17,414,560.16 |
| Moyenne | 611,586.58 |
| Médiane | 89,901.16 |
| Écart-type | 1,541,317.79 |

---

## Valeurs catégorielles

### UNIT

| Valeur | Count | % |
|--------|-------|---|
| NBLOG | 600 | 30.0% |
| POP | 600 | 30.0% |
| DUREE | 600 | 30.0% |

### STOCD

| Valeur | Count | % |
|--------|-------|---|
| ENS | 300 | 15.0% |
| 10 | 300 | 15.0% |
| 21 | 300 | 15.0% |
| 22 | 300 | 15.0% |
| 23 | 300 | 15.0% |
| 30 | 300 | 15.0% |

---

## Recommandations

### Colonnes à conserver
- **CODEGEO**: Clé de jointure - ESSENTIELLE
- **UNIT**: Filtrage données - IMPORTANTE
- **STOCD**: Statut occupation - IMPORTANTE
- **OBS_VALUE**: Donnée principale - ESSENTIELLE

### Colonnes à supprimer
- NIVGEO
- STOCD_label
- DATASET_VERSION
- DATASET_NAME

### Nettoyage recommandé
- Supprimer les 203 lignes avec valeurs manquantes
- Supprimer les colonnes métadonnées non utilisées
- Renommer les colonnes pour plus de clarté si besoin
