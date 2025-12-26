# Compagnon Immobilier

Projet fil rouge DataScientest - Solution d'aide à la décision pour les acheteurs immobiliers.

## Structure du projet

```
Compagnon Immobilier - Datascientest/
├── Economie_Demographie/
│   ├── Notebooks/           # Notebooks Jupyter
│   ├── data/                # Données brutes et nettoyées
│   ├── requirements.txt     # Dépendances Python
│   └── venv/                # Environnement virtuel Python (local, non versionné)
├── Prix immobilier/         # Partie prix immobilier
└── README.md
```

## Installation

### 1. Cloner le repository

```bash
git clone <url-du-repo>
cd "Compagnon Immobilier - Datascientest"
```

### 2. Créer l'environnement virtuel

```bash
cd Economie_Demographie
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 3. Configurer le kernel Jupyter

Installer le kernel avec votre chemin local :

```bash
# Activer le venv
source venv/bin/activate

# Installer le kernel (remplacer <VOTRE_CHEMIN> par votre chemin absolu)
python -m ipykernel install --user --name=compagnon-immo --display-name="Python (Compagnon Immo)"
```

**OU** modifier manuellement le fichier kernel :

1. Trouver le fichier de configuration :
   ```bash
   # Linux/Mac
   ~/.local/share/jupyter/kernels/compagnon-immo/kernel.json

   # Windows
   %APPDATA%\jupyter\kernels\compagnon-immo\kernel.json
   ```

2. Modifier le chemin Python :
   ```json
   {
     "argv": [
       "/VOTRE/CHEMIN/ABSOLU/Compagnon Immobilier - Datascientest/Economie_Demographie/venv/bin/python",
       "-Xfrozen_modules=off",
       "-m",
       "ipykernel_launcher",
       "-f",
       "{connection_file}"
     ],
     "display_name": "Python (Compagnon Immo)",
     "language": "python"
   }
   ```

### 4. Lancer Jupyter

```bash
jupyter notebook
```

Ouvrir les notebooks dans `Economie_Demographie/Notebooks/` et sélectionner le kernel **"Python (Compagnon Immo)"**.

## Notebooks disponibles

| Notebook | Description |
|----------|-------------|
| 01_introduction_environnement.ipynb | Configuration et vérification de l'environnement |
| 02_extraction_donnees.ipynb | Extraction des données via l'API INSEE |
| 03_nettoyage_donnees.ipynb | Nettoyage et preprocessing des données |

## Dépendances

- Python 3.10+
- pandas
- numpy
- matplotlib
- seaborn
- pynsee (API INSEE)
- ipykernel

## Auteurs

Projet réalisé dans le cadre de la formation DataScientest.
