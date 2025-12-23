# Rapport Exploration - 2. Démographie et Économie

**Total: 62 705 lignes sur 14 fichiers**

## population_dept

**Fichier: population_departements.csv | Source: INSEE Recensement 2018**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| 1 | CODEGEO | Code département (01-976) | Oui | object | 0% | Aucun | 101 valeurs | Clé jointure |
| 2 | NIVGEO | Niveau géographique | Oui | object | 10.1% | Supprimer | DEP | Constante |
| 3 | UNIT_label_fr | Libellé type mesure | Oui | object | 10.1% | Supprimer | 3 catégories | Filtrer données |
| 4 | UNIT | Code type mesure | Oui | object | 10.1% | Supprimer | NBLOG,POP,DUREE | Code technique |
| 5 | STOCD | Code statut occupation | Oui | object | 10.1% | Supprimer | 6 catégories | Clé immo |
| 6 | OBS_VALUE | Valeur indicateur | Oui | float64 | 10.1% | Supprimer | 679 à 17.4M | Principale |
| 7 | STOCD_label | Libellé statut | Oui | object | 10.1% | Supprimer | 1 catégorie | Redondant |
| 8 | DATASET_VERSION | Version dataset | Oui | object | 10.1% | Supprimer | GEO2021RP2018 | Métadonnée |
| 9 | DATASET_NAME | Nom dataset | Oui | object | 10.1% | Supprimer | Recensement | Métadonnée |
| 10 | DATA_DATE | Année données | Oui | float64 | 10.1% | Supprimer | 2018 | Constante |

---

## revenus_dept

**Fichier: revenus_departements.csv | Source: INSEE FILOSOFI 2018**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| 1 | CODEGEO | Code département | Oui | object | 0% | Aucun | 101 valeurs | Clé jointure |
| 2 | NIVGEO | Niveau géographique | Oui | object | 0.3% | Supprimer | DEP | Constante |
| 3 | UNIT_label_fr | Libellé indicateur éco | Oui | object | 0.3% | Supprimer | 18 catégories | Important |
| 4 | UNIT | Code indicateur | Oui | object | 0.3% | Supprimer | 18 codes | Technique |
| 5 | INDICS_FILO_DISP | Code interne INSEE | Oui | float64 | 83.4% | Supprimer col | 1.0 | Peu utile |
| 6 | OBS_VALUE | Valeur indicateur | Oui | float64 | 0.3% | Supprimer | -29.5 à 2.5M | Principale |
| 7 | DATASET_VERSION | Version dataset | Oui | object | 0.3% | Supprimer | GEO2021FILO2018 | Métadonnée |
| 8 | DATASET_NAME | Nom dataset | Oui | object | 0.3% | Supprimer | FILOSOFI | Métadonnée |
| 9 | DATA_DATE | Année données | Oui | float64 | 0.3% | Supprimer | 2018 | Constante |

---

## emploi_dept

**Fichier: emploi_departements.csv | Source: INSEE Flores 2018**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| 1 | CODEGEO | Code département | Oui | object | 0% | Aucun | 101 valeurs | Clé jointure |
| 2 | NIVGEO | Niveau géographique | Oui | object | 0% | Supprimer | DEP | Constante |
| 3 | UNIT_label_fr | Libellé type mesure | Oui | object | 0% | Supprimer | 2 catégories | Comptage |
| 4 | UNIT | Code type mesure | Oui | object | 0% | Supprimer | NBET,NBSALET | Technique |
| 5 | NA17 | Code secteur activité | Oui | object | 33.4% | Variable | 18 catégories | Secteurs éco |
| 6 | OBS_VALUE | Valeur indicateur | Oui | float64 | 0% | Aucun | 0 à 1.82M | Principale |
| 7 | NA17_label | Libellé secteur | Oui | object | 33.4% | Variable | 17 secteurs | Description |
| 8 | SPHEREECO | Sphère économique | Oui | object | 66.7% | Variable | 3 catégories | Prod/Présent |
| 9 | DOMPUB | Domaine public | Oui | object | 66.7% | Variable | 3 catégories | Public/Privé |
| 10 | DATA_DATE | Année données | Oui | float64 | 0% | Supprimer | 2018 | Constante |

