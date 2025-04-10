# Pourquoi optimiser ?
Rapidité de chargement
Meilleur référencement  => trafic
Accessibilité => inclusion

# Outils d'audits
- Lighthouse intégré à Chrome : inspecter > Lighthouse (si pas visible directement, cliquer sur les 3 ... à droite) => audit global (performance, SEO, accessibilité, bonnes pratiques)
- L'extension Wave pour l'accessibilité
- Pour le référencement spécifiquement :
  - https://www.outiref.fr
  - https://pagespeed.web.dev/?hl=fr
  - https://gtmetrix.com 
  - SEOQuake
  - référencement local (Géographie, coiffeur à toulouse) : https://search.google.com/test/rich-results => prévisualiser les résultats enrichis (tags schema.org)

# Performance

## Format des images
- formats AVIF et WEBP > jpg/png (plus compressé et optimisé)
- la taille des images compte également, plus une image est grande (en pixels) plus elle est lourde > donc éviter d'appeler une image de 4 000 px de large pour un affiche en 500px
- Redimensionner les images : perte de qualité nécessaire (sinon on ne gagne pas sur le poids) mais proportionnelle au changement de taille => ex passer de 4 000 à 500 px produira une trop grande perte de qualité
### Tuto Gimp :
  - ouvrir l'image avec Gimp
  - Menu Image > Echelle et taille de l'image
    - Réduire la largeur (garder l'option par défaut de conserver les proportions)
    - Qualité > Interpolation : (chatGPT m'a conseillé NoHalo pour mes images)
    - Valider en cliquant sur Mise à l'échelle
  - Fichier > Exporter sous :
    - en bas, déplier le menu "Sélectionner le type de fichier"
    - choisir WebP ou Avif selon le besoin
    - Valider avec le bouton "Exporter"
    [Ouverture de la popup "Exporter l'image come WebP")
    - Image quality : 75% (ratio qui combine une compression significative avec perte raisonnable de la qualité)
    - Valider avec l'autre bouton "Exporter"

  ## Render Blocking resources > voir dans la balise head de l'html
   - Différer le chargement des scripts non nécessaires au 1er chargement avec "defer" ou "async) et les décaler en fin de balise body si besoin
   - Précharger les css et images (preconnect, preload)

  ## Coverage
Minifier les fichiers pour les rendre plus léger (suppression des espaces inutiles pour la machine, moins de caractères)
Identifier le % des fichiers non utilisés (attention parfois une partie du fichier est inutile au lancement mais utile ensuite via un script) :
- Inspecteur du navigateur > Sources : sélectionner un fichier et au niveau de console choisir coverage (possible commande à lancer dans la console pour rendre "coverage" visible)
- Nettoyer les fichiers : PurgeCss pour retirer le css inutile (au 1er chargement ???)
  Installe PurgeCSS
  ```
  npm install -g purgecss
  ```
  Exécute PurgeCSS sur ton fichier Bootstrap
  ```
  purgecss --css assets/bootstrap/bootstrap.css --content index.html assets/**/*.js --output assets/bootstrap/clean-bootstrap.css
  ```
  - PurgeCSS scanne index.html et tous les fichiers .js du dossier assets/
  - Il supprime les classes CSS non utilisées
  - Il génère un fichier propre clean-bootstrap.css
  - Il faut ensuite remplacer le fichier appelé dans index.html par le fichier généré ET BIEN TESTER SI LE STYLE DE LA PAGE A ETE MODIFIE (si oui, on a supprimé des classes utiles !!)
  - Essayer d'identifier les classes utiles qui ont été supprimées et les white lister de l'outil purge (faillible)
  - PurgeCSS réduit déjà énormément le CSS, mais pour optimiser encore plus le First Paint, on peut extraire les styles critiques (ceux visibles immédiatement) grâce à Critical


# Référencement

## Utilisation des balises sémantiques

# Accessibilité
- micro données; ref local
- tuto redimensionner des images



