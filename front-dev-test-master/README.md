# Test developpeur front-end

Ce projet utilise [Vitejs](https://vitejs.dev)

# 🛫 Installation

`npm i` puis `npm run dev` pour lancer le serveur de developpement.

`npm run build` pour générer une version de production de l'app.

Le code source de l'application se trouve dans le dossier `src/`.

# ✈️ Objectifs

- Créer une simple application permettant de rechercher un film.

- L'application se présente sous la forme d'une seule page (pas de routing) avec une barre de recherche et une liste de résultats. Lorsque l'on clique sur un résultat, une fenetre s'ouvre avec les détails du film.

- Pour se faire, utiliser l'API [OMDB](http://www.omdbapi.com) avec la key `23aaa32`.

- Utiliser l'API avec le paramètre de recherche (par exemple : `?s=Matrix`) pour récupérer la liste des films. Afficher toutes les données recues dans la liste.

- Utiliser l'API avec le paramètre ID (par exemple : `?i=tt7002456`) pour récupérer les détails d'un film a partir de l'ID du résultat de recherche. Afficher les infos de la liste + le synopsis et la liste des acteurs dans la fenetre.

---

- Imaginez que l'on doive implémenter un système où l'utilisateur peut choisir pour chaque lettre de l'alphabet son film favori commençant par cette lettre, _e.g. D -> Dead Man_.

- Ne vous souciez pas des cas où le film commence par 'The', 'Le/La', etc ...

- Lancez la commande

```sh
npm run test MoviePicker
```

- Regardez dans le répertoire **src/MoviePicker/**

- Implémentez la classe **MoviePicker** et les 2 types d'erreurs **MoviePickAlreadyExistError**, **EmptyMovieTitleError** de telle sorte que les tests passent :

  - A la construction, une classe répondant à l'interface MoviePickRepo doit pouvoir être "injectée" dans MoviePicker.
  - On doit pouvoir ajouter des titres de film.
  - Si le titre donné est vide, une exception EmptyMovieTitleError doit être lancée.
  - Si le titre commence par une lettre pour laquelle un choix a déjà été effectué, une exception MoviePickAlreadyExistError doit être lancée.

- Regardez src/MoviePicker/MemoryMoviePickRepo.ts. Il s'agit d'une implémentation 'en mémoire' de l'interface MoviePickRepo.
  Celle-ci est utilisé dans les tests MoviePicker.spec.ts.

- Implémentez une autre version de l'interface MoviePickRepo utilisant une solution de stockage de votre choix disponible dans les navigateurs, e.g. LocalStorage, IndexedDB, ...

- Bonus possibles :
  - Afficher la liste des 'picks' de l'utilisateur dans l'app react.
  - Placer un bouton dans la vue détail d'un film permettant de l'ajouter à la liste des 'picks' de l'utilisateur et de l'avertir s'il à déjà fait un choix pour cette lettre.

# ⚠️ Contraintes

- Utiliser les composants de la librairie [Material UI](https://material-ui.com/) pour la barre de recherche, la liste de résultats, et la fenetre.
- Utiliser des Function Components et les Hooks React. Pas de Class Components.
- Utiliser async / await lors du traitement de Promises. Pas de then() / catch() ou de callbacks.
- Utiliser fetch pour effectuer les requêtes à l'API. Pas de librairie externe tel Axios.
- Utiliser Redux pour gérer la liste des films, les états de chargement et d'erreur dans la liste, et la fenetre de détails (son état ouvert/fermé et son contenu). Utiliser useState la barre de recherche.
- Utiliser le module [Redux Toolkit](https://redux-toolkit.js.org) pour configurer Redux.
- Utiliser Typescript !
  - Créer des types Movie et MovieSearchResult utilisables dans toute l'application.
  - Créer une classe Omdb qui fait office de service pour appeller l'API avec une méthode de recherche et de récupération de film. (nommées searchMovies et getMovie par exemple).
  - Regardez apps/react-app/src/JSON.d.ts, les définitions JSON.parse() et de response.json() ( utilisé après un fetch ) ont été modififés pour retourner **unknown**. Vous devrez parser les résultats de ces fonctions et prouver au système de type que les résultats correspondent aux schémas attendus. Il n'est pas nécessaire de couvrir l'intégralité du schéma proposé par OMBD, uniquement les propriétés dont vous avez besoin dans l'application.Vous pouvez prendre en charge la rédaction de fonctions de parsing/validation, mais vous êtes libre d'utiliser une librairie si vous en connaissez une.

# 💡 Pensez-y

- Gérez les erreurs et affichez un message dans l'interface (pas seulement dans la console ou avec une alert box)
- Gérer les temps de chargement visuellement (Avec un composant CircularProgress de la librairie Material UI par exemple)
- Optimisez les render React
- Organisez vos fichiers

# ✅ Livrable

Pusher le code sur un dépot Github public.

- Bonus :
  - Builder et déployer l'app sur Github Pages, Vercel, ou Netlify.
