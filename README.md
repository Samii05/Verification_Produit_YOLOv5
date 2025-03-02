Verification de Produit en Milieu Industriel avec YOLOv5



Description du Projet

Ce projet vise à automatiser la vérification des bouteilles en milieu industriel à l'aide de YOLOv5. Il permet d'identifier six classes de défauts ou caractéristiques des bouteilles :

Cap : Bouchon présent

Defective-Label : Etiquette défectueuse

Good-Label : Bonne étiquette

No-Cap : Absence de bouchon

No-Label : Absence d'étiquette

Bottle : Bouteille détectée

Le modèle a été entraîné sur un dataset disponible sur Roboflow : Lien vers le dataset.

Fonctionnalités Principales

Entraînement et Fine-Tuning YOLOv5 : Entraînement du modèle avec ajout de nouvelles images pour améliorer la précision.

Interface Web (Gradio) : Permet d'effectuer des détections directement via un navigateur.

Interface Desktop (Tkinter) : Application locale permettant une détection en temps réel via webcam.

Importation d'Images : Depuis le PC, via la caméra ou le presse-papiers.

Réglage du Score de Confiance : Ajustement pour affiner la détection.

Affichage des Résultats : Visualisation des détections avec mise en évidence des anomalies.

Enregistrement des Analyses : Sauvegarde des résultats pour suivi et exploitation.

Organisation du Projet

📂 Verification_Produit_YOLOv5/
│── 📁 dataset/            # Contient les images et annotations du dataset
│── 📁 models/             # Contient les meilleurs modèles entrainés (best.pt)
│── 📁 notebooks/          # Codes du projet
│── 📁 diagrams/           # résultat d'évaluation de projet
│── 📄 README.md           # Documentation du projet


Déroulement de l'Entraînement et Fine-Tuning

Premier Entraînement : Entrainement initial avec le dataset de Roboflow.

Analyse des Erreurs : Certains objets n'étaient pas bien détectés (bouchons plats, étiquettes longues, bouteilles larges).

Ajout de Nouvelles Images : Collecte et annotation d'images supplémentaires via MakeSense.ai.

Premier Fine-Tuning : Amélioration des performances avec le nouveau dataset enrichi.

Deuxième Fine-Tuning : Ajout de nouvelles données pour un dernier ajustement.

Evaluation Finale : Analyse de la matrice de confusion et de la courbe PR pour évaluer les performances.

Liens Utiles

Notebook Colab d'Entraînement : Lien

Notebook Colab de l'Interface Web (Gradio) : Lien

Notebook Jupyter de l'Interface Desktop (Tkinter) : Lien

"""" veuillez les trouver dans le dossier notebooks et les télécharger """



Utilisation

Utilisation de l'interface

Ce projet propose une interface permettant d'exécuter un modèle YOLOv5 (best.pt) avec Tkinter (localement) et  (en ligne).
Suivez les étapes ci-dessous pour exécuter l'interface selon votre environnement.



🖥️ 1. Exécution locale avec Tkinter

📌 Prérequis :

créer un notebook jupyter 

Bibliothèques requises : torch, tkinter, PIL

Modèle best.pt placé dans le même dossier que le script

🚀 Étapes :

Placer best.pt dans le dossier du notebook/script

📂 projet/
├── interface_tkinter.ipynb  # Script de l'interface
├── best.pt  # Modèle YOLO

Exécuter le script


🛠️ Code de chargement du modèle

Dans le script interface_tkinter.ipynb, assurez-vous que le chemin du modèle est correct :

import torch

model_path = "best.pt"  # Le fichier doit être dans le même dossier
model = torch.hub.load('ultralytics/yolov5', 'custom', path=model_path, force_reload=True)





☁️ 2. Exécution sur Google Colab

📌 Prérequis :

Avoir un compte Google Drive

Importer best.pt dans un dossier de Drive

🚀 Étapes :

Placer best.pt dans un dossier Drive, par exemple :

📂 Mon Drive/
├── YOLO/
    ├── best.pt  # Modèle YOLO

Monter Google Drive dans Colab
Dans une cellule de notebook Colab, exécutez :

from google.colab import drive
drive.mount('/content/drive')

Spécifier le chemin du modèle best.pt

model_path = "/content/drive/My Drive/YOLO/best.pt"
model = torch.hub.load('ultralytics/yolov5', 'custom', path=model_path, force_reload=True)

Exécuter le notebook normalement et interagir avec l'interface.




✅ Vous êtes maintenant prêt à exécuter l'interface avec votre modèle YOLOv5 ! 🚀

Conclusion

Ce projet apporte une solution efficace pour l'inspection des bouteilles avant leur mise en circulation. Grâce aux interfaces intuitives, il est accessible aussi bien sur le web qu'en local.


✨ Auteur

Sami Ramzi Rezig