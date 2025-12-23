# Analyse: chomage_departements_complet.csv

> **Description**: Taux de chômage trimestriel par département (France entière)
> **Source**: INSEE - Dataset TAUX-CHOMAGE via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/series/102760674
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 16,988 |
| **Nombre de colonnes** | 43 |
| **Départements couverts** | 100 (métropole + DOM) |
| **Régions couvertes** | 17 (13 métro + 4 DOM) |
| **Période temporelle** | 1982-Q1 à 2025-Q3 (175 trimestres) |

---

## Couverture géographique

### Métropole (96 départements)

| Région | Nb départements |
|--------|-----------------|
| Occitanie | 13 |
| Auvergne-Rhône-Alpes | 12 |
| Nouvelle-Aquitaine | 12 |
| Grand Est | 10 |
| Bourgogne-Franche-Comté | 8 |
| Île-de-France | 8 |
| Provence-Alpes-Côte d'Azur | 6 |
| Centre-Val de Loire | 6 |
| Hauts-de-France | 5 |
| Normandie | 5 |
| Pays de la Loire | 5 |
| Bretagne | 4 |
| Corse | 2 |

### DOM (4 départements)
- Guadeloupe (971)
- Martinique (972)
- Guyane (973)
- La Réunion (974)

---

## Colonnes principales

| Colonne | Type | Description | Pertinence |
|---------|------|-------------|------------|
| TIME_PERIOD | object | Trimestre (YYYY-QN) | ESSENTIELLE |
| OBS_VALUE | float64 | Taux de chômage (%) | ESSENTIELLE |
| REF_AREA | object | Code département (D01, D02...) | ESSENTIELLE |
| REF_AREA_label_fr | object | Nom département | UTILE |
| REGION | object | Nom région (ajouté) | IMPORTANTE |
| DEPT_CODE | object | Code département simple | UTILE |

---

## Statistiques OBS_VALUE (Taux de chômage %)

| Statistique | Valeur |
|-------------|--------|
| Min | 3.7% |
| Max | 27.5% (DOM) |
| Moyenne | 8.5% |
| Médiane | 8.0% |

### Extremes

| Extrême | Département | Taux |
|---------|-------------|------|
| Plus bas | Cantal (15) | 3.7% |
| Plus haut | La Réunion (974) | 27.5% |

---

## Comparaison avec ancien fichier

| Fichier | Départements | Lignes |
|---------|--------------|--------|
| chomage_regions.csv (ancien) | 12 | 2,100 |
| **chomage_departements_complet.csv** | **100** | **16,988** |

Le nouveau fichier remplace chomage_regions.csv avec une couverture complète.

---

## Recommandations

### Colonnes à conserver

- **TIME_PERIOD**: Clé temporelle
- **OBS_VALUE**: Taux de chômage
- **REF_AREA**: Code département
- **REF_AREA_label_fr**: Nom département
- **REGION**: Région administrative

### Colonnes à supprimer

- Toutes les colonnes `*_label_en`
- Colonnes métadonnées redondantes

### Utilisation

- Analyse des disparités territoriales du chômage
- Corrélation chômage / prix immobilier par département
- Clustering des territoires selon dynamique emploi
