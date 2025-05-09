# API
- API Application Programming Interface => système qui permet à l'application d'interagir avec d'autres programmes selon une méthode définie à l'anvance
=> C’est ce qu’on appelle une abstraction : une façade qui simplifie des mécanismes complexes permettant de fournir un service demandé.
Un front est une API, qui fournit du HTML en sortie, alors que pour du back on fournit des données (en json par ex)

# Service web
- SERVICE WEB permet de manipuler les données qu’il expose à travers son API en ligne => persistance des données. Il peut
=> les créer POST ,
=> les récupérer GET ,
=> les mettre à jour PUT
=> et les supprimer DELETE
 
# CLIENT 
client serveur désigne l'application web dont l'utilisateur se sert

# SERVEUR : 
"Programme informatique" qui met les services web à disposition des autres programmes.
1 machine, 1 ordinateur capable de recevoir et d'envoyer des requêtes HTTP (ou TCP)
Il possède : 
- une adresse unique au monde : IP / LocalHost
- plusieurs points d'entrée : ports (ex 3001)

Le serveur est joignable à une adresse (IP+ PORT). 
Le navigateur et le serveur doivent  communiquer entre eux grâce au protocole HTTP.
Donc une requête : HTPPs/IP/port (un domaine hébergé sur un serveur va avoir l'ip du serveur correspondant)

# HTTP
-  HTTP : hypertext transfer protocol est un protocole (ensemble de règles) de communication client-serveur développé pour le World Wide Web. HTTPS est la variante sécurisée par le chiffrement et l'authentification.

# Exemple d'adresse web :
- Nom de domaine (ou adresse IP) (localhost:)
-  port : 8081 (serveur : localhost:8081
-  chemin de la ressource /chemin

 
# Back / Front dans tout ça
1 serveur peut héberger autant de backs et fronts qu'on veut, chacun aura son propre port
1 machine possède au moins 65K ports


