# Audit des Donnees - Compagnon Immobilier

**Date:** 26/12/2024
**Objectif:** Inventaire et analyse des sources de donnees disponibles pour l'agregation

---

## 1. Vue d'ensemble

| Source | Granularite | Volume | Periode | Qualite |
|--------|-------------|--------|---------|---------|
| Economie_Demographie | Commune/Dept/National | 18 fichiers CSV | 1975-2025 | Propre |
| Education_Securite | Commune | 4.7M lignes | 2016-2024 | ~46% NaN |
| Prix immobilier (DVF) | Transaction | 20M lignes | 2020-2025 | Brut |
| Annonces (ech_68) | Annonce | 39K lignes | 2019-2023 | Enrichi |

---

## 2. Economie & Demographie (INSEE)

**Localisation:** `Economie_Demographie/data/clean/`
**Source:** API INSEE (pynsee)

### 2.1 Donnees communales (granularite fine)

| Fichier | Lignes | Cles | Variables principales |
|---------|--------|------|----------------------|
| `revenus_communes_2021_clean.csv` | 31,325 | code_commune, code_dept | nb_menages, nb_personnes, **revenu_median** |
| `pauvrete_communes_2021_clean.csv` | 4,396 | code_commune, code_dept | **taux_pauvrete** |

### 2.2 Donnees departementales

