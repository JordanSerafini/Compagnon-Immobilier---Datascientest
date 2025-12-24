# Analyse: revenus_menages_departements.csv

> **Description**: Revenus disponibles des ménages par département
> **Source**: INSEE - Dataset TCRED-SALAIRES-REVENUS-MEN via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/series/103046780
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 1,940 |
| **Nombre de colonnes** | 38 |
| **Départements couverts** | 98 |
| **Période temporelle** | 2012 à 2015 |
| **Fréquence** | Annuelle |

---

## Indicateurs disponibles

| Indicateur | Description |
|------------|-------------|
| Revenu médiane | Revenu disponible par UC : Médiane |
| 1er décile | Revenu disponible par UC : 1er décile (D1) |
| 9e décile | Revenu disponible par UC : 9e décile (D9) |
| Taux imposition | Part des ménages fiscaux imposés |
| Nb ménages | Nombre total de ménages fiscaux |

---

## Colonnes principales

| Colonne | Type | Description | Pertinence |
|---------|------|-------------|------------|
| TIME_PERIOD | object | Année | ESSENTIELLE |
| OBS_VALUE | float64 | Valeur de l'indicateur | ESSENTIELLE |
| REF_AREA | object | Code département (D01, D02...) | ESSENTIELLE |
| TITLE_FR | object | Description complète série | UTILE |
| INDICATEUR | object | Code indicateur | IMPORTANTE |

---

## Utilisation prévue

### Indicateurs exploitables

1. **Revenu médian par département**
   - Indicateur clé du pouvoir d'achat
   - Corrélation avec prix immobilier

2. **Rapport interdécile D9/D1**
   - Mesure des inégalités territoriales
   - Segmentation marchés immobiliers

3. **Taux d'imposition**
   - Indicateur de richesse fiscale
   - Capacité d'investissement

### Jointures possibles

- Avec chomage_departements_complet.csv sur REF_AREA
- Avec population_departements_series.csv sur REF_AREA
- Avec revenus_departements.csv sur CODEGEO (conversion D->code)

---

## Limitations

- **Période limitée**: Données 2012-2015 uniquement
- Données plus récentes disponibles dans revenus_departements.csv (FILOSOFI 2018)