---

## entreprises_dept

**Fichier: entreprises_departements.csv | Source: INSEE REE 2019-2020**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| 1 | CODEGEO | Code département | Oui | object | 0% | Aucun | 101 valeurs | Clé jointure |
| 2 | NIVGEO | Niveau géographique | Oui | object | 0% | Aucun | DEP | Constante |
| 3 | UNIT_label_fr | Libellé type mesure | Oui | object | 0% | Aucun | 4 catégories | Comptage |
| 4 | UNIT | Code type mesure | Oui | object | 0% | Aucun | 4 codes | Technique |
| 5 | NA10_HORS_AZ | Code secteur hors agri | Oui | object | 9.1% | Variable | 10 catégories | Hors agricole |
| 6 | OBS_VALUE | Valeur indicateur | Oui | int64 | 0% | Aucun | 10 à 566K | Principale |
| 7 | DATASET_VERSION | Version dataset | Oui | object | 0% | Aucun | 2 versions | Métadonnée |
| 8 | DATA_DATE | Année données | Oui | int64 | 0% | Aucun | 2019,2020 | Récent |
| 9 | ENTR_INDIVIDUELLE | Type entreprise | Oui | object | 90.9% | Variable | 3 catégories | Juridique |

---

## chomage_dept_complet

**Fichier: chomage_departements_complet.csv | Source: INSEE TAUX-CHOMAGE**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| 1 | TIME_PERIOD | Date (YYYY-QN) | Oui | object | 0% | Aucun | 175 trim/dept | Clé temporelle |
| 2 | OBS_VALUE | Taux chômage (%) | Oui | float64 | 0% | Aucun | 3.7% à 27.5% | Principale |
| 3 | REF_AREA | Code département | Oui | object | 0% | Aucun | 100 codes D01-D974 | Clé géo |
| 4 | REF_AREA_label_fr | Nom département | Oui | object | 0% | Aucun | 100 départements | Label |
| 5 | REGION | Nom région | Oui | object | 0% | Aucun | 17 régions | Jointure géo |
| 6 | DEPT_CODE | Code simple | Oui | object | 0% | Aucun | 01 à 974 | Sans préfixe D |

---

## population_series

**Fichier: population_departements_series.csv | Source: INSEE TCRED-ESTIMATIONS**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| 1 | TIME_PERIOD | Année observation | Oui | object | 0% | Aucun | 1975-2025 (50 ans) | Clé temporelle |
| 2 | OBS_VALUE | Population (milliers) | Oui | float64 | 0% | Aucun | Variable/dept | Principale |
| 3 | REF_AREA | Code département | Oui | object | 0% | Aucun | 101 codes | Clé géo |
| 4 | REF_AREA_label_fr | Nom département | Oui | object | 0% | Aucun | 101 départements | Label |
| 5 | SEXE | Code sexe | Oui | object | 0% | Aucun | 0=Ens,1=H,2=F | Démographie |
| 6 | AGE | Tranche âge | Oui | object | 0% | Aucun | 5 tranches | Structure âge |

---

## prix_logements

**Fichier: prix_logements_indices.csv | Source: INSEE IPLA-IPLNA Notaires**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| 1 | TIME_PERIOD | Trimestre (YYYY-QN) | Oui | object | 0% | Aucun | 1992-Q1 à 2025-Q3 | Clé temporelle |
| 2 | OBS_VALUE | Indice (base 2015=100) | Oui | float64 | 0% | Aucun | 48 à 115 | Principale |
| 3 | REF_AREA | Code zone géo | Oui | object | 0% | Aucun | 32 zones | Régions/depts |
| 4 | INDICATEUR | Type logement | Oui | object | 0% | Aucun | 5 types | Neuf/Ancien |
| 5 | TITLE_FR | Description série | Oui | object | 0% | Aucun | Complète | Métadonnée |

---

## revenus_menages

