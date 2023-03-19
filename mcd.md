# MCD

## Corrections

### J'ai constaté deux erreurs

### 1 .  relation |User| (...) <---HAS---> (...) |Address|

#### Redéfinition des rêgles

 *Un utilisateur peut créer sur son compte une ou plusieurs adresses de livraison.*<br>
   *Une adresse de livraison peut appartenir à un ou plusieurs utilisateurs s'ils habitent ensemble*

 ```diff
      - Donc relation ManyToMany avec une table intermediaire contenant les clefs étrangères des tables(User,Address)
      > |User| (1,n) <---HAS---> (1,n) |Product|
   ```

### 2 .  relation |User| (...) <---LIKE---> (...) |Product|

#### Redéfinition des rêgles

 *Un utilisateur peut liker zéro ou plusieurs produits.*<br>
    *Un produit peut être liké par zéro ou plusieurs utilisateurs.*

```diff
      - Donc relation ManyToMany avec une table intermediaire contenant les clefs étrangères des tables(User,Product)
      > |User| (0,n) <---HAS---> (0,n) |Product|
```

- Il existe beaucoup de logiciels permettant la modélisation.

Globalement, ils se regroupent en deux catégories :

- Les outils graphiques, qui ne sont pas réservés à l’UML, mais qui permettent de créer facilement tous types de diagrammes.

- Les ateliers de génie logiciel (AGL) : ce sont des environnements de conception, souvent très puissants. Contrairement aux outils graphiques (qui ne font que produire un dessin), les AGL « comprennent » la modélisation UML et ils sont capables d’interpréter votre modélisation afin de vous faciliter la tâche : vérification du modèle, génération du code informatique découlant du diagramme de classes, etc). Ils sont cependant plus difficiles à prendre en main.

- Parmi les outils graphiques les plus connus, on trouve LibreOffice Draw, diagrams.net, LucidChart, etc.

- En ce qui concerne les AGL, l’un des plus connus s’appelle ArgoUML. Vous tu peux tester également Papyrus, qui est un environnement de modélisation performant fonctionnant sous Windows, MacOS et Linux. Il est gratuit, open source et développé par la fondation Eclipse.

J'utilise  souvent diagrams.net .

Il est gratuit, et ne nécessite pas d’installation : c’est une application web, qui s’utilise depuis le navigateur (Firefox, Chrome, Safari, Edge, etc.), et ne nécessite même pas la création d’un compte !

[RETOUR](/autoevaluation.md)
