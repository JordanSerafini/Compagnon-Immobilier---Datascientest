# Analyse: revenus_departements.csv

> **Description**: Indicateurs de revenus et pauvreté par département
> **Source**: INSEE - FILOSOFI 2018 via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/4291712
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 1,770 |
| **Nombre de colonnes** | 12 |
| **Taille fichier** | 259.0 KB |
| **Taux de données manquantes global** | 16.9% |

---

## Analyse des colonnes

| Colonne | Type | NA | NA% | Uniques | Pertinence |
|---------|------|-----|-----|---------|------------|
| CODEGEO | object | 0 | 0.0% | 101 | Clé de jointure - ESSENTIELLE |
| NIVGEO | object | 6 | 0.3% | 1 | Niveau géo - SUPPRIMABLE |
| UNIT_label_fr | object | 6 | 0.3% | 18 | Compréhension - UTILE |
| UNIT | object | 6 | 0.3% | 18 | Filtrage données - IMPORTANTE |
| INDICS_FILO_DISP | float64 | 1476 | 83.4% | 1 | À évaluer |
| OBS_VALUE | float64 | 6 | 0.3% | 893 | Donnée principale - ESSENTIELLE |
| INDICS_FILO_DISP_label | object | 1476 | 83.4% | 1 | Redondant - SUPPRIMABLE |
| DATASET_VERSION | object | 6 | 0.3% | 1 | Métadonnée - SUPPRIMABLE |
| DATASET_NAME | object | 6 | 0.3% | 1 | Métadonnée - SUPPRIMABLE |
| DATA_DATE | float64 | 6 | 0.3% | 1 | Année données - CONTEXTE |
| INDICS_FILO_DISP_DET | float64 | 300 | 16.9% | 1 | À évaluer |
| INDICS_FILO_DISP_DET_label | object | 300 | 16.9% | 1 | Redondant - SUPPRIMABLE |

---

## Données manquantes

| Colonne | Lignes NA | % NA | Recommandation |
|---------|-----------|------|----------------|
| NIVGEO | 6 | 0.3% | Imputation ou suppression lignes |
| UNIT_label_fr | 6 | 0.3% | Imputation ou suppression lignes |
| UNIT | 6 | 0.3% | Imputation ou suppression lignes |
| INDICS_FILO_DISP | 1476 | 83.4% | Supprimer la colonne |
| OBS_VALUE | 6 | 0.3% | Imputation ou suppression lignes |
| INDICS_FILO_DISP_label | 1476 | 83.4% | Supprimer la colonne |
| DATASET_VERSION | 6 | 0.3% | Imputation ou suppression lignes |
| DATASET_NAME | 6 | 0.3% | Imputation ou suppression lignes |
| DATA_DATE | 6 | 0.3% | Imputation ou suppression lignes |
| INDICS_FILO_DISP_DET | 300 | 16.9% | Supprimer les lignes NA |
| INDICS_FILO_DISP_DET_label | 300 | 16.9% | Supprimer les lignes NA |

---

## Statistiques OBS_VALUE

| Statistique | Valeur |
|-------------|--------|
| Min | -29.50 |
| Max | 2,478,125.00 |
| Moyenne | 55,832.40 |
| Médiane | 11.75 |
| Écart-type | 202,592.25 |

---

## Valeurs catégorielles

### UNIT

| Valeur | Count | % |
|--------|-------|---|
| NBMEN | 98 | 5.5% |
| NBPERS | 98 | 5.5% |
| MEDIANE | 98 | 5.5% |
| D1 | 98 | 5.5% |
| D9 | 98 | 5.5% |
| RD | 98 | 5.5% |
| TP60 | 98 | 5.5% |
| PACT | 98 | 5.5% |
| PTSA | 98 | 5.5% |
| PCHO | 98 | 5.5% |
| ... | (8 autres) | - |

---

## Synthèse pour le traitement

### Colonnes retenues
- **CODEGEO**: Clé de jointure - ESSENTIELLE
- **UNIT**: Filtrage données - IMPORTANTE
- **OBS_VALUE**: Donnée principale - ESSENTIELLE

### Colonnes exclues
- NIVGEO
- INDICS_FILO_DISP_label
- DATASET_VERSION
- DATASET_NAME
- INDICS_FILO_DISP_DET_label

### Nettoyage à effectuer
- Supprimer les lignes avec valeurs manquantes
- Supprimer les colonnes métadonnées non utilisées
- Renommer les colonnes pour plus de clarté si besoin

### Utilisation prévue
- Pouvoir d'achat immobilier par territoire
- Corrélation revenus médians / prix de l'immobilier
- Segmentation des marchés locaux
