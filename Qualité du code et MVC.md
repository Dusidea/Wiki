# Qualités d'un code professionnel
- **Modulaire** : découpé en de nombreux fichiers, où chaque fichier a un rôle et un seul à la fois.
- **Découplé** : les fichiers sont conçus pour fonctionner indépendamment les uns des autres.
- **Documenté** : la documentation prend généralement la forme de commentaires spéciaux placés au-dessus des méthodes et classes publiques, pouvant être réutilisées dans d'autres projets. On peut générer automatiquement une page web de documentation à partir de ces commentaires.
- en **anglais**
- **clair** :  respecter les normes de formattage (ex PSR 12 pour PHP)

# Avantages
- **réutilisable** : si un jour nous avons codé un fichier utile, nous pouvons nous en resservir dans un autre projet ou dans un autre endroit du même projet. On gagne du temps en n'ayant pas à tout refaire à chaque fois !
- **collaboration facilitée** :  chaque fichier étant indépendant (et généralement de petite taille), on peut travailler en équipe de 5, 10, voire 100 personnes sur un même projet. Si tout était mélangé dans un seul et même gros fichier, il serait impossible de le modifier en même temps !
- **évolutif** : quand quelqu'un vient vous demander une nouvelle fonctionnalité, il est facile de l'ajouter. Vous n'avez pas peur de tout casser, car vous avez même la possibilité de créer des tests automatisés.

En résumé, on peut donc gagner du temps, travailler à plusieurs et ajouter des fonctionnalités facilement sans (presque) jamais causer des bugs.

# Bonnes pratiques cosmétiques
- Il est recommandé de garder uniquement la balise ouvrante<?php  dans les fichiers qui contiennent seulement du PHP. Ceux qui contiennent aussi du HTML ne changent pas.
- La syntaxe des "short open tags" peut être utilisée pour avoir des gabarits d'affichage plus concis.
- En tant que développeur PHP, vous êtes aussi responsable de la bonne gestion de la base de données. Vous pouvez la traiter comme votre code : des noms clairs, de l'anglais…

# Modèle Vue Controleur
- **Modèle** : cette partie gère ce qu'on appelle la **logique métier** de votre site. Elle comprend notamment la gestion des données qui sont stockées, mais aussi tout le code qui prend des décisions autour de ces données. Son objectif est de fournir une interface d'action la plus simple possible au contrôleur. On y trouve donc entre autres des algorithmes complexes et des requêtes SQL.
- **Vue** : cette partie se concentre sur l'**affichage**. Elle ne fait presque aucun calcul et se contente de récupérer des variables pour savoir ce qu'elle doit afficher. On y trouve essentiellement du code HTML mais aussi quelques boucles et conditions PHP très simples, pour afficher par exemple une liste de messages.
- **Contrôleur** : cette partie gère les **échanges** avec l'utilisateur. C'est en quelque sorte l'intermédiaire entre l'utilisateur, le modèle et la vue. Le contrôleur va recevoir des requêtes de l'utilisateur. Pour chacune, il va demander au modèle d'effectuer certaines actions (lire des articles de blog depuis une base de données, supprimer un commentaire) et de lui renvoyer les résultats (la liste des articles, si la suppression est réussie). Puis il va adapter ce résultat et le donner à la vue. Enfin, il va renvoyer la nouvelle page HTML, générée par la vue, à l'utilisateur.

- 
