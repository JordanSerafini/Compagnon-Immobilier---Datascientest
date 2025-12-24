# Analyse: pib_france.csv

> **Description**: Comptes trimestriels du PIB France (équilibre ressources-emplois)
> **Source**: INSEE - Dataset CNT-2020-PIB-EQB-RF via pynsee
> **Date d'extraction**: 2025-12-24

---

## Résumé

| Métrique | Valeur |
|----------|--------|
| **Nombre de lignes** | 20,435 |
| **Nombre de colonnes** | 56 |
| **Période couverte** | 1949-Q1 à 2025-Q3 |
| **Fréquence** | Trimestrielle |
| **Base comptable** | 2020 |

---

## Contenu des séries

Le dataset contient plusieurs types de séries :
- Taux de croissance du PIB (variation trimestrielle en %)
- Contributions à la croissance (demande intérieure, exports, imports...)
- Valeurs absolues en millions d'euros

### Indicateurs principaux

| Indicateur | Description |
|------------|-------------|
| PIB | Produit intérieur brut |
| P3 | Dépenses de consommation finale |
| P51G | Formation brute de capital fixe |
| P6 | Exportations |
| P7 | Importations |
| B1G | Valeur ajoutée brute |

---

## Colonnes principales

| Colonne | Type | Description | Pertinence |
|---------|------|-------------|------------|
| TIME_PERIOD | object | Trimestre (YYYY-QN) | ESSENTIELLE |
| OBS_VALUE | float64 | Valeur (taux ou montant) | ESSENTIELLE |
| TITLE_FR | object | Description de la série | UTILE |
| REF_AREA | object | Zone géographique (FE=France) | INFO |
| IDBANK | int64 | Identifiant série INSEE | TECHNIQUE |
| NATURE | object | Type de donnée (TAUX, VALEUR_ABSOLUE...) | IMPORTANTE |

---

## Statistiques OBS_VALUE

Les valeurs sont de nature différente selon les séries :
- Taux de croissance : entre -13.5% et +17.5%
- Montants absolus : jusqu'à 750 milliards d'euros

| Statistique | Valeur |
|-------------|--------|
| Min | -26,184 |
| Max | 750,662 |
| Valeurs négatives | 2,104 (contributions négatives) |

---

## Synthèse pour le traitement

### Colonnes retenues
- **TIME_PERIOD**: Clé temporelle
- **OBS_VALUE**: Valeur
- **TITLE_FR**: Description
- **REF_AREA**: Zone

### Colonnes exclues
- Toutes les colonnes `*_label_en` (labels anglais)
- Colonnes métadonnées redondantes (56 → 5-7 colonnes)

### Notes
- Les valeurs négatives sont normales (contributions négatives au PIB)
- Filtrer sur NATURE='TAUX' pour n'avoir que les taux de croissance

### Utilisation prévue
- Contexte macroéconomique pour l'analyse immobilière
- Corrélation PIB / dynamique des prix immobiliers
- Variable explicative pour les modèles de prédiction
