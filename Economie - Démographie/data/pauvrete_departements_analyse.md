# Analyse: pauvrete_departements.csv

> **Description**: Taux de pauvreté par tranche d'âge et département
> **Source**: INSEE - Dataset TCRED-SALAIRES-REVENUS-TAUX-PAUVRETE-AGE via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/series/103046780
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 2,716 |
| **Nombre de colonnes** | 41 |
| **Départements couverts** | 98 |
| **Période temporelle** | 2012 à 2015 |
| **Fréquence** | Annuelle |

---

## Ventilation par âge

| Code | Tranche d'âge |
|------|---------------|
| Y_LT30 | Moins de 30 ans |
| Y30-39 | 30-39 ans |
| Y40-49 | 40-49 ans |
| Y50-59 | 50-59 ans |
| Y60-74 | 60-74 ans |
| Y_GE75 | 75 ans et plus |
| _T | Ensemble (tous âges) |

---

## Colonnes principales

| Colonne | Type | Description | Pertinence |
|---------|------|-------------|------------|
| TIME_PERIOD | object | Année | ESSENTIELLE |
| OBS_VALUE | float64 | Taux de pauvreté (%) | ESSENTIELLE |
| REF_AREA | object | Code département (D01, D02...) | ESSENTIELLE |
| AGE | object | Code tranche d'âge | IMPORTANTE |
| TITLE_FR | object | Description complète série | UTILE |

---

## Statistiques OBS_VALUE (Taux de pauvreté %)

| Statistique | Valeur |
|-------------|--------|
| Min | ~5% |
| Max | ~30% |
| Moyenne | ~14% |

---

## Exploitation envisagée

### Indicateurs exploitables

1. **Taux de pauvreté global (_T)**
   - Indicateur de précarité territoriale
   - Impact sur demande logement social

2. **Pauvreté jeunes (Y_LT30)**
   - Potentiel primo-accédants limité
   - Demande locative vs achat

3. **Pauvreté seniors (Y_GE75)**
   - Marché spécifique seniors
   - Résidences services

### Jointures possibles

- Avec chomage_departements_complet.csv sur REF_AREA
- Avec revenus_menages_departements.csv sur REF_AREA
- Avec population_departements_series.csv sur REF_AREA

---

## Limitations

- **Période limitée**: Données 2012-2015 uniquement
- Le seuil de pauvreté est à 60% du revenu médian
