# Analyse: prix_logements_indices.csv

> **Description**: Indices des prix des logements Notaires-INSEE
> **Source**: INSEE - Dataset IPLA-IPLNA-2015 via pynsee
> **Date d'extraction**: 2025-12-23
> **URL source**: https://www.insee.fr/fr/statistiques/series/102761046
> **API**: https://api.insee.fr/catalogue/

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 15,296 |
| **Nombre de colonnes** | 50 |
| **Zones géographiques** | 32 |
| **Période temporelle** | 1992-Q1 à 2025-Q3 |
| **Fréquence** | Trimestrielle |
| **Base indice** | 100 en 2015 |

---

## Indicateurs disponibles

| Indicateur | Description |
|------------|-------------|
| Logements neufs et anciens | Indice global tous types |
| Logements neufs | Construction neuve uniquement |
| Logements anciens | Marché de l'ancien |
| Appartements anciens | Détail appartements |
| Maisons anciennes | Détail maisons |

---

## Couverture géographique

### Zones nationales
- FM: France métropolitaine
- FR-D976: France hors Mayotte

### Régions
- R11: Île-de-France
- R32: Hauts-de-France
- R84: Auvergne-Rhône-Alpes
- R93: Provence-Alpes-Côte d'Azur
- ...

### Île-de-France détaillée
- D75: Paris
- D77: Seine-et-Marne
- D78: Yvelines
- D91: Essonne
- D95: Val-d'Oise
- R11_PC: Petite Couronne

### Agglomérations
- A_69123: Agglomération de Lyon
- A_59350: Agglomération de Lille

### Zones réglementaires
- ZONE-A, ZONE-B1, ZONE-B2, ZONE-C

---

## Colonnes principales

| Colonne | Type | Description | Pertinence |
|---------|------|-------------|------------|
| TIME_PERIOD | object | Trimestre (YYYY-QN) | ESSENTIELLE |
| OBS_VALUE | float64 | Indice (base 100 = 2015) | ESSENTIELLE |
| REF_AREA | object | Code zone géographique | ESSENTIELLE |
| INDICATEUR | object | Type de logement | IMPORTANTE |
| TITLE_FR | object | Description complète | UTILE |

---

## Évolution historique

| Période | Indice (FM, tous logements) |
|---------|----------------------------|
| 2000-Q1 | ~48 |
| 2008-Q1 | ~95 (pic avant crise) |
| 2015-Q1 | 100 (base) |
| 2020-Q1 | ~107 |
| 2025-Q3 | ~115 |

---

## Exploitation envisagée

### Analyses envisageables

1. **Évolution prix sur 30 ans**
   - Tendances longues du marché
   - Cycles immobiliers

2. **Comparaison régionale**
   - Disparités territoriales
   - Attractivité relative

3. **Neuf vs Ancien**
   - Écart de prix
   - Stratégie d'investissement

4. **Zones réglementaires**
   - Impact zonage Pinel/PTZ
   - Tension des marchés

### Jointures possibles

- Avec IPC (ipc_france.csv) pour prix réels
- Avec PIB (pib_france.csv) pour corrélation macro
- Croisement TIME_PERIOD trimestriel

---

## Points forts

- **Série longue**: 33 ans de données (1992-2025)
- **Données récentes**: Jusqu'à Q3 2025
- **Granularité**: Trimestrielle
- **Source officielle**: Notaires-INSEE
