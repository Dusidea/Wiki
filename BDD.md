# SGBD

- Une base de données est un outil qui stocke vos données de manière organisée et vous permet de les retrouver facilement par la suite.
- On communique avec MySQL grâce au langage SQL. Ce langage est commun à tous les systèmes de gestion de base de données (avec quelques petites différences néanmoins pour certaines fonctionnalités plus avancées).
- Donner les ordres au Système de Gestion de Base de Données (SGBD) en langage SQL
- PHP fait l'intermédiaire entre vous et MySQL.(d'autres langages peuvent jouer ce rôle)
## BDD <> Armoire
BDD : imaginons une base de données comme une armoire
- L'armoire est appelée "**la base**" dans le langage SQL. C'est le gros meuble dans lequel les secrétaires ont l'habitude de classer les informations.
- Dans une armoire, il y a plusieurs tiroirs. Un tiroir, en SQL, c'est ce qu'on appelle** "une table"**. Chaque tiroir contient des données différentes. Par exemple, on peut imaginer un tiroir qui contient les pseudonymes et informations sur vos visiteurs, un autre qui contient les messages postés sur votre forum, etc.
- Mais que contient une table ? C'est là que sont enregistrées les données, sous la forme d'un tableau. Dans ce tableau, les colonnes sont appelées **des "champs"**, et les lignes sont appelées **des "entrées"**.

# SQL
## Connexion
Avant de dialoguer avec MySQL, il faut s'y **connecter**. On a besoin
- de l'adresse IP de la machine où se trouve MySQL,
- du nom de la base de données 
- d'un identifiant 
- d'un mot de passe

## Requête
- SELECT récupérer des informations dans une base de données.
- FROM : indique la table appelée
- WHERE : critère de sélection
- ORDER BY : tri
- LIMIT : limiter le nb de résultats

### Requêtes de modification
- INSERT INTO : ajout d'une entrée ;
- UPDATE : modification d'une ou plusieurs entrées ;
- DELETE : suppression d'une ou plusieurs entrées.
Lorsqu'on utilise UPDATE  ou DELETE , il faut penser à filtrer avec un WHERE , sinon toute la table sera affectée par l'opération !

# Grouper les données
MySQL permet d'exécuter certaines fonctions lui-même, sans avoir à passer par PHP. Ces fonctions modifient les données renvoyées.
Il existe deux types de fonctions :
- Les fonctions scalaires : elles agissent sur chaque entrée récupérée. Elles permettent par exemple de convertir tout le contenu d'un champ en majuscules, ou d'arrondir chacune des valeurs.
- Les fonctions d'agrégat : elles effectuent des calculs sur plusieurs entrées pour retourner une et une seule valeur. Par exemple : calcul de la moyenne, somme des valeurs, comptage du nombre d'entrées…

On peut donner un autre nom aux champs modifiés par les fonctions, en créant des alias à l'aide du mot-clé AS .

Lorsqu'on utilise une fonction d'agrégat, il est possible de regrouper des données avec GROUP BY .

Après un groupement de données, on peut filtrer le résultat avec HAVING . Il ne faut pas le confondre avec WHERE qui filtre avant le groupement des données.





