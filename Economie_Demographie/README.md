# Economie & Demographie

Donnees economiques et demographiques extraites de l'API INSEE pour le projet Compagnon Immobilier.

## Structure

```
Economie_Demographie/
├── Notebooks/
│   ├── 01_introduction_environnement.ipynb   # Setup et verification
│   ├── 02_extraction_donnees.ipynb           # Extraction API INSEE
│   ├── 03_nettoyage_donnees.ipynb            # Preprocessing
│   ├── 04_analyse_exploratoire.ipynb         # EDA
│   └── 05_dataviz_analyse.ipynb              # Visualisations
│
├── data/
│   ├── clean/                    # Donnees nettoyees (17 MB) - DANS GIT
│   │   ├── chomage_departements_clean.csv
│   │   ├── revenus_communes_2021_clean.csv
│   │   ├── pauvrete_communes_2021_clean.csv
│   │   └── ... (18 fichiers)
│   └── [brut]                    # Donnees brutes - NON VERSIONNE
│
├── Agregation_Donnees/
│   ├── 01_agregation_eco_demo_ML.ipynb
│   ├── features_eco_demo_COMMUNE.csv         # Dataset agrege communes
│   ├── features_eco_demo_DEPARTEMENT.csv     # Dataset agrege departements
│   └── DICTIONNAIRE_VARIABLES.md
│
├── DataViz_IMG/                  # Images des visualisations
├── requirements.txt
└── README.md
```

## Installation rapide

```bash
# Depuis la racine du projet
cd Economie_Demographie

# Creer environnement virtuel
python3 -m venv venv
source venv/bin/activate      # Linux/Mac
# .\venv\Scripts\activate     # Windows

# Installer dependances
pip install -r requirements.txt

# Installer kernel Jupyter
python -m ipykernel install --user --name=compagnon-immo --display-name="Python (Compagnon Immo)"

# Lancer Jupyter
jupyter notebook
```

## Donnees disponibles

### Fichiers clean (dans git)

| Fichier | Lignes | Description |
|---------|--------|-------------|
| `chomage_departements_clean.csv` | 16,988 | Taux chomage par dept (1982-2025) |
| `chomage_national_clean.csv` | 19,130 | Chomage national |
| `chomage_regions_clean.csv` | 2,100 | Chomage regional |
| `revenus_communes_2021_clean.csv` | 31,325 | Revenus par commune |
| `pauvrete_communes_2021_clean.csv` | 4,396 | Taux pauvrete par commune |
| `population_series_clean.csv` | 9,687 | Population par dept |
| `emploi_clean.csv` | 5,396 | Etablissements par dept |
| `entreprises_clean.csv` | 3,328 | Creations entreprises |
| `prix_logements_clean.csv` | 15,292 | Indices prix immobilier |
| `ipc_clean.csv` | 431 | Inflation (IPC) |
| `pib_clean.csv` | 20,435 | PIB France |
| ... | ... | ... |

### Fichiers agreges (prets pour ML)

| Fichier | Lignes | Cle | Description |
|---------|--------|-----|-------------|
| `features_eco_demo_COMMUNE.csv` | 31,325 | code_commune | Features par commune |
| `features_eco_demo_DEPARTEMENT.csv` | 97 | code_dept | Features par departement |

## Variables principales

### Commune

| Variable | Type | Description |
|----------|------|-------------|
| `code_commune` | str | Code INSEE (5 car.) |
| `revenu_median` | float | Revenu median (EUR/an) |
| `taux_pauvrete` | float | Taux pauvrete (%) |
| `pop_commune` | float | Population |

### Departement

| Variable | Type | Description |
|----------|------|-------------|
| `code_dept` | str | Code dept (2-3 car.) |
| `taux_chomage` | float | Taux chomage (%) |
| `nb_etablissements` | float | Nb etablissements |
| `nb_creations_entreprises` | float | Creations entreprises |
| `densite_etablissements` | float | Etabl. / 1000 hab |
| `dynamisme_entrepreneurial` | float | Creations / 1000 hab |

## Regenerer les donnees brutes (optionnel)

Si vous avez besoin des donnees brutes:

1. Creer un compte sur [api.insee.fr](https://api.insee.fr)
2. Configurer les credentials:
   ```python
   from pynsee import set_credentials
   set_credentials(consumer_key="VOTRE_CLE", consumer_secret="VOTRE_SECRET")
   ```
3. Executer `02_extraction_donnees.ipynb`
4. Executer `03_nettoyage_donnees.ipynb`

## Jointures avec autres sources

```python
# Avec DVF (Prix immobilier)
df_dvf.merge(df_eco_commune, on='code_commune', how='left')

# Avec Criminalite
df_crime['code_commune'] = df_crime['CODGEO_2025']
df_crime.merge(df_eco_commune, on='code_commune', how='left')

# Extraire dept depuis commune
df['code_dept'] = df['code_commune'].str[:2]  # ou [:3] pour DOM-TOM
```

## Valeurs manquantes

| Variable | % NaN | Raison |
|----------|-------|--------|
| `taux_pauvrete` | 86% | Secret statistique (petites communes) |
| Autres | < 1% | DOM-TOM |

**Recommandation:** Imputer `taux_pauvrete` par moyenne departementale.

## Dependances

```
pandas>=2.0.0
numpy>=1.24.0
matplotlib>=3.6.0
seaborn>=0.12.0
pynsee>=0.2.0
ipykernel>=6.0.0
openpyxl>=3.0.0
scipy>=1.10.0
scikit-learn>=1.3.0
```
