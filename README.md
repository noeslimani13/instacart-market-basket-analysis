# 🛒 Projet T-DAT-600 - Instacart Market Basket Analysis (Joja)

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
## 📖 Présentation du Projet

Ce projet s'inscrit dans le cadre du module **T-DAT-600 (Joja)** d'Epitech. L'objectif principal est de réaliser une **Analyse Exploratoire des Données (EDA)** approfondie sur l'historique de commandes d'Instacart (3,4 millions de commandes, 206 000 utilisateurs, 50 000 produits), puis de concevoir un **modèle de Machine Learning prédictif** permettant de prédire le réachat d'articles par les utilisateurs (`reordered`).

---

## 💻 Guide Détaillé d'Installation et d'Exécution

### 1. Prérequis Système
Avant de commencer, assurez-vous d'avoir installé sur votre système :
- **Python** (version 3.10 ou supérieure) : `python3 --version`
- **Git** (pour le gestionnaire de versions) : `git --version`
- **Google Chrome** ou **Chromium** (optionnel, pour l'export PDF automatisé)

---

### 2. Procédure d'Installation Étape par Étape

#### Étape A : Cloner ou accéder au projet
```bash
cd /chemin/vers/votre/repertoire/T-DAT-600
```

#### Étape B : Préparation du jeu de données (Dataset)
Assurez-vous que les fichiers CSV du jeu de données Instacart sont placés dans le dossier `dataset/` à la racine :
```text
dataset/
├── orders.csv
├── order_products.csv
├── products.csv
├── aisles.csv
└── departments.csv
```

#### Étape C : Création et activation de l'environnement virtuel Python
Il est fortement recommandé d'utiliser un environnement virtuel isolé pour installer les dépendances sans interférer avec le système global :

* **Sur Linux / macOS** :
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```

* **Sur Windows (PowerShell / CMD)** :
  ```powershell
  python -m venv venv
  .\venv\Scripts\activate
  ```

#### Étape D : Installation des librairies requises
Une fois l'environnement virtuel activé, installez l'ensemble des bibliothèques nécessaires à l'aide du fichier `requirements.txt` :
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

---

### 3. Exécution et Génération des Livrables

#### A. Lancement du Notebook Jupyter (Analyse & Modélisation)
Pour ouvrir et exécuter le notebook interactif :
```bash
jupyter notebook eda.ipynb
```

#### B. Génération de l'Export HTML (`eda.html`)
Pour générer un rapport web autonome partageable sans serveur Jupyter :
```bash
jupyter nbconvert --to html eda.ipynb
```

#### C. Génération de l'Export PDF (`eda.pdf`)
Pour produire le document au format PDF :
```bash
google-chrome --headless --disable-gpu --print-to-pdf=eda.pdf --no-pdf-header-footer eda.html
```

---

## 📁 Structure Générale du Dépôt

```text
T-DAT-600/
├── eda.ipynb                    # Notebook principal (EDA + Feature Engineering + Machine Learning)
├── eda.html                     # Rapport exporté au format HTML (Livrable)
├── eda.pdf                      # Rapport exporté au format PDF (Livrable)
├── README.md                    # Documentation générale et guide d'installation (ce fichier)
├── requirements.txt             # Liste des dépendances Python requises
├── .gitignore                   # Fichier de règles d'exclusion pour Git
```

---

## 💡 Synthèse des Résultats & Insights Métier

1. **Comportement Temporel** : Pics de commandes observés le **Dimanche et Lundi (10h-16h)**. Le délai inter-commande présente deux cycles majeurs : **7 jours** (réachat hebdomadaire) et **30 jours** (réachat mensuel).
2. **Rayons Phares** : Les rayons **Produce (Produits Frais)** et **Dairy (Produits Laitiers)** concentrent le plus grand volume d'achats et les taux de réachat les plus élevés (~65%).
3. **Ordre d'Ajout au Panier** : Les 3 premiers articles ajoutés au panier ont une probabilité de réachat nettement supérieure (~68%).
4. **Modélisation ML** : La **Forêt Aléatoire (Random Forest)** atteint un score **ROC-AUC supérieur à 0.85**, surpassant la Régression Logistique grâce à la prise en compte des interactions non-linéaires entre le profil utilisateur et le produit.

--
