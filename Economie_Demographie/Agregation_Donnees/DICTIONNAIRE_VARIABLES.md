# Dictionnaire des Variables - Économie & Démographie

## Fichiers Générés

| Fichier | Granularité | Lignes | Clé de jointure |
|---------|-------------|--------|-----------------|
| `features_eco_demo_COMMUNE.csv` | Commune | 31 325 | `code_commune` |
| `features_eco_demo_DEPARTEMENT.csv` | Département | 97 | `code_dept` |

---

## Variables Disponibles

### Identifiants

| Variable | Type | Description | Exemple |
|----------|------|-------------|---------|
| `code_commune` | str | Code INSEE commune (5 car.) | 01001, 75056 |
| `code_dept` | str | Code département (2-3 car.) | 01, 75, 2A |

### Démographie

| Variable | Type | Unité | Description |
|----------|------|-------|-------------|
| `pop_commune` | float | habitants | Population de la commune |
| `pop_departement` | float | habitants | Population du département |
| `nb_menages` | float | ménages | Nombre de ménages fiscaux |

### Économie - Revenus

| Variable | Type | Unité | Description |
|----------|------|-------|-------------|
| `revenu_median` | float | €/an | Revenu disponible médian |
| `taux_pauvrete` | float | % | Taux de pauvreté à 60% (NaN si secret stat.) |

### Économie - Emploi

| Variable | Type | Unité | Description |
|----------|------|-------|-------------|
| `taux_chomage` | float | % | Taux de chômage départemental |
| `nb_etablissements` | float | établ. | Nombre d'établissements (dept) |
| `nb_creations_entreprises` | float | créations | Créations d'entreprises (dept) |

### Indicateurs Dérivés

| Variable | Type | Unité | Description |
|----------|------|-------|-------------|
| `densite_etablissements` | float | /1000 hab | Établissements pour 1000 habitants |
| `dynamisme_entrepreneurial` | float | /1000 hab | Créations pour 1000 habitants |

### Contexte National

| Variable | Type | Unité | Description |
|----------|------|-------|-------------|
| `inflation_nationale` | float | % | Taux d'inflation annuel 2021 |
| `ipc_national` | float | indice | Indice des prix (base 100 = 2015) |

---

## Jointures avec Autres Sources

### Avec DVF (Prix immobiliers)
```python
# DVF contient code_commune
df_merged = df_dvf.merge(df_eco_commune, on='code_commune', how='left')
```

### Avec Sécurité (Criminalité)
```python
# Sécurité contient CODGEO_2025 = code_commune
df_secu['code_commune'] = df_secu['CODGEO_2025']
df_merged = df_secu.merge(df_eco_commune, on='code_commune', how='left')
```

### Avec Éducation
```python
# Éducation contient code_commune ou code_postal
df_merged = df_educ.merge(df_eco_commune, on='code_commune', how='left')
```

### Conversion département ↔ commune
```python
# Extraire département depuis commune
code_dept = code_commune[:2]  # ou [:3] pour Corse

# Joindre features département à données commune
df = df.merge(df_eco_dept, on='code_dept', how='left')
```

---

## Valeurs Manquantes

| Variable | Manquantes | Raison |
|----------|------------|--------|
| `taux_pauvrete` | ~27 000 | Secret statistique (petites communes) |
| Autres | < 5% | Données DOM-TOM incomplètes |

**Recommandation** : Imputer `taux_pauvrete` par la moyenne départementale.

---

## Année de Référence

**2021** - Meilleure couverture des sources :
- FILOSOFI 2021 (revenus, pauvreté communale)
- Chômage T1-T4 2021
- Emploi/Entreprises 2018-2020 (agrégé)

---

## Source des Données

- **INSEE** (API pynsee) : chômage, population, IPC
- **FILOSOFI 2021** : revenus et pauvreté par commune
- **Flores 2018** : emploi par département
- **REE 2020** : créations d'entreprises
