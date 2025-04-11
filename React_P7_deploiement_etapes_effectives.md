# Hebergement mutualisé

1. Go to OVH > hebergement : cliquer sur mon hebergment > FTP SSH
   l'hote est la ligne copiable ftp.cluster029.hosting.ovh.net

2.

- Dans le dossier de mon projet : npm run build
- modifier la config de vite.confing.js pour ajouter le chemin du dossier dans ovh (home/dusided) => je rajoute la ligne :

```
base: "/dusided/", => NON, en fait tout est bien à la racine, c'est de la merde, laisse la valeur de base
```

- rebuild : lancer "npm run build"

3. Uploader les fichiers sur le serveur
   3.1 il faut un client FTP => je DL FileZilla client (version miniomale), j'installe. Je me connecte avec mes ID (ligne du haut du client)
   J'ai rencontré un pb de mdp => j'ai mis à jour le mdp du cluster => attendre mail de confirmation pour que le changement soit effectif
   Connexion réussie

3.2 Accède au dossier de ton site web

Si tu veux que ton site soit accessible depuis monsite.com, envoie les fichiers dans le dossier public_html/ (OVH) ou www/ (selon l’hébergeur).

Si c'est un sous-domaine ou un sous-dossier, place le contenu de dist/ dans le bon dossier.

=> une fois la co établie, à droite, je choisis le dossier www

2.3 Upload le contenu de dist/

Important : Envoie uniquement le contenu de dist et non le dossier lui-même.
📤 Envoyer les fichiers dans "www"
Côté gauche (ton PC) dans FileZilla, navigue jusqu’au dossier dist/ généré par npm run build.

Sélectionne tout le contenu de dist/ (mais pas le dossier lui-même !).

Glisse-dépose les fichiers dans "www" côté serveur.

⏳ Attends que l’upload se termine (ça peut prendre quelques minutes).

**\*\*\*\***\*\***\*\*\*\***J'ai sauté 3 et 4 des prérequis OVH, à voir\***\*\*\*\*\*\*\***

5. Une configuration Apache correcte (.htaccess pour React Router)
   Si ton app utilise React Router, ajoute ce fichier .htaccess dans www/ :

apache
Copier
Modifier
RewriteEngine On
RewriteBase /
RewriteRule ^index\.html$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.html [L]
Cela empêche les erreurs 404 en mode SPA.

note : il y avait déjà un fichier .htaccess, je l'ai remplacé

erreur MIME, là on doit récupérer un fichier JS on a en réalité de l'html

Si on essaie d’accéder directement à un fichier JS, par exemple :
🔗 https://dusidea.fr/assets/index-_eCZvA3V.js
📌 Ça affiche une page HTML au lieu de ton script JS, ce qui provoque l’erreur "Failed to load module script".

Cela signifie que ton serveur ne trouve pas les fichiers JS correctement. Voyons comment régler ça !
Modifier ton fichier .htaccess
Ajoute cette ligne avant le RewriteRule pour s'assurer que les fichiers statiques sont bien servis :

```
RewriteCond %{REQUEST_URI} !^/assets/ [NC]
```

Sans cette ligne, toutes les requêtes sont redirigées vers index.html, y compris tes fichiers .js, ce qui explique le bug. 🚀

ok j'avais un autre pb :

1. je n'aurais pas du modifier la ligne "base" dans vite.config.js car les fichiers sont bien à la racine, j'ai rétabli sa valeur précédente

```
 base: "/",
```

2. dans mon code, 2 fichiers font un fetch vers un fichier json et utilisent un chemin relatif. Il fallait un chemin absolu. Lors du build, vite gère le fait d'avoir le json à la racine du projet. J'ai donc du modifier le chemin du fetch dans logement.jsx et home.jsx => "logements.json" au lieu "../../public/logements.json"

# Déploiement sur VPS

## VPS définition
Serveur = machine (ordi)
VPS = Virtual Private server => une machine virtuelle
Le serveur a :
- un OS (en général Linux pour les serveurs de déploiement)
- une adresse unique au monde, l'IP (vs quand je fais IP config sur mon pc, c'est l'IP fournie par ma box)
Pour déployer, je communique avec le serveur avec la commande DOS. Je dois m'authentifier en SSH

## Différence déploiement VPS vs hébergement mutualisé type mon site OVH

Sur hébergement mutualisé, j'utilise un  FTP File Transfer PROTOCOL (File zilla par ex), il y a déjà un magasin, je me balade dans les rayons
Sur VPS, je gère plus globalement la logistique, il n'y a pas de rayons. Le protocole de communication c'est HTTPS


Ca fonctionne, le projet KASA est dispo sur dusidea.fr
Par contre il est à la racine, pas dans un sous dossier et donc c'est le site principal.

## Etapes
- acheter une adresse IP (à la journée)
- me connecter à cette adresse
- vérifier que le serveur marche
- installer nginx
- déployer mon projet Kasa

