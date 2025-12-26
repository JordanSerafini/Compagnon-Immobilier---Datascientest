# Compagnon Immobilier

Projet fil rouge DataScientest - Solution d'aide a la decision pour les acheteurs immobiliers.

## Objectifs du projet

1. **Prediction de l'evolution des prix** selon les territoires
2. **Estimation du prix au m2** d'un logement donne
3. **Data Visualization** pour comparer les territoires (prix, demographie, securite, economie)

## Structure du projet

```
Compagnon Immobilier - Datascientest/
├── Economie_Demographie/
│   ├── Notebooks/              # Notebooks Jupyter (extraction, nettoyage, analyse)
│   ├── data/
│   │   ├── clean/              # 18 fichiers CSV nettoyes
│   │   └── ...                 # Donnees brutes INSEE
│   ├── requirements.txt
│   └── venv/                   # Environnement virtuel (non versionne)
│
├── Education_Securite/
│   ├── Educ_Secu.ipynb         # Notebook exploration
│   └── *.parquet               # Donnees criminalite (4.7M lignes)
│
├── Prix immobilier/
│   └── Data/
│       ├── DVF_20XX.gz         # Transactions immobilieres 2020-2025 (20M lignes)
│       ├── ech_annonces_ventes_68.csv
│       └── ech_annonces_locations_68.csv
│
├── Aggregation/
│   └── AUDIT_DONNEES.md        # Audit complet des sources et schema d'agregation
│
└── README.md
```

## Installation rapide

### Option 1: Script automatique (recommande)

```bash
# Cloner le repo
git clone <url-du-repo>
cd "Compagnon Immobilier - Datascientest"

# Setup automatique
cd Economie_Demographie
python3 -m venv venv
source venv/bin/activate      # Linux/Mac
# .\venv\Scripts\activate     # Windows

pip install -r requirements.txt
python -m ipykernel install --user --name=compagnon-immo --display-name="Python (Compagnon Immo)"
```

### Option 2: Installation manuelle

1. **Creer l'environnement virtuel**
   ```bash
   cd Economie_Demographie
   python3 -m venv venv
   ```

2. **Activer l'environnement**
   ```bash
   # Linux/Mac
   source venv/bin/activate

   # Windows PowerShell
   .\venv\Scripts\Activate.ps1

   # Windows CMD
   .\venv\Scripts\activate.bat
   ```

3. **Installer les dependances**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configurer le kernel Jupyter**
   ```bash
   python -m ipykernel install --user --name=compagnon-immo --display-name="Python (Compagnon Immo)"
   ```

5. **Lancer Jupyter**
   ```bash
   jupyter notebook
   ```

   Ouvrir les notebooks et selectionner le kernel **"Python (Compagnon Immo)"**.

## Notebooks disponibles

### Economie_Demographie/Notebooks/

| Notebook | Description |
|----------|-------------|
| `01_introduction_environnement.ipynb` | Configuration et verification de l'environnement |
| `02_extraction_donnees.ipynb` | Extraction des donnees via l'API INSEE (pynsee) |
| `03_nettoyage_donnees.ipynb` | Nettoyage et preprocessing des donnees |
| `04_analyse_exploratoire.ipynb` | Analyse exploratoire des donnees |
| `05_dataviz_analyse.ipynb` | Visualisations et analyses statistiques |

### Education_Securite/

| Notebook | Description |
|----------|-------------|
| `Educ_Secu.ipynb` | Exploration des donnees criminalite et education |

## Sources de donnees

| Source | Volume | Periode | Description |
|--------|--------|---------|-------------|
| INSEE (pynsee) | 18 fichiers | 1975-2025 | Chomage, population, revenus, emploi |
| Criminalite | 4.7M lignes | 2016-2024 | 15 indicateurs par commune |
| DVF | 20M transactions | 2020-2025 | Prix immobiliers geolocalisees |
| Annonces (68) | 39K annonces | 2019-2023 | Ventes/locations avec DPE |

Voir `Aggregation/AUDIT_DONNEES.md` pour le detail complet.

## Dependances principales

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

## Configuration API INSEE (optionnel)

Pour utiliser l'API INSEE, creer un compte sur [api.insee.fr](https://api.insee.fr) et configurer les credentials:

```python
from pynsee import set_credentials
set_credentials(consumer_key="VOTRE_CLE", consumer_secret="VOTRE_SECRET")
```

Ou via variables d'environnement:
```bash
export INSEE_CONSUMER_KEY="VOTRE_CLE"
export INSEE_CONSUMER_SECRET="VOTRE_SECRET"
```

## Troubleshooting

### Le kernel Jupyter ne fonctionne pas

```bash
# Verifier les kernels installes
jupyter kernelspec list

# Reinstaller le kernel
source Economie_Demographie/venv/bin/activate
python -m ipykernel install --user --name=compagnon-immo --display-name="Python (Compagnon Immo)" --force
```

### Erreur d'import pandas/numpy

```bash
# Verifier que le venv est active
which python  # Doit pointer vers venv/bin/python

# Reinstaller les dependances
pip install -r requirements.txt --force-reinstall
```

### Fichiers DVF trop volumineux

Les fichiers DVF sont compresses (.gz). Pour les lire:
```python
import pandas as pd
import gzip

with gzip.open('Prix immobilier/Data/DVF_2021.gz', 'rt') as f:
    df = pd.read_csv(f)
```

## Auteurs

Projet realise dans le cadre de la formation DataScientest.

## Licence

Donnees sous licence ouverte - Etalab
