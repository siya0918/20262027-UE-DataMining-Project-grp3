# Année 2026-2027 - M2IA/M2DS - UE Data Mining - Projet
## Règles de formatage :

TODO

## Carte des fichiers

pour public records
<img width="957" height="387" alt="image" src="https://github.com/user-attachments/assets/987df92b-6939-4f2f-aa59-60c3b40b6181" />


<img width="935" height="444" alt="image" src="https://github.com/user-attachments/assets/a898eb2f-7c12-4c64-8942-d71df9920d8d" />


                                  +---------------------------------------+
                                  |         public_appointments           |
                                  |---------------------------------------|
                                  | - appointment_record_id (PK)          |
                                  | - office_holder_name                  |
                                  | - institution_name                    |
                                  | - official_region                     |
                                  +---------------------------------------+

 +-----------------------------------+            +------------------------------------+
 |        registered_entities        | 1        * |          officer_filings           |
 |-----------------------------------|------------|------------------------------------|
 | - registration_number (PK)        |            | - filing_id (PK)                   |
 | - legal_name                      |            | - registration_number (FK)         |
 | - parent_registration_number      |            | - full_name                        |
 | - registered_entity_type          |            | - role_title                       |
 +-----------------------------------+            +------------------------------------+
       | 1                                
       |                                  
       | *                                
 +-----------------------------------+            +------------------------------------+
 |        licensed_facilities        | 1        * |       licensed_professionals       |
 |-----------------------------------|------------|------------------------------------|
 | - facility_license_number (PK)    |            | - license_number (PK)              |
 | - operating_organization_reg (FK) |            | - primary_facility_license (FK)    |
 | - facility_name                   |            | - professional_name, specialty     |
 | - latitude, longitude             |            +------------------------------------+
 +-----------------------------------+
       | 
       | (related_site_code / site_code)
       +------------------------------------+
       |                                    |
       v                                    v
 +-----------------------------------+    +------------------------------------+
 |       regulatory_case_events      |    |      site_access_case_events       |
 |-----------------------------------|    |------------------------------------|
 | - regulatory_event_id (PK)        |    | - access_event_id (PK)             |
 | - case_number                     |    | - access_case_number               |
 | - subject_registration_number (FK)|    | - requesting_registration_num (FK) |
 | - related_site_code               |    | - site_code                        |
 | - related_shipment_number         |    | - event_time, activity, outcome    |
 | - event_time, activity, outcome   |    +------------------------------------+
 +-----------------------------------+                      |
       ^                                                    |
       | (related_case_number)                              |
       +----------------------------+-----------------------+
                                    |
 +----------------------------------v+            +------------------------------------+
 |        institutional_memos        |            | public_and_investigative_documents |
 |-----------------------------------|            |------------------------------------|
 | - document_id (PK)                |            | - document_id (PK)                 |
 | - related_case_number (FK)        |            | - collection                       |
 | - related_purchase_order (FK)     |            | - document_type, title             |
 | - related_shipment_number (FK)    |            | - author_name, author_organization |
 | - document_type, author_name      |            | - text, public_or_restricted       |
 +-----------------------------------+            +------------------------------------+

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
