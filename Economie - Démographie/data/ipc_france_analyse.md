# Analyse: ipc_france.csv

> **Description**: Indice des prix à la consommation France
> **Source**: INSEE - Séries IDBANK via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/series/102761046
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 431 |
| **Nombre de colonnes** | 56 |
| **Taille fichier** | 333.0 KB |
| **Taux de données manquantes global** | 0.0% |

---

## Analyse des colonnes

| Colonne | Type | NA | NA% | Uniques | Pertinence |
|---------|------|-----|-----|---------|------------|
| TIME_PERIOD | object | 0 | 0.0% | 431 | Clé temporelle - ESSENTIELLE |
| OBS_VALUE | float64 | 0 | 0.0% | 411 | Donnée principale - ESSENTIELLE |
| OBS_STATUS | object | 0 | 0.0% | 1 | À évaluer |
| OBS_QUAL | object | 0 | 0.0% | 1 | À évaluer |
| OBS_TYPE | object | 0 | 0.0% | 1 | À évaluer |
| IDBANK | int64 | 0 | 0.0% | 1 | À évaluer |
| FREQ | object | 0 | 0.0% | 1 | Fréquence - UTILE |
| TITLE_FR | object | 0 | 0.0% | 1 | À évaluer |
| TITLE_EN | object | 0 | 0.0% | 1 | À évaluer |
| LAST_UPDATE | object | 0 | 0.0% | 1 | À évaluer |
| UNIT_MEASURE | object | 0 | 0.0% | 1 | À évaluer |
| UNIT_MULT | int64 | 0 | 0.0% | 1 | À évaluer |
| REF_AREA | object | 0 | 0.0% | 1 | Zone référence - UTILE |
| DECIMALS | int64 | 0 | 0.0% | 1 | À évaluer |
| DATE | object | 0 | 0.0% | 431 | À évaluer |
| nomflow | object | 0 | 0.0% | 1 | À évaluer |
| cleFlow | object | 0 | 0.0% | 1 | À évaluer |
| INDICATEUR | object | 0 | 0.0% | 1 | À évaluer |
| FORME-VENTE | object | 0 | 0.0% | 1 | À évaluer |
| COICOP2016 | int64 | 0 | 0.0% | 1 | À évaluer |
| PRIX_CONSO | object | 0 | 0.0% | 1 | À évaluer |
| NATURE | object | 0 | 0.0% | 1 | À évaluer |
| MENAGES_IPC | object | 0 | 0.0% | 1 | À évaluer |
| CORRECTION | object | 0 | 0.0% | 1 | À évaluer |
| BASIND | int64 | 0 | 0.0% | 1 | À évaluer |
| SERIE_ARRETEE | bool | 0 | 0.0% | 1 | À évaluer |
| FREQ_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| FREQ_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| INDICATEUR_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| INDICATEUR_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| FORME-VENTE_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| FORME-VENTE_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| COICOP2016_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| COICOP2016_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| PRIX_CONSO_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| PRIX_CONSO_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| NATURE_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| NATURE_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| MENAGES_IPC_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| MENAGES_IPC_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| REF_AREA_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| REF_AREA_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| UNIT_MEASURE_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| UNIT_MEASURE_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| CORRECTION_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| CORRECTION_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| BASIND_label_fr | int64 | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| BASIND_label_en | int64 | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| SERIE_ARRETEE_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| SERIE_ARRETEE_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| OBS_STATUS_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| OBS_STATUS_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| OBS_TYPE_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| OBS_TYPE_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| OBS_QUAL_label_fr | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |
| OBS_QUAL_label_en | object | 0 | 0.0% | 1 | Redondant - SUPPRIMABLE |

---

## Données manquantes

**Aucune donnée manquante.**

---

## Statistiques OBS_VALUE

| Statistique | Valeur |
|-------------|--------|
| Min | 66.44 |
| Max | 122.24 |
| Moyenne | 91.35 |
| Médiane | 91.93 |
| Écart-type | 14.41 |

---

## Valeurs catégorielles

### FREQ

| Valeur | Count | % |
|--------|-------|---|
| M | 431 | 100.0% |

---

## Recommandations

### Colonnes à conserver
- **TIME_PERIOD**: Clé temporelle - ESSENTIELLE
- **OBS_VALUE**: Donnée principale - ESSENTIELLE

### Colonnes à supprimer
- FREQ_label_fr
- FREQ_label_en
- INDICATEUR_label_fr
- INDICATEUR_label_en
- FORME-VENTE_label_fr
- FORME-VENTE_label_en
- COICOP2016_label_fr
- COICOP2016_label_en
- PRIX_CONSO_label_fr
- PRIX_CONSO_label_en
- NATURE_label_fr
- NATURE_label_en
- MENAGES_IPC_label_fr
- MENAGES_IPC_label_en
- REF_AREA_label_fr
- REF_AREA_label_en
- UNIT_MEASURE_label_fr
- UNIT_MEASURE_label_en
- CORRECTION_label_fr
- CORRECTION_label_en
- BASIND_label_fr
- BASIND_label_en
- SERIE_ARRETEE_label_fr
- SERIE_ARRETEE_label_en
- OBS_STATUS_label_fr
- OBS_STATUS_label_en
- OBS_TYPE_label_fr
- OBS_TYPE_label_en
- OBS_QUAL_label_fr
- OBS_QUAL_label_en

### Nettoyage recommandé
- Supprimer les colonnes métadonnées non utilisées
- Renommer les colonnes pour plus de clarté si besoin