| Fichier | Lignes | Cles | Variables principales |
|---------|--------|------|----------------------|
| `chomage_departements_clean.csv` | 16,988 | zone (D##), periode | **taux_chomage** |
| `emploi_clean.csv` | 5,396 | code_dept, annee | **nb_etablissements** |
| `entreprises_clean.csv` | 3,328 | code_dept, annee | **nb_creations** |
| `population_series_clean.csv` | 9,687 | zone (D##), periode | **population** |
| `revenus_departements_clean.csv` | 1,764 | code_dept, annee | revenu |
| `revenus_menages_clean.csv` | 1,940 | zone (D##), periode | revenu median |
| `pauvrete_clean.csv` | 2,716 | zone (D##), periode | taux_pauvrete |
| `population_logements_clean.csv` | 1,800 | code_dept, annee | nb_logements |

### 2.3 Donnees nationales (series temporelles)

| Fichier | Lignes | Periode | Variables principales |
|---------|--------|---------|----------------------|
| `prix_logements_clean.csv` | 15,292 | 2000-2024 | **indice_prix** (32 zones) |
| `ipc_clean.csv` | 431 | 1990-2025 | indice_prix, **inflation** |
| `pib_clean.csv` | 20,435 | 1950-2024 | valeur PIB |
| `chomage_national_clean.csv` | 19,130 | 1975-2024 | taux_chomage |
| `construction_logements_clean.csv` | 26,000 | 2000-2024 | nb_logements autorises |
| `parc_logements_clean.csv` | 1,144 | 1982-2024 | nb_logements total |
| `population_france_clean.csv` | 383 | 1994-2024 | population |
| `chomage_regions_clean.csv` | 2,100 | 1982-2024 | taux_chomage regional |

### 2.4 Points d'attention

- **Revenus/Pauvrete communes:** Annee 2021 uniquement
- **Chomage dept:** Series trimestrielles depuis 1982
- **Prix logements:** 32 zones seulement (grandes agglos), pas de granularite departementale complete
- **Emploi/Entreprises:** Annees fixes (2018/2020)

---

## 3. Securite - Criminalite

**Localisation:** `Education_Securite/`
**Source:** Ministere de l'Interieur (data.gouv.fr)
**Format:** Parquet (14.6 MB)

### 3.1 Structure

| Colonne | Description |
|---------|-------------|
| `CODGEO_2025` | Code commune INSEE (5 chiffres) |
| `annee` | 2016 - 2024 |
| `indicateur` | Type de crime/delit |
| `nombre` | Nombre d'infractions |
| `taux_pour_mille` | Taux pour 1000 habitants |
| `insee_pop` | Population commune |
| `insee_log` | Nombre de logements |

### 3.2 Indicateurs disponibles (15)

1. Violences physiques intrafamiliales
2. Violences physiques hors cadre familial
3. Violences sexuelles
4. Vols avec armes
5. Vols violents sans arme
6. Vols sans violence contre des personnes
7. **Cambriolages de logement** (pertinent immo)
8. Vols de vehicule
9. Vols dans les vehicules
10. Vols d'accessoires sur vehicules
11. Destructions et degradations volontaires
12. Usage de stupefiants
13. Usage de stupefiants (AFD)
14. Trafic de stupefiants
15. Escroqueries et fraudes

### 3.3 Statistiques

- **4,714,200** enregistrements
- **34,920** communes couvertes
- **9 annees** (2016-2024)
- **~46% valeurs manquantes** sur nombre/taux (petites communes non diffusees)

### 3.4 Points d'attention

- Donnees non diffusees (`ndiff`) pour petites communes (secret statistique)
- Utiliser `taux_pour_mille` plutot que `nombre` pour comparaisons

---

## 4. Prix Immobilier - DVF

**Localisation:** `Prix immobilier/Data/`
**Source:** data.gouv.fr - Demandes de Valeurs Foncieres
**Format:** CSV compresse (.gz)

### 4.1 Fichiers disponibles

| Fichier | Taille | Transactions |
|---------|--------|--------------|
| DVF_2020.gz | 53.5 MB | 2,065,003 |
| DVF_2021.gz | 116.7 MB | 4,674,176 |
| DVF_2022.gz | 117.1 MB | 4,675,007 |
| DVF_2023.gz | 96.7 MB | 3,812,327 |
| DVF_2024.gz | 88.1 MB | 3,489,149 |
| DVF_2025.gz | 35.7 MB | 1,387,077 |
| **TOTAL** | **508 MB** | **20,102,739** |

### 4.2 Colonnes cles (40 colonnes total)

| Colonne | Description | Usage |
|---------|-------------|-------|
| `id_mutation` | Identifiant transaction | Cle primaire |
| `date_mutation` | Date de vente | Temporel |
| `valeur_fonciere` | Prix de vente (EUR) | **Target ML** |
| `code_commune` | Code INSEE commune | **Jointure** |
| `code_departement` | Code departement | **Jointure** |
| `type_local` | Maison/Appartement/Dependance | Feature |
| `surface_reelle_bati` | Surface habitable (m2) | Feature |
| `nombre_pieces_principales` | Nb pieces | Feature |
| `surface_terrain` | Surface terrain (m2) | Feature |
| `longitude` | Coordonnee GPS | Geoloc |
| `latitude` | Coordonnee GPS | Geoloc |

### 4.3 Points d'attention

- **Donnees brutes:** Necessite nettoyage (doublons, valeurs aberrantes)
- **Plusieurs lignes par mutation:** Une vente = plusieurs lots
- **Types de biens:** Filtrer sur Maison/Appartement (exclure dependances, terrains)
- **Valeurs extremes:** Prix < 10k EUR ou > 10M EUR a verifier
- **Annee 2025:** Donnees partielles

### 4.4 Annonces immobilieres (echantillon dept 68)

**Fichiers:** `ech_annonces_ventes_68.csv`, `ech_annonces_locations_68.csv`
**Source:** Scraping annonces
**Periode:** 2019-02 -> 2023-04

| Fichier | Lignes | Colonnes | Type |
|---------|--------|----------|------|
| ech_annonces_ventes_68.csv | 27,737 | 59 | Ventes |
| ech_annonces_locations_68.csv | 11,702 | 52 | Locations |

**Colonnes cles:**

| Colonne | Description |
|---------|-------------|
| `INSEE_COM` | Code commune INSEE |
| `DEP` | Code departement |
| `date` | Date (YYYY-MM) |
| `typedebien` | a=appartement, m=maison |
| `prix_bien` | Prix de vente |
| `surface` | Surface (m2) |
| `nb_pieces` | Nombre de pieces |
| `dpeL` / `dpeC` | Diagnostic energetique |
| `prix_m2_vente` | Prix au m2 (pre-calcule) |
| `loyer_m2_median_n6` | Loyer median zone |
| `taux_rendement_n6` | Rendement locatif |
| `mapCoordonneesLatitude/Longitude` | GPS |

**Avantages:** Donnees enrichies (DPE, rendement, loyers)
**Limite:** Uniquement departement 68 (Haut-Rhin)

---

## 5. Cles de jointure

### 5.1 Hierarchie geographique

```
Transaction DVF --> Commune --> Departement --> Region --> France
                     |             |
               code_commune   code_dept/zone
                (5 digits)    (2-3 digits)
```

### 5.2 Formats des codes

| Type | Format | Exemple |
|------|--------|---------|
| code_commune | 5 chiffres | 01001, 75056, 97411 |
| code_dept | 2-3 chiffres | 01, 75, 2A, 974 |
| zone INSEE | D + code | D01, D75, D2A |
| FM | France Metro | FM |
| FE | France Entiere | FE |

### 5.3 Fonctions de conversion

```python
# Commune -> Departement
def commune_to_dept(code_commune):
    code = str(code_commune).zfill(5)
    return code[:3] if code.startswith('97') else code[:2]

# Zone INSEE -> Departement
def zone_to_dept(zone):
    return zone[1:] if zone.startswith('D') else None
```

---

## 6. Strategie d'agregation MULTI-ANNEES (pour ML)

### 6.1 Periode optimale: **2020-2024** (5 ans)

Intersection des sources temporelles:
- DVF: 2020-2025
- Criminalite: 2016-2024
- Chomage: 1982-2025
- Population: 1975-2025
- **Intersection: 2020-2024**

### 6.2 Schema pivot: ANNEE x DEPARTEMENT

```
┌─────────────────────────────────────────────────────────────────┐
│                    DATASET PRINCIPAL                            │
│                    (annee, code_dept)                           │
├─────────────────────────────────────────────────────────────────┤
│ Dimensions: 100 departements x 5 annees = 500 lignes            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  DVF (agrege)          Criminalite (agrege)    Economie         │
│  ─────────────         ───────────────────     ────────         │
│  prix_m2_median        cambriolages_1000       taux_chomage     │
│  prix_m2_moyen         violences_1000          population       │
│  nb_transactions       vols_1000               nb_entreprises   │
│  part_maisons          score_securite          nb_emplois       │
│  surface_moyenne                                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 6.3 Jointures detaillees

```
NIVEAU 1: DVF -> Departement x Annee
────────────────────────────────────
DVF_YYYY.gz
  │ Filtrer: type_local IN ('Maison', 'Appartement')
  │ Calculer: prix_m2 = valeur_fonciere / surface_reelle_bati
  │ Extraire: annee = year(date_mutation)
  │ Extraire: code_dept = code_departement
  └─> GROUP BY (annee, code_dept)
      └─> prix_m2_median, prix_m2_moyen, nb_transactions, etc.

NIVEAU 2: Criminalite -> Departement x Annee
────────────────────────────────────────────
criminalite.parquet
  │ Extraire: code_dept = CODGEO_2025[:2] (ou [:3] si 97x)
  │ Pivot: indicateur -> colonnes
  └─> GROUP BY (annee, code_dept)
      └─> cambriolages_1000, violences_1000, etc.

NIVEAU 3: Chomage -> Departement x Annee
─────────────────────────────────────────
chomage_departements_clean.csv
  │ Convertir: code_dept = zone[1:] (enlever 'D')
  │ Filtrer: annee IN (2020, 2021, 2022, 2023, 2024)
  └─> GROUP BY (annee, code_dept)
      └─> taux_chomage_moyen

NIVEAU 4: Population -> Departement x Annee
───────────────────────────────────────────
population_series_clean.csv
  │ Convertir: code_dept = zone[1:]
  │ Filtrer: annee IN (2020-2024)
  └─> SELECT population

FUSION FINALE:
──────────────
df_dvf_agg
  .merge(df_crime_agg, on=['annee', 'code_dept'])
  .merge(df_chomage_agg, on=['annee', 'code_dept'])
  .merge(df_pop_agg, on=['annee', 'code_dept'])
  --> dataset_dept_annuel.csv (500 lignes, ~20 colonnes)
```

### 6.4 Features temporelles pour ML

```python
# Pour chaque departement, calculer:
df['evolution_prix_1an'] = df.groupby('code_dept')['prix_m2_median'].pct_change(1)
df['evolution_prix_2ans'] = df.groupby('code_dept')['prix_m2_median'].pct_change(2)
df['evolution_chomage'] = df.groupby('code_dept')['taux_chomage'].pct_change(1)
df['evolution_crime'] = df.groupby('code_dept')['score_securite'].pct_change(1)

# Lag features (valeurs annee precedente)
df['prix_m2_lag1'] = df.groupby('code_dept')['prix_m2_median'].shift(1)
df['chomage_lag1'] = df.groupby('code_dept')['taux_chomage'].shift(1)
```

### 6.5 Dataset communal (enrichissement statique)

Pour les predictions au niveau transaction:
```
revenus_communes_2021 (snapshot)
  + pauvrete_communes_2021 (snapshot)
  + criminalite_2021 (pivot)
  --> Jointure sur code_commune pour enrichir DVF
```

### 6.6 Annonces dept 68 (cas particulier)

```
ech_annonces_ventes_68.csv
  │ Periode: 2019-2023
  │ Avantage: DPE, rendement locatif pre-calcule
  └─> Modele specifique dept 68 avec features enrichies
```

---

## 7. Indicateurs a calculer

### 7.1 Prix immobilier (DVF)

| Indicateur | Formule |
|------------|---------|
| prix_m2_median | median(valeur_fonciere / surface_reelle_bati) |
| prix_m2_moyen | mean(valeur_fonciere / surface_reelle_bati) |
| nb_transactions | count(id_mutation) |
| part_maisons | count(Maison) / count(total) |
| surface_moyenne | mean(surface_reelle_bati) |

### 7.2 Securite

| Indicateur | Formule |
|------------|---------|
| score_securite | moyenne ponderee des taux |
| cambriolages_1000 | taux cambriolages |
| violences_1000 | sum(violences intra + hors famille) |

### 7.3 Economie

| Indicateur | Formule |
|------------|---------|
| dynamisme_eco | nb_creations / population |
| densite_emploi | nb_etablissements / population |

---
