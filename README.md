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

On démarre un serveur MLflow local avec SQLite et un artifact store dédié.

<img width="914" height="289" alt="image" src="https://github.com/user-attachments/assets/e1087102-4058-4376-900a-93660c782a7e" />
<img width="1862" height="404" alt="image" src="https://github.com/user-attachments/assets/dc0cfd00-2c80-4b67-9a3f-745aadbde015" />


**Étape 5 : Instrumentation réelle de train.py**

On a commencé par injecter les capacités de tracking et de versioning de MLflow directement dans le script d'entraînement, transformant un processus manuel en une chaîne MLOps automatisée.

<img width="1667" height="843" alt="image" src="https://github.com/user-attachments/assets/7a0a9a65-41c6-47e4-9316-c1d1179514fc" />



**Étape 6 : Observation du registry MLflow**

On a transformé le fichier technique (.joblib) en un artefact structuré au sein de MLflow, lui donnant ainsi un statut d'actif officiel grâce à son immuabilité et sa traçabilité complète.
<img width="1585" height="231" alt="image" src="https://github.com/user-attachments/assets/5eed07f9-9f5a-4a06-a996-6b8cd3d0a1b6" />
<img width="1635" height="190" alt="image" src="https://github.com/user-attachments/assets/b2319c7e-7d40-4aa8-8e9b-f830c3a67756" />


**Étape 7 : Promotion d’un modèle (activation)**

En créant l'alias production, on crée un "nom stable" qui pointe vers la meilleure version : cela permet de mettre à jour le modèle en un clic sans jamais avoir à modifier le code des applications qui l'utilisent.

<img width="1282" height="72" alt="image" src="https://github.com/user-attachments/assets/bfce5a0f-df9a-41d9-b514-0cb3cbf4ebb4" />

**Étape 8 : Rollback via MLflow Model Registry**

On a  remplacé les anciens fichiers texte par le Model Registry de MLflow comme unique source de vérité, permettant de gérer les versions du modèle de manière professionnelle. Cette étape a consisté à :
Abandonner les fichiers locaux pour utiliser un système centralisé et automatisé.
Créer une commande de "sécurité" capable de revenir instantanément à une version stable si la nouvelle pose problème.
Utiliser l'alias "production" comme un curseur mobile que l'on déplace entre les versions (v1, v2) sans jamais modifier le code de l'application.

<img width="1659" height="235" alt="image" src="https://github.com/user-attachments/assets/4ff5164c-ebdf-4ffa-93ad-f23811b42fe0" />


**Étape 9 : API : chargement du modèle actif**
On a connecté l’API au Model Registry de MLflow pour que le chargement du modèle ne dépende plus de fichiers locaux mais de l'alias @production

<img width="1640" height="385" alt="image" src="https://github.com/user-attachments/assets/7087d9a6-1274-40e1-916f-2707faa1d18d" />
