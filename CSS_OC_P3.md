# Taille des conteneurs et écartements

* Logique des **espacements** : poser les écarts entre blocs comme sur la maquette plutot que sur 1er/dernier objet du bloc + lisible au débug, plutot que de devoir passer sur les éléments internes pour repérer les marges
* Fonctionnement des **gap** : permet de gérer l'espace entre les éléments d'un conteneurs, à condition que celui-ci soit en display **flex**
* Eléments qui **débordent du conteneur** : appliquer **box-sizing border box** pour intégrer les paddings aux marges à la taille des conteneurs => ne pas hésiter à l'appliquer à toute la feuille
* Les **tailles en %** ne peuvent fonctionner que si le parent a une hauteur fixe en pixels. Donc width 100% est inefficace si le parent n'a pas de taille définie en px.

# Bonnes pratiques

* Pour débuguer et comprendre : **réduire la complexité**. Quand quelque chose ne fonctionne pas comme attendu => créer des fichiers avec seulement une rubrique de l’html et supprimer les parents du plus proche au + loin
* Bonnes pratiques de **nommage des classes** kebab
* Dans l'inspecteur du navigateur : **décocher les propriétés** de style une par une pour identifier celle qui influe (une case à cocher apparait au survol)
* Ajouter une **border rouge** pour voir le bord des blocs  
```
{
    border: 1px solid red; /* Facilite la visualisation 
}
```

# Problèmes rencontrés
* icone "i" déformée en mobile => ajout d'un min-width (au lieu de width) sur cet icone
* méthodo : c'était pratique de procéder par étape, cependant pour les corrections de fin de projet : une fois tout intégré il est très facile de casser 3 éléments en en modifiant un.
Il est donc important d’être encore plus méticuleux en versionnant et recettant l’ensemble
