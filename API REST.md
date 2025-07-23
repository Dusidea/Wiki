# API REST

## API
Une API (Application Programming Interface) est une application capable de recevoir une requête HTTP avec des méthodes HTTP, et de rendre une réponse HTTP avec un code status.

## REST
Architecture REST : Representational State Transfer.  
Souvent associée à l'architecture orientée service (Service Oriented Architecture), cette architecture est un moyen de présenter et manipuler des ressources.

- Contrainte n° 1 : Client/Server (Client-Serveur).

- Contrainte n° 2 : Stateless (sans état).

- Contrainte n° 3 : Cacheable (cachable).

- Contrainte n° 4 : Layered system (système à plusieurs couches).

- Contrainte n° 5 : Uniform interface (Interface uniforme) :

une ressource doit posséder un identifiant ;

une ressource doit avoir une représentation ;

une ressource doit être autodécrite.

- Contrainte n° 6 : Code on demand (du code sur demande).

## Evaluation : modèle de Richardson
Vous pouvez évaluer une API avec le modèle de maturité de Richardson, constitué de 4 niveaux :
- niveau 0 : marécage du Plain Old XML ;
- niveau 1 : les ressources ;
- niveau 2 : méthodes HTTP ;
- niveau 3 : contrôles hypermédia.

## Requête HTTP

Une requête HTTP émane d'un client (tout logiciel dans la capacité de forger une requête). Une requête est constituée des éléments suivants :

1. La première ligne (request line) doit contenir :

- la **méthode HTTP** (  GET  ,   POST  ,   PUT  ,   PATCH  ,   DELETE  ,   OPTIONS  ,   CONNECT  ,   HEAD  ou   TRACE  ) ;
- l**'URI**, c'est-à -dire ce qu'il y a après le nom de domaine (exemple : /users/1  ) ;
- la **version du protocole** (exemple : HTTP/1.1  ).

2. Les **entêtes** (headers), une entête par ligne, chaque ligne étant finie par le caractère spécial "retour à la ligne" (  CRLF  ).

3. Le **contenu de la requête **(body), qui doit être séparé de deux caractères spéciaux "retour à la ligne" (  CRLF CRLF  ) – optionnel.

### Méthodes HTTP

- GET  : utilisée pour récupérer des informations en rapport avec l'URI ; il ne faut en aucun cas modifier ces données au cours de cette requête. Cette méthode est dite safe (sécuritaire), puisqu'elle n'affecte pas les données du serveur. Elle est aussi dite idempotent, c'est-à-dire qu'une requête faite en GET doit toujours faire la même chose (comme renvoyer une liste d'utilisateurs à chaque fois que la requête est faite – d'une requête à l'autre, on ne renverra pas des produits si le client s'attend à une liste d'utilisateurs !) ;

- POST  : utilisée pour créer une ressource. Les informations (texte, fichier…) pour créer la ressource sont envoyées dans le contenu de la requête. Cette méthode n'est ni safe, ni idempotent ;

- PUT  : utilisée pour remplacer les informations d'une ressource avec ce qui est envoyé dans le contenu de la requête. Cette méthode n'est ni safe, ni idempotent ;

- PATCH  : utilisée pour modifier une ressource. La différence avec une requête avec la méthode PUT est que l'action à effectuer sur la ressource est indiquée dans le contenu de la requête. (modif partielle)

- DELETE  : utilisée pour supprimer une ou plusieurs ressources. Les ressources à supprimer sont indiquées dans l'URI.

## Réponse HTTP 

Une réponse HTTP émane d'un serveur (tout logiciel dans la capacité de forger une réponse HTTP). Une réponse est constituée des éléments suivants :

1. La première ligne (status line) doit contenir :
- la version du protocole utilisée ;
- le code status ;
- l'équivalent textuel du code status.

2. Les entêtes (headers), un entête par ligne, chaque ligne étant finie par le caractère spécial "retour à la ligne" (  CRLF  ).

3. Le contenu de la réponse (body) doit être séparé de deux caractères spéciaux "retour à la ligne” (  CRLFCRLF  ) – optionnel.
