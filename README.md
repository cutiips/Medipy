[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/cutiips/MedipyTest2.git/HEAD?labpath=https%3A%2F%2Fgithub.com%2Fcutiips%2FMedipyTest2%2Fblob%2Fmain%2Fnotebooks%2F1_TissueEngin.ipynb)
[![Launch Jupyter](https://img.shields.io/badge/launch-jupyter-blue?logo=jupyter)](https://notebooks.gesis.org/binder/jupyter/user/cutiips-medipy-qt5ij4ro/tree)
[![GitHub Pages](https://img.shields.io/badge/static-jupyter-blue?logo=jupyter)](https://cutiips.github.io/Medipy/)

Pour exécuter le notebook online, vous pouvez configurer Binder : https://notebooks.gesis.org/binder/ ; il suffit de rajouter le lien de repo actuel dans le premier champ (et être patient). Il faudra ensuite rajouter manuellement les variables d'environnement pour éviter tout problèmes. 

---

# 📊 Projet de Science des Données - Construction d'un Graphe de Connaissances avec le NLP

## 📝 Introduction

Le domaine biomédical est un excellent exemple où la représentation des données sous forme 
de graphe est particulièrement pertinente. En effet, il s'agit souvent d'analyser les interactions 
et relations entre gènes, maladies, médicaments, protéines, et bien plus encore. 

Par exemple, comme illustré dans la figure ci-dessous, l'acide ascorbique (également connu 
sous le nom de vitamine C) peut être relié à d'autres concepts biomédicaux, montrant que 
la vitamine C pourrait être utilisée pour traiter la gastrite chronique. Bien que l'on puisse 
s'appuyer sur une équipe d'experts pour cartographier toutes ces connexions, il est souvent 
coûteux et complexe d'avoir une telle équipe.

Dans ce projet, nous allons exploiter des techniques de **traitement du langage naturel (NLP)** 
pour extraire automatiquement ces relations à partir de recherches scientifiques. Bien que ces 
résultats ne soient pas toujours parfaits, cela permet de constituer un graphe de connaissances 
biomédicales sans une expertise médicale approfondie.

---

## 🎯 1.Objectifs initiaux

Le but de ce projet est de combiner différentes techniques pour construire un graphe de 
connaissances à partir d'articles de recherche biomédicale au format PDF. Pour ce faire, 
nous allons :

1.1. **Utiliser l'OCR (Reconnaissance Optique de Caractères)** : Extraire le texte des articles PDF.

1.2. **Appliquer des méthodes de "Named Entity Linking"** : Identifier et lier les entités biomédicales mentionnées dans les articles.

1.3. **Extraire les relations entre ces entités** : Grâce à des modèles NLP avancés.

1.4. **Enrichir les données avec des bases externes** : Pour rendre les relations plus complètes 
et fiables.

##  🎯 2.Objectifs en plus
Essayez d'enrichir votre graphique de connaissances :

2.1. Ajoutez un nouvel article à votre graphe de connaissances. En utilisant la bibliothèque PubMed, recherchez et sélectionnez un article qui pourrait être lié à celui de
Mohammadreza Ahmadi. En suivant l'exemple de ce qui a été fait jusqu'à présent, importez les phrases et les entités de ce nouvel article dans votre graphe de connaissances.
les phrases et les entités de ce nouvel article dans votre graphe de connaissances.

2.2. Essayez d'enrichir davantage votre graphe de connaissances en utilisant la SNOMED-CT et Wikidata.

2.3. Rédigez un rapport documentant tout le travail mentionné ci-dessus, essayez de conclure en
fournir quelques cas d'utilisation dans lesquels votre graphe pourrait être utile

### 🔍 Démarche
- Chaque article sera segmenté en phrases.
- Nous utiliserons le NLP pour identifier les entités médicales et les relations entre elles.
- Contrairement à une approche classique où les relations sont directement représentées 
comme des liens, ici, nous représenterons chaque **relation sous forme de nœud intermédiaire**. Cela permettra de 
conserver une traçabilité claire des informations extraites et de valider leur exactitude.

---

# 🚀 Setup

## 🐍 Environnement virtuel
- Télécharger et installer [Anaconda](https://www.anaconda.com/products/distribution).
- Créer l'environnement virtuel : `conda env create --file environment.yml --name Medipy python=3.7`
- Activer l'environnement virtuel : `conda activate Medipy`.
- Se rendre dans le répertoire du projet : `cd path/to/semesterproject`.
- Pour lancer Jupyter Notebook : `jupyter notebook`.
- Pour désactiver l'environnement virtuel : `conda deactivate`.

### PyCharm
- Ouvrir PyCharm et sélectionner l'environnement virtuel `Medipy` : ![PyCharm](/setup/pycharm.png)

## 💊 problèmes dépendances - manuellement :
- Créer un environnement virtuel avec Python 3.7 : `conda create --name Medipy python=3.7` (sans le .yml)
- Installer les dépendances `conda-forge` : `conda install -c conda-forge tesseract poppler`
- Installer les dépendances `anaconda` : `conda install -c anaconda nltk pandas`.
- You can find all the anaconda dependencies in the `anaconda.txt` file.
- Installer les dépendances `pip` : `pip install -r requirements.txt`.
- Créer un fichier data, contenant un dossier PDF1 et PDF2 vierge, à la racine du projet
- Créer un fichier .env à la racine du projet et structuré comme ceci : 
```
HOST_PROD=YOUR_HOST_NEO4J_AURA
USER_PROD=YOUT_USER_NEO4J_AURA
PASSWORD_PROD=YOUR_PASSWORD_NEO4J_AURA

HOST_DEV=YOUR_HOST_BLANK_SANDBOX
USER_DEV=YOUR_USER_BLANK_SANDBOX
PASSWORD_DEV=YOUT_PASSWORD_BLANK_SANDBOX

API_KEY_BIOPORTAL=YOUR_API_KEY

PDF1_PATH_NLTK_DATA=YOUR_PATH\Medipy\data\PDF1
PDF2_PATH_NLTK_DATA=YOUR_PATH\Medipy\data\PDF2
```
