## React : 
- framework de JS (ensemble de classes, fonctions et utilitaires réutilisables) pour les besoins courants
- Créer des interfaces utilisateurs modulaires => composants réutilisables
- vient directement modifier le DOM de la page web
## Extension .jsx  : 
autorise l’interpolation => utiliser du html dans le code
## Composants : 
réutilisables et intégrables dans une même page html (une seule page pour l’utilisateur). Regroupent : 
- gestion des comportements (JS) , 
- structure(html),
- style (css ou scss ou tailwind) 
## Props : 
- Les props sont des objets que l'on peut récupérer dans les paramètres de notre composant fonction.
- La prop  children  est renseignée en imbriquant les enfants dans le parent : <Parent><Enfant /></Parent>. (utile quand on ne connaît pas à l’avance les enfants, fetch ou réutilisation du composant)

## Hook : 
Un hook est une fonction qui permet de « se brancher » (to hook up) sur des fonctionnalités React
## State :
permet de préserver les données liées au composant (stable malgré le re render). Local au composant
## useState   
est un hook qui permet d’ajouter le state local React à des fonctions composant. Renvoie une paire de valeurs dans un tableau de 2 éléments
## useEffect : 
- effectuer des effets : permet à notre composant d'exécuter des actions après l'affichage, en choisissant à quel moment cette action doit être exécutée. 
- appelé après chaque rendu du composant. 
- possible de préciser quelle modification de donnée déclenche les effets exécutés dans useEffect, avec le tableau de dépendances.