| Étape | Ce que tu fais |
|-------|----------------|
| 1 | Louer un VPS Ubuntu 22.04 |
| 2 | Se connecter en SSH |
| 3 | Installer Nginx |
| 4 | Déployer ton site |
| 5 | Vérifier depuis le navigateur |

### Protocoles
Voici les protocoles réseau fondamentaux impliqués dans ton projet :

| Protocole | Rôle | Exemples |
|----------|------|----------|
| **IP** (Internet Protocol) | Adresse du serveur. Identifie une machine sur Internet. | Ex: `192.168.0.1` ou `51.38.XX.XX` |
| **TCP** (Transmission Control Protocol) | Communication fiable entre deux machines. | Port 22 (SSH), port 80 (HTTP), port 443 (HTTPS) |
| **SSH** (Secure Shell) | Connexion sécurisée au terminal du VPS. | Ex: `ssh root@IP` |
| **HTTP / HTTPS** | Transfert de pages web. | Navigateur web ↔ Nginx |
| **DNS** (optionnel) | Traduit un nom de domaine vers une IP. | Ex: `mon-site.fr` → `51.38.X.X` |


J'ai créé un droplet sur Digital ocean
Avec la vps test (dans mon users > gouzi22 > ssh)
IP : 209.38.108.171

Connexion :
ssh root@TON_ADRESSE_IP -i chemin/vers/ta_clé.pem (clé privée : sans le .pub)
ssh root@209.38.108.171 -i C:\Users\gouzi\.ssh\id_ed25519_vps
1ere interaction avec le serveur on me donne son empreinte raccourcie, accepter de l'ajouter aux known hosts

The authenticity of host 'IP du serveur' can't be established. 
ED25519 key fingerprint is XXXX 
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? => oui

Connexion réussion " Welcome to Ubuntu ..."

Étape 3 : Mettre à jour le système
```
apt update && apt upgrade -y
```
En cas de conflit de configuration : keep the local version
Étape 4 : Installer Nginx
```
apt install nginx -y
systemctl start nginx
systemctl enable nginx

```
Etape 5 : Déployer le projet
- Création du dossier
mkdir -p /var/www/mon-site
mkdir -p /var/www/kasatest

Transfère tes fichiers avec scp : Depuis ton PC :
(d'abord "exit" pour quitter l'intérieur du serveur, puis cd pour arriver au dossier du code sur ma machine, ensuite =>
scp -i ~/.ssh/id_ed25519_vps -r * root@209.38.108.171:/var/www/kasatest
(ici je remets la clé car la connexion a été interrompue)
je vois des trucs qui se copient dans le terminal

Configure Nginx :
Reconnexion au serveur 
ssh -i ~/.ssh/id_ed25519_vps root@209.38.108.171

puis accède à la configuration de nginx
nano /etc/nginx/sites-available/kasatest

ajout de la config (j'utilise l'IP du serveur comme nom de serveur à la place d'un nom de domaine. Parce que flemme
```
server {
    listen 80;
    server_name 209.38.108.171;

    root /var/www/kasatest;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
Si tu veux que Nginx accepte toute requête sans vérifier un domaine spécifique, tu peux utiliser un alias générique comme _ : ( server_name _;)

Après avoir collé le texte ci dessus : CTRL+O pour enregistrer, entrée pour confirmer le nom du fichier, CTRL X pour quitter nano (l'éditeur)

Vérifier la config : nginx -t

Activer le site 
```
ln -s /etc/nginx/sites-available/kasatest /etc/nginx/sites-enabled/

```

Redémarre Nginx pour appliquer les changements :
```
systemctl restart nginx
```
Déploiement effectué, je vois bien le titre KASA mais comme avec l'hébergement mutualisé le script js ne s'execute pas (tout est blanc)
 j'ai une erreur dans la console : main.jsx:1 Failed to load module script: Expected a JavaScript module script but the server responded with a MIME type of "application/octet-stream". Strict MIME type checking is enforced for module scripts per HTML spec.

Tu dois t'assurer que Nginx sert correctement les fichiers JavaScript avec le bon type MIME.
je modifie la config ngnix notamment pour avoir text/javascript js; (attention à ne pas avoir 2 ligne avec la même extension )
je redémarre nginx

J'ai du modifier la configuration nginx et notamment les chemins
  GNU nano 8.1                                                                               /etc/nginx/sites-available/kasatest
 server {
    listen 80;
    server_name 209.38.108.171;

  root /var/www/kasatest/dist;


    index index.html;

    location / {
        try_files $uri /index.html;
    }

location /assets/ {
        try_files $uri =404;  # S'assurer que les fichiers JS et CSS dans /assets sont bien servis
    }

    types {
        application/javascript js jsx;
        application/json json;
        text/css css;
        text/html html;
        image/png png;
        image/jpeg jpeg jpg;
        image/gif gif;
        application/font-woff2 woff2;
        application/font-woff woff;
    }
}


