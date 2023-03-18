# Atelier Solo : Triple Triad Deck Builder

# Mission

Triple Triad est un jeu de plateau à base de cartes, inventé par SquareEnix et présent dans Final Fantasy 8.

Les règles sont plutôt simples, mais ce n'est pas ce qui nous intéresse aujourd'hui !

On a récupéré toutes les données relatives aux cartes ainsi que leurs visuels. Et on voudrait construire une application pour gérer nos cartes, chercher des cartes selons plusieurs critères, et même gérer nos decks (= paquets de 5 cartes différentes).

# Feedback Tuteur-AMOUZOUN

## Étape 0 : Analyse du code fourni et mise en place de la BD

### Attentes

- Analyse du code fourni pour comprendre ce qui a déjà été fait et voir ce que tu va pouvoir réutiliser dans la suite.

- Mettre en place la base de données à partir du fichier `data/create_db.sql`.

## Étape 1 : Détail d'une carte

### Attentes

Quand on clique sur carte dans la page d'accueil, on veut arriver sur la page "détail de la carte".

### Commentaires

- La page d'acceuil n'affiche pas correctement les cartes . Doublure des noms de cartes
- Pour plus d'élégance tu aurais dû entourer seulement chaque carte image avec la balise <a></a>
- La page cardDetails ne s'affiche pas correctement . Tu utile une boucle alors que tu es censé recevoir
les informations d'une carte ; de plus la bonne information n'est pas envoyé depuis le mainController (ligne 29) . Tu renvoies la variable "oneCard" au lieu de la variable "card"
- Revoir la correction type . Je suis sûr que tu vas y arriver 🚀

## Étape 2 : Recherche

### Attentes

- Recherche par "élément"

### Commentaires

- La recherche par élément ne fonctionne pas
- Dans searchController tu ne fais pas appel à la méthode dataMapper(const dataMapper = require("../dataMapper"). De plus la methode cardElement() n'existe pas dans dataMapper.js

### Conseils

- Installer et utiliser le linter Eslint : <https://eslint.org/>
- Eslint va permettre d'avoir un code  d’une bonne qualité syntaxique
- Une bonne lisibilité du code, que ça soit par toi, plus tard, ou par tes collègues ;
- Une meilleure maintenabilité, notamment grâce à cette lisibilité améliorée ;
- Il va analyser ton code pour en faire ressortir les erreurs ou incohérences en fonction de règles prédéfinies

## Étape 3 : Construire un deck

On veut pouvoir construire un deck de 5 cartes différentes.

Pour ça, on va utiliser les sessions.

Et pour éviter de faire trop d'appels à la base de données, on va directement stocker toutes les données des cartes dans la session (et pas _juste_ les ID).

### Commentaires

- Tu n'as pas pu implémenter le Deck. je peux comprendre parce que le fait
de ne pas implémenter correctement l'affichage des details d'une carte a joué sur 
le reste des fonctionalités
- Revoir la correction type

### Axes d'amélioration

- Il faut retravailler le projet
- Revoir les l'utilisation du moteur de rendu ejs dans un projet nodejs
- Bien étudier le concept de la transmission des données entre les pages
- Aller je suis sûr qu'avec un peu d'effort tu vas y arriver..🚀🚀🚀
- N'hésite pas à te rapprocher de tes collègues pour des éclaircissements.
- Ton formateur et aussi ton tuteur sont aussi là pour t'éclairer davantage