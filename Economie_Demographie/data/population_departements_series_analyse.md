# Analyse: population_departements_series.csv

> **Description**: Estimations de population par département (séries temporelles)
> **Source**: INSEE - Dataset TCRED-ESTIMATIONS-POPULATION via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/series/103046780
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 9,687 |
| **Nombre de colonnes** | 47 |
| **Départements couverts** | 101 |
| **Période temporelle** | 1975 à 2025 (50 ans) |
| **Fréquence** | Annuelle |

---

## Structure des données

### Ventilation par sexe

| Code | Description |
|------|-------------|
| 0 | Ensemble (total) |
| 1 | Hommes |
| 2 | Femmes |

### Ventilation par âge

| Code | Description |
|------|-------------|
| Y_LT20 | Moins de 20 ans |
| Y20-39 | 20-39 ans |
| Y40-59 | 40-59 ans |
| Y60-74 | 60-74 ans |
| Y_GE75 | 75 ans et plus |

---

## Colonnes principales

| Colonne | Type | Description | Pertinence |
|---------|------|-------------|------------|
| TIME_PERIOD | object | Année | ESSENTIELLE |
| OBS_VALUE | float64 | Population (milliers) | ESSENTIELLE |
| REF_AREA | object | Code département | ESSENTIELLE |
| REF_AREA_label_fr | object | Nom département | UTILE |
| SEXE | object | Code sexe (0/1/2) | IMPORTANTE |
| AGE | object | Tranche d'âge | IMPORTANTE |

---

## Utilisation prévue

### Indicateurs à calculer

1. **Population totale par département**
   - Filtrer: SEXE=0, AGE=total

2. **Structure par âge**
   - Ratio jeunes (<20) / seniors (>60)
   - Indice de vieillissement

3. **Évolution démographique**
   - Taux de croissance annuel
   - Projection tendancielle

### Jointures possibles

- Avec revenus_departements.csv sur CODEGEO
- Avec chomage_departements_complet.csv sur REF_AREA
- Avec emploi_departements.csv sur CODEGEO

---

## Synthèse pour le traitement

### Colonnes retenues

- **TIME_PERIOD**: Année
- **OBS_VALUE**: Population
- **REF_AREA**: Code département
- **SEXE**: Ventilation sexe
- **AGE**: Tranche d'âge

### Colonnes exclues

- Toutes les colonnes `*_label_en`
- Colonnes métadonnées (IDBANK, DATASET, etc.)

### Nettoyage à effectuer

- Pivoter les données pour avoir une colonne par tranche d'âge
- Calculer les ratios démographiques