**Fichier: revenus_menages_departements.csv | Source: INSEE TCRED-SALAIRES Melodi**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| 1 | TIME_PERIOD | Année | Oui | object | 0% | Aucun | 2012-2015 | Clé temporelle |
| 2 | OBS_VALUE | Valeur indicateur | Oui | float64 | 0% | Aucun | Variable | Principale |
| 3 | REF_AREA | Code département | Oui | object | 0% | Aucun | 98 depts | D01,D02... |
| 4 | TITLE_FR | Description série | Oui | object | 0% | Aucun | 5 indicateurs | Médiane/déciles |
| 5 | INDICATEUR | Code indicateur | Oui | object | 0% | Aucun | 5 types | Technique |

---

## pauvrete_dept

**Fichier: pauvrete_departements.csv | Source: INSEE TCRED-PAUVRETE Melodi**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| 1 | TIME_PERIOD | Année | Oui | object | 0% | Aucun | 2012-2015 | Clé temporelle |
| 2 | OBS_VALUE | Taux pauvreté (%) | Oui | float64 | 0% | Aucun | 5% à 30% | Principale |
| 3 | REF_AREA | Code département | Oui | object | 0% | Aucun | 98 depts | D01,D02... |
| 4 | AGE | Code tranche âge | Oui | object | 0% | Aucun | 7 tranches | Y_LT30... |
| 5 | TITLE_FR | Description série | Oui | object | 0% | Aucun | Complète | Métadonnée |

---

## series_nationales

**Fichier: Séries France (pop,ipc,pib,chom) | Source: INSEE Séries temporelles**

| N° Col | Nom de la colonne | Description | Disponibilité | Type | Taux NA | Gestion NA | Distribution | Remarques |
|---|---|---|---|---|---|---|---|---|
| Numéro | Nom technique | Description fonctionnelle | Oui/Non | int/float/object | % NA | Stratégie | Min/Max/Uniques | Notes |
| population_serie_france.csv (383 lignes) |  |  |  |  |  |  |  |  |
| 1 | TIME_PERIOD | Date YYYY-MM | Oui | object | 0% | Aucun | 1994-2025 | Mensuel |
| 2 | OBS_VALUE | Population (milliers) | Oui | int64 | 0% | Aucun | 59M à 68.7M | +16% |
| ipc_france.csv (431 lignes) |  |  |  |  |  |  |  |  |
| 1 | TIME_PERIOD | Date YYYY-MM | Oui | object | 0% | Aucun | 1990-2025 | Mensuel |
| 2 | OBS_VALUE | Indice prix base 2015 | Oui | float64 | 0% | Aucun | 66 à 122 | +84% |
| pib_france.csv (306 lignes) |  |  |  |  |  |  |  |  |
| 1 | TIME_PERIOD | Date YYYY-QX | Oui | object | 0% | Aucun | 1949-2025 | Trimestriel |
| 2 | OBS_VALUE | Évolution PIB (%) | Oui | float64 | 0.3% | 1 NA | -13.5% à +17.5% | Base 2020 |
| chomage_series.csv (350 lignes) |  |  |  |  |  |  |  |  |
| 1 | TIME_PERIOD | Date YYYY-QX | Oui | object | 0% | Aucun | 1982-2025 | Trimestriel |
| 2 | OBS_VALUE | Taux chômage (%) | Oui | float64 | 0% | Aucun | 5.3% à 10.7% | BIT |
| 3 | REF_AREA | Zone géo | Oui | object | 0% | Aucun | FM + IdF | 2 zones |
| chomage_regions.csv (2100 lignes) |  |  |  |  |  |  |  |  |
| 1 | TIME_PERIOD | Date YYYY-QX | Oui | object | 0% | Aucun | 1982-2024 | Trimestriel |
| 2 | OBS_VALUE | Taux chômage (%) | Oui | float64 | 0% | Aucun | 3.8% à 12.6% | 12 depts |
| 3 | REF_AREA | Code département | Oui | object | 0% | Aucun | D70 à D81 | 8 régions |
| 4 | REGION | Nom région | Oui | object | 0% | Aucun | 8 régions | Jointure |

---

