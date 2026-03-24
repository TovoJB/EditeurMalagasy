# Malagasy Root Scraper 🇲🇬

Projet de scraping pour extraire les racines malgaches et leurs dérivés à partir de [tenymalagasy.org](https://tenymalagasy.org/bins/rootLists).

## Structure du Projet 🏗️

- `Malagasy_Root_Scraper.ipynb` : Notebook Jupyter contenant le code principal.
- `requirements.txt` : Liste des dépendances nécessaires.
- `malagasy_roots.json` : Exportation des données au format JSON (généré après exécution).
- `malagasy_roots.csv` : Exportation des données au format CSV (généré après exécution).

## Comment utiliser ? 🚀

1. Installez les dépendances :
   ```bash
   pip install -r requirements.txt
   ```

2. Lancez Jupyter Notebook ou Jupyter Lab :
   ```bash
   jupyter notebook
   ```

3. Ouvrez et exécutez toutes les cellules de `Malagasy_Root_Scraper.ipynb`.

## Données Extraites 📊

Le script extrait :
- La racine (root)
- Les mots dérivés associés
- Format final : Un dictionnaire `{"word": "teny", "root": "teny"}`.

jupyter notebook