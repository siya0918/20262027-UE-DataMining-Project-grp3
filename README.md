# UE Data Mining – Projet 2026-2027 – Groupe 3

**Membres :** Siyaman MOHAMAD, Yannis BORDJI, Ilicia BENAOUDIA, Cédric AUDIE, Mohamed Ali DAMERGI, Yann AMER, Kenza ABOU-EL KASEM

**Objectif :** retrouver le narratif caché dans les données du projet (santé, écologie, registres publics, logistique) avec les méthodes de data mining vues en cours.

---

## 1. Contenu du dépôt

- [`01_health_nettoyage.ipynb`](01_health_nettoyage.ipynb) / [`01_health_analyse.ipynb`](01_health_analyse.ipynb) : données de santé
- [`02_ecology_nettoyage.ipynb`](02_ecology_nettoyage.ipynb) / [`02_ecology_analyse.ipynb`](02_ecology_analyse.ipynb) : données écologiques
- [`03_public_records_nettoyage.ipynb`](03_public_records_nettoyage.ipynb) / [`03_public_records_analyse.ipynb`](03_public_records_analyse.ipynb) : registres publics
- [`04_logistics_nettoyage.ipynb`](04_logistics_nettoyage.ipynb) / [`04_logistics_analyse.ipynb`](04_logistics_analyse.ipynb) : logistique
- [`05_croisements.ipynb`](05_croisements.ipynb) : liens entre les quatre domaines
- [`06_rapport_final.ipynb`](06_rapport_final.ipynb) : synthèse (méthode, résultats, narratif, limites, usage de l'IA)
- [`pistes.md`](pistes.md) : notre carnet d'enquête (pistes suivies, questions, hypothèses)
- `data/` : données brutes fournies (ne pas modifier)
- `data_clean/` : données nettoyées, créées par les notebooks de nettoyage
- `resultats/` : fichiers produits par les analyses (`patients_reperes.csv`)
- [`requirements-pip.txt`](requirements-pip.txt) : bibliothèques nécessaires pour faire tourner les notebooks
- `requirements.txt` : environnement conda fourni avec le sujet (Python et Jupyter seulement)

## 2. Organisation des données

| Domaine | Fichiers principaux | Ce qu'on y trouve |
|---|---|---|
| Santé | patients, consultations, observations, actes, notes, enregistrements cardiaques | 240 patients suivis dans plusieurs établissements |
| Écologie | sites, relevés de chauves-souris, vergers, météo, rapports de terrain, appareils de suivi | suivi des chauves-souris et des vergers (durians) |
| Registres publics | sociétés, dirigeants, nominations, licences, documents, mémos, visites des sites | qui dirige quoi, depuis quand, qui entre où |
| Logistique | partenaires, sites, commandes, envois, réceptions, stocks | ce qui circule entre les organismes |

Liens entre domaines :
- santé ↔ logistique : par l'établissement (site) et la date
- écologie ↔ registres publics / logistique : par l'organisme qui visite les grottes
- santé ↔ registres publics : par les noms et dates de naissance (rapprochement approché, pas d'identifiant commun)

Le dictionnaire des colonnes est dans [`data/data_dictionary.csv`](data/data_dictionary.csv).

## 3. Ce qu'on a trouvé
Le cheminement de l'enquête (pistes suivies, questions posées, hypothèses, pistes sans résultat) est dans [`pistes.md`](pistes.md), voici ce qu'on a trouvé brièvement.

- **Santé :** 11 patients ont un corps qui ne ressemble pas à celui d'un humain (deux cœurs, yeux indépendants), et quelques dirigeants reçoivent régulièrement un traitement, le `MRP-42`, et paraissent plus jeunes que leur âge.
- **Écologie :** les chauves-souris disparaissent dans certaines grottes, sans cause naturelle.
- **Registres publics :** l'organisme Horizon entre dans ces grottes la nuit ; des dirigeants restent en poste anormalement longtemps et changent d'identité.
- **Logistique :** Horizon envoie des échantillons biologiques à Meridian Biologistics, qui livre ensuite les établissements où les dirigeants reçoivent le `MRP-42`.
- **Croisements :** les chauves-souris baissent après chaque visite d'Horizon, et plusieurs patients atypiques se retrouvent sous un nom proche dans les registres publics.

**Narratif :** Horizon prélève des chauves-souris dans les grottes, et Meridian en tire un traitement (`MRP-42`) donné à des dirigeants qui vieillissent moins vite. Les patients atypiques vivent sous des identités successives depuis le XIXe siècle. Des documents internes les décrivent comme des êtres non humains proches du caméléon (« Chamaeleonidian », « Unwabu » = caméléon en zoulou). Les détails, les chiffres et les limites sont dans [`06_rapport_final.ipynb`](06_rapport_final.ipynb). 

## 4. Ordre d'exécution

Les notebooks doivent être lancés dans cet ordre, car chacun utilise ce que le précédent a produit :

1. Les quatre nettoyages : [`01_health_nettoyage`](01_health_nettoyage.ipynb), [`02_ecology_nettoyage`](02_ecology_nettoyage.ipynb), [`03_public_records_nettoyage`](03_public_records_nettoyage.ipynb), [`04_logistics_nettoyage`](04_logistics_nettoyage.ipynb)
   → ils créent `data_clean/`, utilisé par toutes les analyses.
2. [`01_health_analyse`](01_health_analyse.ipynb)
   → crée `resultats/patients_reperes.csv` (patients atypiques et patients ayant reçu plusieurs MRP-42), réutilisé ensuite.
3. [`02_ecology_analyse`](02_ecology_analyse.ipynb), [`03_public_records_analyse`](03_public_records_analyse.ipynb), [`04_logistics_analyse`](04_logistics_analyse.ipynb)
4. [`05_croisements`](05_croisements.ipynb) : a besoin des données nettoyées des quatre domaines et de `resultats/`.
5. [`06_rapport_final`](06_rapport_final.ipynb) : synthèse, à lire en dernier.

Pour chaque notebook : « Restart & Run All ».

## 5. Installation

**Prérequis :** Python 3.11 ou plus récent (`python --version` pour vérifier).

Les bibliothèques utilisées par les notebooks sont listées dans [`requirements-pip.txt`](requirements-pip.txt) : pandas, numpy, matplotlib, seaborn, scipy, scikit-learn, networkx, pyarrow et Jupyter. Le fichier `requirements.txt` fourni avec le sujet ne contient que Python et Jupyter : il ne suffit pas pour lancer nos notebooks.

Toutes les commandes se lancent depuis le dossier du dépôt.

**1. Créer un environnement virtuel**

Windows (PowerShell) :
```powershell
python -m venv .venv
.venv\Scripts\activate
```

Linux / macOS :
```bash
python3 -m venv .venv
source .venv/bin/activate
```

Le nom `(.venv)` doit apparaître au début de la ligne.

**2. Installer les bibliothèques**
```bash
pip install -r requirements-pip.txt
```

Vérification :
```bash
python -c "import pandas, numpy, sklearn, scipy, seaborn, networkx, pyarrow; print('tout est installé')"
```

**3. Ouvrir les notebooks**
```bash
python -m jupyter lab
```
Puis ouvrir les notebooks dans l'ordre de la partie 4 et faire « Restart Kernel and Run All Cells » sur chacun.

**Variante conda :** `conda create --name dm3 python=3.12`, `conda activate dm3`, puis `pip install -r requirements-pip.txt`.


**Tester tout le projet d'un coup (optionnel)**

Cette commande exécute les 10 notebooks dans l'ordre et affiche `OK` ou `ERREUR` pour chacun. Les copies exécutées sont écrites dans `test_execution/`, les notebooks d'origine ne sont pas modifiés.

Windows (PowerShell) :
```powershell
$notebooks = "01_health_nettoyage","02_ecology_nettoyage","03_public_records_nettoyage","04_logistics_nettoyage","01_health_analyse","02_ecology_analyse","03_public_records_analyse","04_logistics_analyse","05_croisements","06_rapport_final"
foreach ($nb in $notebooks) {
    python -m nbconvert --to notebook --execute --ExecutePreprocessor.timeout=600 --output-dir test_execution "$nb.ipynb" 2>&1 | Select-String "Error" | Select-Object -Last 1
    if ($LASTEXITCODE -eq 0) { Write-Host "OK    $nb" } else { Write-Host "ERREUR $nb" }
}
```

Linux / macOS :
```bash
for nb in 01_health_nettoyage 02_ecology_nettoyage 03_public_records_nettoyage 04_logistics_nettoyage 01_health_analyse 02_ecology_analyse 03_public_records_analyse 04_logistics_analyse 05_croisements 06_rapport_final; do
  python -m nbconvert --to notebook --execute --ExecutePreprocessor.timeout=600 --output-dir test_execution "$nb.ipynb" > /dev/null 2>&1 && echo "OK     $nb" || echo "ERREUR $nb"
done
```

Nous avons fait ce test dans un environnement neuf (Windows, PowerShell, venv) : les 10 notebooks affichent `OK`.

## 6. Usage de l'IA

Notre usage de l'IA générative est décrit dans [`06_rapport_final.ipynb`](06_rapport_final.ipynb), partie 6.
