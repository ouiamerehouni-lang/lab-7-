# lab-7- : Gestion du cycle de vie des modèles avec MLflow

**Étape 1 : Initialisation de l’environnement et installation de MLflow**

On a commencé par l'initialisation de l'environnement avec Python 3.12 et l'installation de MLflow version 2.20.1

<img width="918" height="255" alt="image" src="https://github.com/user-attachments/assets/75eb741f-86d1-40f5-8798-9e54190e94b7" />

**Étape 2 : Création explicite de l’espace de stockage MLflow**

On a commencé par créer une structure de dossiers dédiée afin de préparer explicitement la séparation entre les métadonnées, qui concernent les mesures et paramètres stockés en base de données, et les artefacts, qui regroupent les fichiers physiques comme les modèles et les graphiques.

<img width="927" height="224" alt="image" src="https://github.com/user-attachments/assets/f67f2931-f2d4-4db4-b17f-ba1f808f7b8a" />


**Étape 3 : Configuration du client MLflow**

On a commencé par configurer l'URI du serveur de tracking via une variable d'environnement, ce qui permet de lier officiellement notre terminal au serveur MLflow pour que tous les futurs entraînements soient enregistrés au bon endroit.
<img width="625" height="51" alt="image" src="https://github.com/user-attachments/assets/66e48e64-7e8d-4193-949d-5a5eb15081c0" />
<img width="449" height="30" alt="image" src="https://github.com/user-attachments/assets/af7b64ff-d735-415d-8f9a-1afd75da5c86" />


**Étape 4 : Démarrage du serveur MLflow (tracking server)**
