1+ **Membre du groupe:**
n° 09 TOVO Jean Bien Aimé         ISAIA 5
Role: Pris en charge du developpement du lemmatisation et Autocomplétion

n° 08 RAJOHARIVELO Andriarivony Antenaina         ISAIA 5
Role: Pris en charge du developpement du frontend

n° 12 RAKOTOMAHARAVO Vali Fanomezantsoa         ISAIA 5
Role: Pris en charge du developpement de la verification à base de règles

n° 02 RAHERIMANANA Andriniaina Koloina Mandresy         ISAIA 5
Role: Pris en charge du developpement du correcteur orthographique

**Bibliographie**
source de données : tenymalagasy.org

**Liste et brève description du fonctionnalité IA**
**correction orthographique** : scrapping des données, tokenisation et normalisation des inputs, chargement du dictionnaire, puis detection des erreurs, recherche de candidats, calcul de similarité et selection du meilleur candidat. En dernier, la validation, la correction et la reconstruction de l'input

**Vérification des règles de base**: Citez les alaphabets malagasy, determiner les règles (les lettres interdites et consonnes interdites en fin de mots), combinaison de consonnes autorisées, et puis création d'une fonction interne pour vérifier les paires de consonnes. Enfin, detection des erreurs a partir des regle Regex classique

**Lemmatisation** : scrapping du site web tenymalagasy, construction du datasets d'entrainement et entrainement du modèle Seq2Seq + Infrérence

**Autocomplétion**: utilisation du méthode markovienne


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

---

## 🔗 Dossiers — Cliquez pour les détails

- **[📂 scraping/](./scraping/README.md)** — Scraping des racines malgaches depuis tenymalagasy.org
- **[📂 lemmnation/](./lemmnation/README.md)** — Modèle de segmentation morphologique Seq2Seq
- **[📂 Backend/](./Backend/README.md)** — API de service (FastAPI/Flask)
- **[📂 Front/](./Front/README.md)** — Interface utilisateur (React/Vue)
