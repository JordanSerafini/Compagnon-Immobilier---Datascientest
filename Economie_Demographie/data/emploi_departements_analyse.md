# Analyse: emploi_departements.csv

> **Description**: Emploi salarié par secteur et département
> **Source**: INSEE - Flores 2018 via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/4986764
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 5,402 |
| **Nombre de colonnes** | 14 |
| **Taille fichier** | 1068.0 KB |
| **Taux de données manquantes global** | 23.8% |

---

## Analyse des colonnes

| Colonne | Type | NA | NA% | Uniques | Pertinence |
|---------|------|-----|-----|---------|------------|
| CODEGEO | object | 0 | 0.0% | 101 | Clé de jointure - ESSENTIELLE |
| NIVGEO | object | 2 | 0.0% | 1 | Niveau géo - SUPPRIMABLE |
| UNIT_label_fr | object | 2 | 0.0% | 2 | Compréhension - UTILE |
| UNIT | object | 2 | 0.0% | 2 | Filtrage données - IMPORTANTE |
| NA17 | object | 1802 | 33.4% | 18 | Secteur activité - IMPORTANTE |
| OBS_VALUE | float64 | 2 | 0.0% | 3977 | Donnée principale - ESSENTIELLE |
| NA17_label | object | 1802 | 33.4% | 1 | Redondant - SUPPRIMABLE |
| DATASET_VERSION | object | 2 | 0.0% | 1 | Métadonnée - SUPPRIMABLE |
| DATASET_NAME | object | 2 | 0.0% | 1 | Métadonnée - SUPPRIMABLE |
| DATA_DATE | float64 | 2 | 0.0% | 1 | Année données - CONTEXTE |
| SPHEREECO | object | 3602 | 66.7% | 3 | Sphère économique - IMPORTANTE |
| DOMPUB | object | 3602 | 66.7% | 3 | Public/Privé - IMPORTANTE |
| SPHEREECO_label | object | 3602 | 66.7% | 1 | Redondant - SUPPRIMABLE |
| DOMPUB_label | object | 3602 | 66.7% | 1 | Redondant - SUPPRIMABLE |

---

## Données manquantes

| Colonne | Lignes NA | % NA | Recommandation |
|---------|-----------|------|----------------|
| NIVGEO | 2 | 0.0% | Imputation ou suppression lignes |
| UNIT_label_fr | 2 | 0.0% | Imputation ou suppression lignes |
| UNIT | 2 | 0.0% | Imputation ou suppression lignes |
| NA17 | 1802 | 33.4% | Supprimer les lignes NA |
| OBS_VALUE | 2 | 0.0% | Imputation ou suppression lignes |
| NA17_label | 1802 | 33.4% | Supprimer les lignes NA |
| DATASET_VERSION | 2 | 0.0% | Imputation ou suppression lignes |
| DATASET_NAME | 2 | 0.0% | Imputation ou suppression lignes |
| DATA_DATE | 2 | 0.0% | Imputation ou suppression lignes |
| SPHEREECO | 3602 | 66.7% | Supprimer la colonne |
| DOMPUB | 3602 | 66.7% | Supprimer la colonne |
| SPHEREECO_label | 3602 | 66.7% | Supprimer la colonne |
| DOMPUB_label | 3602 | 66.7% | Supprimer la colonne |

---

## Statistiques OBS_VALUE

| Statistique | Valeur |
|-------------|--------|
| Min | 0.00 |
| Max | 1,820,029.00 |
| Moyenne | 29,688.54 |
| Médiane | 3,401.50 |
| Écart-type | 89,567.14 |

---

## Valeurs catégorielles

### UNIT

| Valeur | Count | % |
|--------|-------|---|
| NBET | 2700 | 50.0% |
| NBSALET | 2700 | 50.0% |

### NA17

| Valeur | Count | % |
|--------|-------|---|
| ENS | 200 | 3.7% |
| AZ | 200 | 3.7% |
| C1 | 200 | 3.7% |
| C2 | 200 | 3.7% |
| C3 | 200 | 3.7% |
| C4 | 200 | 3.7% |
| C5 | 200 | 3.7% |
| DE | 200 | 3.7% |
| FZ | 200 | 3.7% |
| GZ | 200 | 3.7% |
| ... | (8 autres) | - |

### SPHEREECO

| Valeur | Count | % |
|--------|-------|---|
| ENS | 600 | 11.1% |
| 1 | 600 | 11.1% |
| 2 | 600 | 11.1% |

### DOMPUB

| Valeur | Count | % |
|--------|-------|---|
| ENS | 600 | 11.1% |
| 1 | 600 | 11.1% |
| 2 | 600 | 11.1% |

---

## Synthèse pour le traitement

### Colonnes retenues
- **CODEGEO**: Clé de jointure - ESSENTIELLE
- **UNIT**: Filtrage données - IMPORTANTE
- **NA17**: Secteur activité - IMPORTANTE
- **OBS_VALUE**: Donnée principale - ESSENTIELLE
- **SPHEREECO**: Sphère économique - IMPORTANTE
- **DOMPUB**: Public/Privé - IMPORTANTE

### Colonnes exclues
- NIVGEO
- NA17_label
- DATASET_VERSION
- DATASET_NAME
- SPHEREECO_label
- DOMPUB_label

### Nettoyage à effectuer
- Supprimer les 5402 lignes avec valeurs manquantes
- Supprimer les colonnes métadonnées non utilisées
- Renommer les colonnes pour plus de clarté si besoin
