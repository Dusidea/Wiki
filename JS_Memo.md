# Memo JavaScript

## Objets et Tableaux

- objets : accès => monObjet.propriété
- accéder aux éléments d’un tableau : monTableau[i]
- taille du tableau : monTableau.length
- ajout/retrait d’un élément à la fin d'un tableau : push/pop

## Récupérer un élément de page web :

- document.querySelector
- document.querySelectorAll
- document.getElementById

## Modifier un élément :

- var.setAttribute (“attribut”, “nouvelle valeur”)
- var.attribut =””
- var.classList.add
- var.classList.remove

## Créer un élément :

- document.createElement(“div”)
- parentElement.appendChild(nouvelElement);
- InnerHTML ``
- Interpolation (on peut utiliser des variables dans ces morceaux d’HTML à injecter)

# Détecter un évenement : action utilisateur ou chargement de page par ex

La programmation événementielle consiste à écrire du code qui réagit à des événements.
Un événement est un signal envoyé par l’élément HTML lorsque l’utilisateur effectue une action (clic, frappe au clavier…).
Pour savoir quand un événement est envoyé, vous devez attacher un écouteur à l’élément HTML.
Pour gérer un événement, vous devez l’écouter en utilisant la méthode AddEventListener.

EventListener : addEventListener ( “Event”, () => {})

Vous pouvez récupérer des informations sur un événement en utilisant la variable event.

- event.target : renvoie l’élément HTML qui a déclenché l’événement ;
- event.key : la touche appuyée quand l’événement écouté est lié au clavier ;
- event.clientX et event.clientY : les coordonnées de la souris quand l’événement écouté est lié à la souris.

Evénements :

- https://developer.mozilla.org/fr/docs/Web/Event

## Ordre d'exécution des fonctions
### Résumé des mécanismes déterminants :
- Les fonctions synchrones s'exécutent dans l'ordre d'appel (de haut en bas).
- Les tâches asynchrones (comme les timers ou les promesses) sont placées dans une file d’attente : Les micro-tâches sont exécutées avant les macrotâches.
- Le contrôle de la boucle d’événements s'assure que le code principal est terminé avant de traiter les tâches différées.

### Priorité de la boucle d’événements
#### Pile d'exécution (Call Stack)
Les fonctions synchrones sont exécutées directement dans la pile.

#### Microtask Queue (Micro-tâches)
Elle gère :

- Les promesses.
- Les tâches liées à async/await. Elle est toujours vidée avant la file de macrotâches.

#### Macrotask Queue (Macrotâches)
Elle inclut :
- setTimeout, setInterval.
- requestAnimationFrame.
- I/O ou événements d'utilisateur.
