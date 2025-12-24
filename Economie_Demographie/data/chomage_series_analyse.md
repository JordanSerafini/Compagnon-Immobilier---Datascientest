# Analyse: chomage_series.csv

> **Description**: Taux de chômage France
> **Source**: INSEE - Séries IDBANK via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/series/102760674
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 350 |
| **Nombre de colonnes** | 42 |
| **Taille fichier** | 210.4 KB |
| **Taux de données manquantes global** | 6.9% |

---

## Analyse des colonnes

| Colonne | Type | NA | NA% | Uniques | Pertinence |
|---------|------|-----|-----|---------|------------|
| TIME_PERIOD | object | 0 | 0.0% | 175 | Clé temporelle - ESSENTIELLE |
| OBS_VALUE | float64 | 0 | 0.0% | 53 | Donnée principale - ESSENTIELLE |
| OBS_STATUS | object | 0 | 0.0% | 2 | À évaluer |
| OBS_QUAL | object | 0 | 0.0% | 2 | À évaluer |
| OBS_TYPE | object | 0 | 0.0% | 1 | À évaluer |
| IDBANK | int64 | 0 | 0.0% | 2 | À évaluer |
| FREQ | object | 0 | 0.0% | 1 | Fréquence - UTILE |
| TITLE_FR | object | 0 | 0.0% | 2 | À évaluer |
| TITLE_EN | object | 0 | 0.0% | 2 | À évaluer |
| LAST_UPDATE | object | 0 | 0.0% | 1 | À évaluer |
| UNIT_MEASURE | object | 0 | 0.0% | 1 | À évaluer |
| UNIT_MULT | int64 | 0 | 0.0% | 1 | À évaluer |
| REF_AREA | object | 0 | 0.0% | 2 | Zone référence - UTILE |
| DECIMALS | int64 | 0 | 0.0% | 1 | À évaluer |
| OBS_REV | float64 | 337 | 96.3% | 1 | À évaluer |
| DATE | object | 0 | 0.0% | 175 | À évaluer |
| nomflow | object | 0 | 0.0% | 1 | À évaluer |
| cleFlow | object | 0 | 0.0% | 2 | À évaluer |
| INDICATEUR | object | 0 | 0.0% | 1 | À évaluer |
| NATURE | object | 0 | 0.0% | 1 | À évaluer |
| CORRECTION | object | 0 | 0.0% | 1 | À évaluer |
| FREQ_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| FREQ_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| INDICATEUR_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| INDICATEUR_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| NATURE_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| NATURE_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| REF_AREA_label_fr | object | 0 | 0.0% | 2 | Redondant - SUPPRIMABLE |
| REF_AREA_label_en | object | 0 | 0.0% | 2 | Redondant - SUPPRIMABLE |
| UNIT_MEASURE_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| UNIT_MEASURE_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| CORRECTION_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| CORRECTION_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| OBS_STATUS_label_fr | object | 0 | 0.0% | 2 | Redondant - SUPPRIMABLE |
| OBS_STATUS_label_en | object | 0 | 0.0% | 2 | Redondant - SUPPRIMABLE |
| OBS_REV_label_fr | object | 337 | 96.3% | 1 | Redondant - SUPPRIMABLE |
| OBS_REV_label_en | object | 337 | 96.3% | 1 | Redondant - SUPPRIMABLE |
| OBS_TYPE_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| OBS_TYPE_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| OBS_QUAL_label_fr | object | 0 | 0.0% | 2 | Redondant - SUPPRIMABLE |
| OBS_QUAL_label_en | object | 0 | 0.0% | 2 | Redondant - SUPPRIMABLE |
| LABEL | object | 0 | 0.0% | 2 | À évaluer |

---

## Données manquantes

| Colonne | Lignes NA | % NA | Recommandation |
|---------|-----------|------|----------------|
| OBS_REV | 337 | 96.3% | Supprimer la colonne |
| OBS_REV_label_fr | 337 | 96.3% | Supprimer la colonne |
| OBS_REV_label_en | 337 | 96.3% | Supprimer la colonne |

---

## Statistiques OBS_VALUE

| Statistique | Valeur |
|-------------|--------|
| Min | 5.30 |
| Max | 10.70 |
| Moyenne | 7.80 |
| Médiane | 7.80 |
| Écart-type | 1.25 |

---

## Valeurs catégorielles

### FREQ

| Valeur | Count | % |
|--------|-------|---|
| T | 350 | 100.0% |

---

## Synthèse pour le traitement

### Colonnes retenues
- **TIME_PERIOD**: Clé temporelle - ESSENTIELLE
- **OBS_VALUE**: Donnée principale - ESSENTIELLE

### Colonnes exclues
- FREQ_label_fr
- FREQ_label_en
- INDICATEUR_label_fr
- INDICATEUR_label_en
- NATURE_label_fr
- NATURE_label_en
- REF_AREA_label_fr
- REF_AREA_label_en
- UNIT_MEASURE_label_fr
- UNIT_MEASURE_label_en
- CORRECTION_label_fr
- CORRECTION_label_en
- OBS_STATUS_label_fr
- OBS_STATUS_label_en
- OBS_REV_label_fr
- OBS_REV_label_en
- OBS_TYPE_label_fr
- OBS_TYPE_label_en
- OBS_QUAL_label_fr
- OBS_QUAL_label_en

### Nettoyage à effectuer
- Supprimer les colonnes avec >50% de valeurs manquantes
- Supprimer les colonnes métadonnées non utilisées
- Renommer les colonnes pour plus de clarté si besoin

### Utilisation prévue
- Indicateur macroéconomique national
- Contexte du marché de l'emploi pour l'analyse immobilière
- Corrélation chômage national / dynamique des prix
