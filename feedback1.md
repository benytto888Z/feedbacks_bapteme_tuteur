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
- searchController (Ligne 22) Le symbole " + " cherche à faire une addition avec une chaîne de caractères
ce qui aboutit à l'erreur NaN(Not a Number) sur ta page de recherche par "élémént"
- Au niveau du "dataMapper.js"  tu as laissé la méthode "searchByElementNull()" qui
n'est utilisée null part dans le projet . Tu as aussi laissé des commentaires surperflus dans
searchController ligne 8

### Conseils

- Installer et utiliser le linter Eslint : <https://eslint.org/>
- Eslint va permettre d'avoir un code  d’une bonne qualité syntaxique
- Une bonne lisibilité du code, que ça soit par toi, plus tard, ou par tes collègues ;
- Une meilleure maintenabilité, notamment grâce à cette lisibilité améliorée ;
- Il va analyser ton code pour en faire ressortir les erreurs ou incohérences en fonction de règles prédéfinies
- Ainsi tu pourras dans un gros projet te débarraser rapidement des bouts de codes inutilisés et des commentaires surperflus.

## Étape 3 : Construire un deck

On veut pouvoir construire un deck de 5 cartes différentes.

Pour ça, on va utiliser les sessions.

Et pour éviter de faire trop d'appels à la base de données, on va directement stocker toutes les données des cartes dans la session (et pas _juste_ les ID).

### 3.1: Activer les sessions

### Commentaires

- "express-session" est installée 👍

### 3.2 Ajouter une carte au deck

### Attentes

- Les liens `[+]`, présents sur toutes les cartes, doivent ajouter la carte au deck de la session.

- Si la carte est déjà présente dans le deck ou que le deck possède déjà 5 cartes, on ne fait rien !

### Commentaires

- Attentes satisfaisantes 👍

### 3.3 Une page pour visualiser le deck

### Attentes

- Mettre  en place la route `/deck`
- Construire  la view pour l'affichage du Deck

### Commentaires

- Attentes satisfaisantes 👍

### 3.4 Supprimer une carte du deck

### Attentes

- Ajouter des liens pour supprimer chacune des cartes du deck.

### Commentaires

- Attentes satisfaisantes 👍

## Bonus: finir les recherches

### Commentaires

- Bravo pour avoir ajouté le bonus 👏🏻👏🏻👏🏻

### Recherche par niveau

On veut le niveau exact. Pas de "au moins".

### Commentaires

- Attentes satisfaisantes 👍
- Mais attention aux actions de l'utilisateur au niveau de l'url (Never Trust The User Input)
- On attend un entier en paramètre au niveau de l'url exemple : <http://localhost:5001/search/level?level=3>
- L'utilisateur pourrait bien ajouter manuellement ...level?level=oclock😃 , et là le resultat est : "An error occured" . PAS DU TOUT USER FRIENDLY

### Conseils

- Tester le paramètre level
- Et faire une redirection vers la page Not Found avec le message "Niveau introuvable" par exemple.

### Recherche par valeur

On veut toutes les cartes qui ont _au moins_ la valeur choisi dans la direction sélectionnée.

### Commentaires

- Attentes satisfaisantes 👍
- Bien joué pour le refactoring de la méthode "searchByValues()". Bien vu pour ta
proposition 👏🏻👏🏻👏🏻.
- Suivre les mêmes suggestions que les commentaires et conseils précédents

### Par nom

On veut les cartes dont le nom contient la valeur entrée.

### Commentaires

- Attentes satisfaisantes 👍

### Points forts 💪💪

- Ajout de quelques commentaires, mais tu peux faire mieux
- Les routes sont définies dans un fichiers unique.
Le site est fonctionnel et conforme aux maquettes
Code bien organisé et indenté
- Découpage des vues partials/ en templates réutilisables
- La navigation fonctionne convenablement et affiche la page 404 en cas de route non définie
- Création d'un middleware pour gérer la session
- Le masquage des données avec dotenv
- Tu t'es aussi penché sur le Bonus. C'est Top.

### Axes d'amélioration

- Côté sécurité des données qui transitent par le navigateur ;
visite ce lien : <https://www.ionos.fr/digitalguide/sites-internet/developpement-web/get-vs-post/>

- Tenir compte des normes et réglementations importantes en matière de sécurité des données
- Utiliser la référence OWASP (Open Web Application Security Project)
pour le développement d’applications web ! . On va ainsi prévenir , les injections sql(facile à implémenter
grâce aux données transitant par url avec la méthode get) , les attaques xss, csrf etc..

- Par exemple : utiliser le package helmet
helmet est un middleware permettant d’ajout de la sécurité à un serveur Express. Via la simple inclusion de la ligne de code suivant :
app.use(helmet());
- Pour comprendre comment sécuriser ses applications nodejs : <https://cours-info.iut-bm.univ-fcomte.fr/upload/supports/S3/web/cot%20serveur/TP12.pdf>

- Utiliser un Object Relational Mapper (ORM) : Obfusque les requêtes
- Exemples d'ORM: Sequelize pour Mysql et PostgreSQL , TypeOrm pour PostgreSQL.
