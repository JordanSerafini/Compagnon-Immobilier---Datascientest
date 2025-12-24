# Analyse: entreprises_departements.csv

> **Description**: Stock et créations entreprises par département
> **Source**: INSEE - REE 2019-2020 via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/2012696
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 3,333 |
| **Nombre de colonnes** | 12 |
| **Taille fichier** | 576.5 KB |
| **Taux de données manquantes global** | 16.7% |

---

## Analyse des colonnes

| Colonne | Type | NA | NA% | Uniques | Pertinence |
|---------|------|-----|-----|---------|------------|
| CODEGEO | object | 0 | 0.0% | 101 | Clé de jointure - ESSENTIELLE |
| NIVGEO | object | 0 | 0.0% | 1 | Niveau géo - SUPPRIMABLE |
| UNIT_label_fr | object | 0 | 0.0% | 4 | Compréhension - UTILE |
| UNIT | object | 0 | 0.0% | 4 | Filtrage données - IMPORTANTE |
| NA10_HORS_AZ | object | 303 | 9.1% | 10 | Secteur activité - IMPORTANTE |
| OBS_VALUE | int64 | 0 | 0.0% | 2688 | Donnée principale - ESSENTIELLE |
| NA10_HORS_AZ_label | object | 303 | 9.1% | 1 | Redondant - SUPPRIMABLE |
| DATASET_VERSION | object | 0 | 0.0% | 2 | Métadonnée - SUPPRIMABLE |
| DATASET_NAME | object | 0 | 0.0% | 1 | Métadonnée - SUPPRIMABLE |
| DATA_DATE | int64 | 0 | 0.0% | 2 | Année données - CONTEXTE |
| ENTR_INDIVIDUELLE | object | 3030 | 90.9% | 3 | À évaluer |
| ENTR_INDIVIDUELLE_label | object | 3030 | 90.9% | 1 | Redondant - SUPPRIMABLE |

---

## Données manquantes

| Colonne | Lignes NA | % NA | Recommandation |
|---------|-----------|------|----------------|
| NA10_HORS_AZ | 303 | 9.1% | Imputation ou suppression lignes |
| NA10_HORS_AZ_label | 303 | 9.1% | Imputation ou suppression lignes |
| ENTR_INDIVIDUELLE | 3030 | 90.9% | Supprimer la colonne |
| ENTR_INDIVIDUELLE_label | 3030 | 90.9% | Supprimer la colonne |

---

## Statistiques OBS_VALUE

| Statistique | Valeur |
|-------------|--------|
| Min | 10.00 |
| Max | 566,025.00 |
| Moyenne | 7,886.18 |
| Médiane | 2,294.00 |
| Écart-type | 22,270.21 |

---

## Valeurs catégorielles

### UNIT

| Valeur | Count | % |
|--------|-------|---|
| NBCRET | 1010 | 30.3% |
| NBET | 1010 | 30.3% |
| NBENT | 1010 | 30.3% |
| NBCRENT | 303 | 9.1% |

### NA10_HORS_AZ

| Valeur | Count | % |
|--------|-------|---|
| ENS | 303 | 9.1% |
| BE | 303 | 9.1% |
| FZ | 303 | 9.1% |
| GI | 303 | 9.1% |
| JZ | 303 | 9.1% |
| KZ | 303 | 9.1% |
| LZ | 303 | 9.1% |
| MN | 303 | 9.1% |
| OQ | 303 | 9.1% |
| RU | 303 | 9.1% |

---

## Synthèse pour le traitement

### Colonnes retenues
- **CODEGEO**: Clé de jointure - ESSENTIELLE
- **UNIT**: Filtrage données - IMPORTANTE
- **NA10_HORS_AZ**: Secteur activité - IMPORTANTE
- **OBS_VALUE**: Donnée principale - ESSENTIELLE

### Colonnes exclues
- NIVGEO
- NA10_HORS_AZ_label
- DATASET_VERSION
- DATASET_NAME
- ENTR_INDIVIDUELLE_label

### Nettoyage à effectuer
- Supprimer les 3333 lignes avec valeurs manquantes
- Supprimer les colonnes métadonnées non utilisées
- Renommer les colonnes pour plus de clarté si besoin
