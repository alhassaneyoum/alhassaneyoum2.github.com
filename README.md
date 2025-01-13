# alhassaneyoum2.github.com
Projet-R-Web-Scraping
# README : Analyse des Genres et Sentiments des Meilleures Séries Télévisées

## Description du Projet

Ce projet explore les caractéristiques des meilleures séries télévisées listées sur le site Allociné. Il vise à mettre en lumière les genres dominants et à analyser les sentiments des spectateurs à travers leurs commentaires. 

Les objectifs principaux sont :
- Identifier les genres les plus fréquents parmi les séries bien notées.
- Analyser les sentiments des spectateurs pour comprendre leur perception.
- Fournir des visualisations claires et informatives pour interpréter les données.


## Structure du projet

1. **Extraction de données via Web Scraping**
   - Récupération des titres, genres, et commentaires des séries télévisées depuis Allociné.
   - Nettoyage et structuration des données pour une analyse optimale.

2. **Analyse descriptive des genres**
   - Identification des genres les plus représentés.
   - Visualisation sous forme de graphiques (camemberts, histogrammes).

3. **Analyse des sentiments**
   - Traitement des commentaires de spectateurs pour une série sélectionnée.
   - Classification des sentiments en positifs, négatifs et neutres.
   - Création de nuages de mots pour visualiser les thèmes récurrents.

4. **Visualisation des résultats**
   - Diagrammes et graphiques pour illustrer les tendances et les résultats.

---

## Structure du Projet

### 1. Packages Utilisés
Le projet repose sur les bibliothèques suivantes :
- `stringr` : Manipulation des chaînes de caractères.
- `rvest` : Extraction de données HTML pour le web scraping.
- `dplyr` et `tidyr` : Transformation et manipulation des données.
- `ggplot2` : Création de graphiques.
- `wordcloud` : Génération de nuages de mots.
- `RColorBrewer` : Palettes de couleurs pour les visualisations.

### 2. Étapes Principales

#### **Étape 1 : Web Scraping**
- Extraction des notes de presse et spectateurs, titres et genres des 150 meilleures séries sur Allociné.
- Nettoyage des données pour supprimer les doublons, valeurs manquantes et éléments inutiles.

#### **Étape 2 : Analyse des Genres**
- Comptage des occurrences des genres.
- Identification des genres dominants à l’aide de graphiques.

#### **Étape 3 : Analyse des Sentiments**
- Analyse des commentaires pour une série sélectionnée.
- Calcul des scores de sentiment (positif, neutre, négatif).
- Création d’un diagramme circulaire pour visualiser la répartition des sentiments.

#### **Étape 4 : Visualisation et Interprétation**
- Création de graphiques et nuages de mots pour illustrer les thèmes récurrents.
- Mise en évidence des genres dominants et des sentiments associés aux séries.

---

## Fichiers Inclus

- **Script principal (`programmation.qmd`)** : Contient le code pour les analyses.
- **README.md** : Ce fichier expliquant le projet.


- **Extraction des données** :
  ```R
  url <- "https://www.allocine.fr/series/meilleures/"
  page <- read_html(url)
  ```

- **Analyse des genres** :
  ```R
  genre_data <- series_data %>%
    separate_rows(Genre, sep = ",") %>%
    group_by(Genre) %>%
    summarise(Count = n())
  ```

- **Analyse des sentiments** :
  ```R
  sentiment_scores <- sapply(comments_clean, function(comment) {
    pos <- sum(sapply(positive_words, function(word) grepl(word, comment, ignore.case = TRUE)))
    neg <- sum(sapply(negative_words, function(word) grepl(word, comment, ignore.case = TRUE)))
    pos - neg
  })
  ```

## Résultats et Interprétation

### Analyse des Genres
- Le genre **Drame** est dominant avec une fréquence de **26,2 %**.
- Autres genres notables : **Historique (15,7 %)**, **Animation (7,8 %)**.

### Analyse des Sentiments
- Répartition équilibrée entre sentiments neutres et positifs.
- Les thèmes récurrents incluent les intrigues, les performances des acteurs, et la qualité de la production.

### Visualisations
- Diagrammes circulaires pour les genres et les sentiments.
- Nuages de mots illustrant les termes les plus fréquents dans les commentaires.
