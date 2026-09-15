# Année 2026-2027 - M2IA/M2DS - UE Data Mining - Projet
## Règles de formatage :

TODO

## Carte des fichiers
ecology

<img width="976" height="511" alt="image" src="https://github.com/user-attachments/assets/68c1a212-f2d7-41ba-980c-611e65fc7274" />

<img width="938" height="216" alt="image" src="https://github.com/user-attachments/assets/23f0c797-bc81-4494-806d-954d6e5a66cc" />


                            +-------------------------------------------+
                            |             monitoring_sites              |
                            |-------------------------------------------|
                            | - site_code (PK)                          |
                            | - site_name, region, habitat_category     |
                            | - latitude, longitude, elevation_m        |
                            +-------------------------------------------+
                                  |
                                  | 1
                                  +--------------------+---------------------+--------------------+
                                  | *                  | *                   | *                  | *
    +-----------------------------v----+    +----------v----------+    +-----v--------------+    +v------------------------+
    |           bat_surveys            |    |   orchard_surveys   |    |environmental_month |    |monitoring_device_operat.|
    |----------------------------------|    |---------------------|    |--------------------|    |-------------------------|
    | - survey_id (PK)                 |    | - orchard_survey_id |    | - site_code (FK)   |    | - device_operation_id   |
    | - site_code (FK)                 |    | - site_code (FK)    |    | - reporting_month  |    | - site_code (FK)        |
    | - colony_estimate, visit_count   |    | - fruit_set_rate_pct|    | - mean_temp, rain  |    | - device_reference      |
    | - observed_bat_count             |    | - durian_yield_kg   |    | - pesticide_index  |    | - uptime_pct, fault_code|
    +----------------------------------+    +---------------------+    +--------------------+    +-------------------------+
                    ^                                                                                         ^
                    | (related_survey_id)                                           (related_device_reference)|
                    +-----------------------------+-----------------------------------------------------------+
                                                  |
                                   +--------------v---------------------+
                                   |    environmental_field_reports     |
                                   |------------------------------------|
                                   | - document_id (PK)                 |
                                   | - site_code (FK)                   |
                                   | - reporting_period, title, text    |
                                   +------------------------------------+




<img width="960" height="411" alt="image" src="https://github.com/user-attachments/assets/b574b4a4-ba21-4c37-b144-d1f1847022e5" />

<img width="975" height="304" alt="image" src="https://github.com/user-attachments/assets/fe64947b-1a90-4309-bac7-27fc3ea96368" />

                                 

<img width="949" height="394" alt="image" src="https://github.com/user-attachments/assets/85dc2408-9e64-433d-8fef-8174a27d6013" />

<img width="1023" height="273" alt="image" src="https://github.com/user-attachments/assets/5d4835e7-294a-45a4-a841-6a5a8345be47" />

pour public records
<img width="957" height="387" alt="image" src="https://github.com/user-attachments/assets/987df92b-6939-4f2f-aa59-60c3b40b6181" />


<img width="935" height="444" alt="image" src="https://github.com/user-attachments/assets/a898eb2f-7c12-4c64-8942-d71df9920d8d" />



Sur ce repository, vous pourrez trouver l’ensemble des éléments
nécessaire au projet de groupe de l’UE Data Mining pour l’année 2026-2027.

Votre objectif est de mettre en évidence le narratif caché à l’intérieur
de ces données à l’aide des notions et méthodes vues au fur et
à mesure de l’UE Data Mining.

/!\ Ce narratif est entièrement fictif. Il a été créé dans un objectif pédagogique et ne reflète aucunement la réalité /!\

Pour ce faire, vous travaillerez en groupe en débattant et
en vous répartissant les tâches à faire.

Le rendu attendu est un rapport, sous la forme d’un notebook jupyter,
qui détaillera vos réflexions, les méthodes et vos conclusions.

Pour cela, le fichier `Base_notebook_to_complete.ipynb` est mis à votre disposition (vous pouvez changer le nom si vous le souhaitez).

Pensez à bien y préciser:

* Le nom de votre groupe
* La liste des membres

Vous serez avant tout évalué sur votre méthode, donc soyez précis, détaillé
et rigoureux dans vos descriptions.

/!\ L’usage de l’IA Générative est fortement déconseillé (ce sont vos cerveaux que l’on souhaite entrainer ici).
Si vous souhaitez tout de même l’utiliser, cela doit être justifié et documenté dans votre rapport /!\

## Jeux de données

Dans le dossier `data/`, vous trouverez les ensembles des jeux de données suivants:

- `data/public_records/` — jeux de données issus d’institutions administratives publiques,
- `data/health/` — jeux de données médicales issus de cliniques et d’hôpitaux,
- `data/ecology/` — jeux de données issus de recherches environnementales,
- `data/logistics/` — jeux de données issus de groupes et d’entreprises privées.

Le fichier `data/data_dictionary.csv` détaille les caractéristiques des variables présentes dans chaque jeu de données.

/!\ Ces jeux de données sont entièrement synthétiques et ont été créé dans un but pédogagique.
Ils ne représentent pas des informations factuelles à propos de personnes réelles,
d’organisations réelles, de gouvernnements réels ou localisations réelles.
Toute ressemblance avec des personnes réelles, physiques ou morales, est totalement involontaire et fortuite. /!\ 
 
## Pour bien commencer

1. Faites un `fork` de ce repository vers un noveau repository pour votre groupe.
2. Clonez le repository de votre groupe sur votre machine.
3. (Installez conda si ce n’est pas déjà fait)
4. Installez les dépendances avec la commande: `conda create --name <envname> --file requirements.txt`
5. Lancez le notebook avec la commande: `jupyter notebook nom-du-notebook.ipynb`
6. Travaillez en groupe et complétez le notebook

## Rendu

Le rendu pourra se faire via:

* une `pull-request`, 
* en m’envoyant une archive .zip contenant votre travail à `antoine.richard@chu-lyon.fr`.
