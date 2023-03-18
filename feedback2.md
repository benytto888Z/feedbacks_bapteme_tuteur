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

- Attentes satisfaisantes 👍

## Étape 2 : Recherche

### Attentes

- Recherche par "élément"

### Commentaires

- La recherche par élément affiche effectivement le bon resultat 👍

## Étape 3 : Construire un deck

### Ojectifs

- construire un deck de 5 cartes différentes.
- stocker toutes les données des cartes dans une session
pour éviter de faire trop d'appels à la base de données

### 3.1: Activer les sessions

### Commentaires

- "express-session" est installée 👍

### 3.2 Ajouter une carte au deck

### Attentes

- Les liens `[+]`, présents sur toutes les cartes, doivent ajouter la carte au deck de la session.

- Si la carte est déjà présente dans le deck ou que le deck possède déjà 5 cartes, on ne fait rien !

### Commentaires

- Les cartes sont bien ajoutées dans le deck
- Mais il manque la condition qui vérifie si le nombre de cartes n'est pas déjà égal à 5
- On arrive à ajouter plus de 5 cartes dans le deck
- Tester d'abord :  if (request.session.deck.length < 5), avant
d'ajouter un nouveau une nouvelle carte dans le tableau request.session.deck

### 3.3 Une page pour visualiser le deck

### Attentes

- Mettre  en place la route `/deck`
- Construire  la view pour l'affichage du Deck

### Commentaires

- Deck.ejs ligne 38 : Il n'a pas de champ price dans la table card.
- Reprend la mise en forme de ta vue deck.ejs avec une bonne utilation de la balise <table></table>

### 3.4 Supprimer une carte du deck

### Attentes

- Ajouter des liens pour supprimer chacune des cartes du deck.

### Commentaires

- Ces liens sont ajoutés au moment de la boucle d'affichage des déléments du tableau request.session.deck
- Tu peux y arriver en reprenant la correction-type 🤗🤗🤗

### Points forts 💪💪

- Le code est propre et bien indenté
- Les routes sont définies dans un fichiers unique.
Le site est fonctionnel et conforme aux maquettes
Code bien organisé et indenté
- Découpage des vues partials/ en templates réutilisables
- La navigation fonctionne convenablement et affiche la page 404 en cas de route non définie

- Le masquage des données avec dotenv

### Axes d'amélioration

- Ajout de quelques commentaires pour soi même et pour un travail collaboratif

- Tenir compte des normes et réglementations importantes en matière de sécurité des données
- Utiliser la référence OWASP (Open Web Application Security Project)
pour le développement d’applications web ! . On va ainsi prévenir , les injections sql(facile à implémenter
grâce aux données transitant par url avec la méthode get) , les attaques xss, csrf etc..

- Par exemple : utiliser le package helmet
helmet est un middleware permettant d’ajout de la sécurité à un serveur Express. Via la simple inclusion de la ligne de code suivant :
app.use(helmet());
- Pour comprendre comment sécuriser ses applications nodejs : <https://cours-info.iut-bm.univ-fcomte.fr/upload/supports/S3/web/cot%20serveur/TP12.pdf>

- Utilisez un Object Relational Mapper (ORM) : Obfusque les requêtes
- Exemples d'ORM: Sequelize pour Mysql et PostgreSQL , TypeOrm pour PostgreSQL.
