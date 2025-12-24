# Analyse: chomage_regions.csv

> **Description**: Taux de chômage localisé par département
> **Source**: INSEE - Séries IDBANK via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/series/102760674
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 2,100 |
| **Nombre de colonnes** | 42 |
| **Taille fichier** | ~1.2 MB |
| **Départements couverts** | 12 (70 à 81) |
| **Période temporelle** | 1982-Q1 à 2024-Q3 (175 trimestres) |
| **Taux de données manquantes global** | 6.8% |

---

## Couverture géographique

| Département | Région |
|-------------|--------|
| 70 - Haute-Saône | Bourgogne-Franche-Comté |
| 71 - Saône-et-Loire | Bourgogne-Franche-Comté |
| 72 - Sarthe | Pays de la Loire |
| 73 - Savoie | Auvergne-Rhône-Alpes |
| 74 - Haute-Savoie | Auvergne-Rhône-Alpes |
| 75 - Paris | Île-de-France |
| 76 - Seine-Maritime | Normandie |
| 77 - Seine-et-Marne | Île-de-France |
| 78 - Yvelines | Île-de-France |
| 79 - Deux-Sèvres | Nouvelle-Aquitaine |
| 80 - Somme | Hauts-de-France |
| 81 - Tarn | Occitanie |

---

## Analyse des colonnes

| Colonne | Type | NA | NA% | Uniques | Pertinence |
|---------|------|-----|-----|---------|------------|
| TIME_PERIOD | object | 0 | 0.0% | 175 | Clé temporelle - ESSENTIELLE |
| OBS_VALUE | float64 | 0 | 0.0% | 87 | Taux de chômage (%) - ESSENTIELLE |
| REF_AREA | object | 0 | 0.0% | 12 | Code département (D70, D71...) - UTILE |
| REF_AREA_label_fr | object | 0 | 0.0% | 12 | Nom département - UTILE |
| REGION | object | 0 | 0.0% | 8 | Région - IMPORTANTE |
| FREQ | object | 0 | 0.0% | 1 | Fréquence (T=Trimestrielle) - UTILE |
| DATE | object | 0 | 0.0% | 175 | Date formatée - UTILE |
| OBS_REV | float64 | 2002 | 95.3% | 1 | À supprimer |

---

## Données manquantes

| Colonne | Lignes NA | % NA | Recommandation |
|---------|-----------|------|----------------|
| OBS_REV | 2002 | 95.3% | Supprimer la colonne |
| OBS_REV_label_fr | 2002 | 95.3% | Supprimer la colonne |
| OBS_REV_label_en | 2002 | 95.3% | Supprimer la colonne |

---

## Statistiques OBS_VALUE (Taux de chômage %)

| Statistique | Valeur |
|-------------|--------|
| Min | 3.80% |
| Max | 12.60% |
| Moyenne | 7.91% |
| Médiane | 7.80% |
| Écart-type | 1.77 |

---

## Distribution par région

| Région | Nb enregistrements | % |
|--------|-------------------|---|
| Île-de-France | 525 | 25.0% |
| Bourgogne-Franche-Comté | 350 | 16.7% |
| Auvergne-Rhône-Alpes | 350 | 16.7% |
| Pays de la Loire | 175 | 8.3% |
| Normandie | 175 | 8.3% |
| Nouvelle-Aquitaine | 175 | 8.3% |
| Hauts-de-France | 175 | 8.3% |
| Occitanie | 175 | 8.3% |

---

## Synthèse pour le traitement

### Colonnes retenues

- **TIME_PERIOD**: Clé temporelle
- **OBS_VALUE**: Taux de chômage
- **REF_AREA_label_fr**: Nom du département
- **REGION**: Région administrative
- **DATE**: Date formatée

### Colonnes exclues

- Toutes les colonnes `*_label_en` (labels anglais)
- OBS_REV, OBS_REV_label_fr, OBS_REV_label_en (95% manquantes)
- Colonnes métadonnées non utilisées

### Limitations

- **Couverture partielle**: Seulement 12 départements sur 96
- Les départements couverts sont dans la tranche 70-81
- Fichier remplacé par chomage_departements_complet.csv (100 départements)

### Utilisation prévue
- Analyse historique du chômage régional
- Complément au fichier chomage_departements_complet
