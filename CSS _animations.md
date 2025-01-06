# Transition
transition: transform 300ms ease-in-out;
fonction + durée + fonction de timing +(retard)

**fonction de timing** : accélération / décélération
Par défaut : linear
timing custom avec cubic-bezier qui fonctionne comme la fonction  rgb()  : on indique une liste de valeurs numériques, mais au lieu de transformer ces chiffres en couleur, la fonction  cubic-bezier  les transforme en courbe d’accélération.

Les transitions se déclenchent via pseudo classe 

**Optimisation** : transform & opacity, éviter de rentrer dans la phase de “paint”

# Keyframes
**Keyframes** permettent de définir des changements selon le % d’animation + cumuler les propriétés
- déclenchement par pseudo classe ou à l'installation
- animation-delay + animation-timing-function (similaire aux transitions)
- animation-fill-mode : prolonger la durée :
  - backwards  prolonge les valeurs de départ d'une animation avant son lancement, 
  - forwards » prolonge les valeurs finales d'une animation jusqu'à ce que la page soit rechargée ou que le navigateur soit fermé,
  - both  prolonge l'animation dans les deux sens ;
