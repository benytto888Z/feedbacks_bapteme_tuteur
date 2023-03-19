# API Fetch

- Il fut un temps où l’on utilisait XMLHttpRequest pour créer des requêtes API(Application
 Programming Interface). Il n’intégrait pas les promesses et n’était pas conçu pour générer des codes JavaScript propres.

Maintenant, JavaScript intègre un moyen qui lui est propre de créer des requêtes API. Il s’agit de l’API Fetch, une nouvelle norme qui permet de réaliser des requêtes sur un serveur en utilisant des promesses. Elle intègre cependant bien d’autres fonctionnalités.
-L’API Fetch va également utiliser la méthode globale fetch() qui représente en quelques sortes le coeur de celle-ci. Cette méthode permet l’échange de données avec le serveur de manière asynchrone.

Le premier paramètre de cette méthode sera souvent une chaîne de caractères indiquant l'URL de la ressource à aller récupérer et le second paramètre sera un objet d'options spécifiant les informations à envoyer avec la requête (méthode, en tête...)

- La promesse est résolue avec un objet Response qui contiendra des informations sur le retour fait par le serveur. Cet objet contiendra notamment une propriété ok qui sera vraie sur la status de la réponse est compris entre 200 et 299 (les redirects sont pris suivi lors de l'appel HTTP)
On aura aussi 2 méthodes intéréssantes :

text() qui renverra le texte de la réponse
json() qui parsera la réponse au format JSON.

# Exemple : Affichage de la liste des cartes

## création du web service
- 0 . Notre endpoint est /api/cards
- 1 . dans router.js crée la route :

```
router.get('/api/cards', mainController.fetchAllCards);
```

- 2 . au niveau de ton mainController crée la méthode :

```
   fetchAllCards: async (req, res) => {
    try {
      const cards = await dataMapper.getAllCards();
      res.status(200).send(cards)
    } catch (error) {
      console.error(error);
      res.status(500).send(`An error occured with the database :\n${error.message}`);
    }
  }
```

- 3 . au niveau de index.js  après avoir faire "npm install cors" dans ton terminal ajoute :

```
const cors = require('cors'); 
app.use(cors())
app.use((req, res, next) => {
    res.setHeader('Access-Control-Allow-Origin', '*');
    res.setHeader('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content, Accept, Content-Type, Authorization');
    res.setHeader('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE, PATCH, OPTIONS');
    next();
});

```

- le package cors permettra au client(ex : application  frontend) d'obtenir l’autorisation d’accéder aux ressources de l'api et de les charger.

- 4 . en tapant l'url (http://localhost:3000/api/cards) dans ton navigateur tu peux déjà voir la liste des cartes
affichée sous forme de données json - Pour tester les api tu peux utiliser le logiciel Postman ou insomnia
- Et voilà notre api est prête pour être consommée.

## Mise en place du client
- 1 . Crée un dossier frontend à la racine de ton projet actuel
- 2 . A l'interieur de ce dossier créé les fichiers
`fetchcards.js`

 ```
document.getElementById("spanDate").innerHTML = new Date().getFullYear();
fetch("http://localhost:3000/api/cards", {
  headers: {
    Accept: "application/json",
  },
})
  .then((response) => {
    if (response.ok) {
      // On utilise la méthode json() pour convertir response en données JSON :
      return response.json();
    } else {
      throw new Error("Erreur serveur", { cause: r });
    }
  })
  .then((cards) => {
    // traiter les données JSON
    showGameCards(cards);
  })
  .catch((e) => {
    console.error("Une erreur est survenue", e);
  });

const showGameCards = (cards) => {
  let cardsDOM = "";
  if (cards.length) {
    cards.forEach((card) => {
      cardsDOM += `
    <div class="card">
      <a href="#">
        <img src="http://localhost:3000/visuals/${card.visual_name}" alt="${card.name} illustration">
        <p class="cardName"> ${card.name}</p>
      </a>
    </div>
    `;
    });
  } else {
    cardsDOM = Empty;
  }
  document.querySelector(".main").innerHTML = cardsDOM;
};
 ```

`index.html`

 ```
 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./fetchcards.js" defer></script>
    <link rel="stylesheet" href="style.css">
    <title>cardlist</title>
</head>
<body>
    
    <header class="header">
    <a class="sitename" href="/">Triple Triad Deck Builder</a>

    <nav>
      <a href="/">Cartes</a>
      <a href="/search">Recherche</a>
      <a href="/deck">Decks</a>
    </nav>

  </header>

  <main class="main cardsContainer">
  
  </main>

<footer class="footer">
  &copy; O'clock & SquareEnix - <span id="spanDate"></span>
</footer>

</body>
</html>
 ```

- 3 . Dans vscode au niveau du dossier frontend ouvre index.html avec live server
- Les cartes devraient s'afficher.

- Certains détails peuvent ne pas être clairs tout de suite à ton niveau ,
mais avec de la pratique tu finiras pas tout comprendre. 