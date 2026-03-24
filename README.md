# Projet ISAIA 5 – Traitement Automatique du Malgache

[![Licence](https://img.shields.io/badge/Licence-MIT-green)](LICENSE)  
[![Python](https://img.shields.io/badge/Python-3.10-blue)](https://www.python.org/)

## Description

Ce projet vise à développer des outils de traitement automatique du malgache, incluant :

- Correction orthographique  
- Vérification des règles de base  
- Lemmatisation (avec modèle encodeur-décodeur)  
- Autocomplétion (méthode markovienne)  

Les données sont extraites du site [tenymalagasy.org](https://tenymalagasy.org).

---

## Membres du groupe

| N°  | Nom | Rôle |
|-----|-----|------|
| 09  | **TOVO Jean Bien Aimé** | Lemmatisation, autocomplétion, scraping des datasets |
| 08  | **RAJOHARIVELO Andriarivony Antenaina** | Développement du frontend |
| 12  | **RAKOTOMAHARAVO Vali Fanomezantsoa** | Vérification des règles à base de regex |
| 02  | **RAHERIMANANA Andriniaina Koloina Mandresy** | Correcteur orthographique |

---

## Fonctionnalités principales

### Correction orthographique
- Scraping des données depuis le site source.  
- Tokenisation et normalisation des entrées.  
- Chargement du dictionnaire malgache.  
- Détection des erreurs et recherche de candidats.  
- Calcul de similarité et sélection du meilleur candidat.  
- Validation, correction et reconstruction des entrées.

### Vérification des règles de base
- Identification de l’alphabet malgache.  
- Définition des règles : lettres interdites, consonnes interdites en fin de mots, combinaisons de consonnes autorisées.  
- Fonction interne pour vérifier les paires de consonnes.  
- Détection des erreurs via des expressions régulières (Regex).

### Lemmatisation
- Scraping du site pour constituer le dataset.  
- Construction du dataset d’entraînement.  
- Entraînement d’un modèle **encodeur-décodeur (Seq2Seq)** pour la lemmatisation.  
- Inférence sur de nouveaux mots.

### Autocomplétion
- Implémentation d’une méthode **markovienne** pour la suggestion de mots ou phrases.

---

# 🇲🇬 Malagasy Morpheme Segmentation — DataML

> **Projet de NLP** pour la segmentation morphologique et l'identification de racines en langue malgache, combinant scraping de données et apprentissage profond.

---

## 📁 Structure du Projet

```
DataML/
├── scraping/          ← Collecte et préparation des données
├── lemmnation/        ← Modèle de segmentation morphologique (Seq2Seq)
├── Backend/           ← API de service (FastAPI/Flask)
└── Front/             ← Interface utilisateur (React/Vue)
```

| Dossier | Rôle | Technologies |
|---|---|---|
| [`📂 scraping/`](./scraping/README.md) | Web scraping des racines malgaches, construction du dataset d'entraînement | Python, BeautifulSoup, Pandas |
| [`📂 lemmnation/`](./lemmnation/README.md) | Modèle Seq2Seq pour segmenter les mots en morphèmes et identifier la racine | TensorFlow, Keras, LSTM |
| [`📂 Backend/`](./Backend/README.md) | Serveur d'API pour exposer le modèle Keras | FastAPI, Uvicorn |
| [`📂 Front/`](./Front/README.md) | UI interactive pour tester la segmentation | React, Tailwind CSS |

---

## 🔄 Pipeline Global

```
┌─────────────────────────────────────────────────────────────────┐
│                        PIPELINE NLP                             │
├──────────────┬──────────────────┬──────────────────────────────┤
│   ÉTAPE 1    │     ÉTAPE 2      │          ÉTAPE 3             │
│  (scraping/) │   (scraping/)    │       (lemmnation/)          │
│              │                  │                              │
│  Scraping    │  Construction    │  Entraînement du modèle      │
│  du site web │  du dataset      │  Seq2Seq + Inférence         │
│  tenymalagasy│  d'entraînement  │                              │
└──────────────┴──────────────────┴──────────────────────────────┘
         ↓                ↓                    ↓
   racines.json    training_data.csv    model.keras + predict()
```

---

## 🚀 Démarrage Rapide

### 1. Cloner le projet

```bash
git clone <url-du-repo>
cd DataML
```

### 2. Installer les dépendances

```bash
pip install -r scraping/requirements.txt
```

### 3. Lancer Jupyter

```bash
cd lemmnation
jupyter notebook
```

> ⚠️ **GPU recommandé** — Voir [`lemmnation/README.md`](./lemmnation/README.md) pour la configuration GPU.

---

## 📊 Résultats

| Métrique | Valeur |
|---|---|
| Val Accuracy (meilleure) | **~98.6%** |
| Meilleure époque | **38 / 50** |
| Architecture | LSTM Seq2Seq (668K paramètres) |
| Taille du vocabulaire | **29 tokens** (26 caractères + 3 spéciaux) |

---

## 📈 Aperçu et Performances

### 1. Segmentation en Action (Demo)
Le modèle est capable de segmenter des mots complexes tout en isolant la racine entre crochets.
![Démo de segmentation](./lemmnation/models/demo.png)

### 2. Statistiques du Vocabulaire
Nous avons scrapé plus de **40 000 mots** avec leurs **règles grammaticales** respectives, créant ainsi une base solide pour l'apprentissage.
avec
![Vocabulaire](./lemmnation/models/vocabular.png)

### 3. Courbes d'Apprentissage
L'entraînement sur GPU a permis d'atteindre une précision de **98.76%** rapidement.
![Courbes d'entraînement](./lemmnation/models/training_curves.png)

### 1. Demostration (Demo)
![Démo de segmentation](./photo/demo1.png)

---

## 🔗 Dossiers — Cliquez pour les détails

- **[📂 scraping/](./scraping/README.md)** — Scraping des racines malgaches depuis tenymalagasy.org
- **[📂 lemmnation/](./lemmnation/README.md)** — Modèle de segmentation morphologique Seq2Seq
- **[📂 Backend/](./Backend/README.md)** — API de service (FastAPI/Flask)
- **[📂 Front/](./Front/README.md)** — Interface utilisateur (React/Vue)
