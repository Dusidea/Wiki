# Pourquoi optimiser ?
Perf : Rapidité de chargement + fluidité
SEO : Meilleur référencement  => trafic
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
### Tester le coverage
Identifier le % des fichiers non utilisés (attention parfois une partie du fichier est inutile au lancement mais utile ensuite via un script) :
- Inspecteur du navigateur > Sources : sélectionner un fichier et au niveau de console choisir coverage (possible commande à lancer dans la console pour rendre "coverage" visible)
### Purge & Critical
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
- Veiller à avoir les balises de base (header/footer Nav et Main) telles quelles et non une div de class = "header" par exemple => https://ronan-hello.fr/series/html/balises-semantiques-html
- Title : définit le titre de votre page web qui apparaît dans les résultats de recherche. accrocheur qui décrit de manière concise le contenu de votre page. Reco max char : 55
- Meta Description : fournit une courte description de votre page web qui apparaît dans les résultats de recherche => informative et accrocheuse pour inciter les utilisateurs à cliquer sur votre lien.  Reco max char : 160

## Référencement local

Ensemble des techniques qui participent à positionner favorablement un site web ou la fiche établissement Google My Business d'une entreprise, parmi les premiers résultats de recherches dites locales à travers Google et les pages de résultats d'autres moteurs de recherche (SERP). => se positionner sur les résultats de recherche de type "ouvert maintenant à proximité" 

### Caser le nom de la ville et le type de business dans le titre
### Micro données

Les microdonnées sont une forme de balisage HTML (comme itemprop, itemscope, itemtype) qui permet d’ajouter des données structurées à une page web.
Elles sont utilisées pour expliquer aux moteurs de recherche ce que signifient les contenus d’une page : par exemple, qu’un nom est celui d’une personne, qu’un horaire est celui d’un magasin, etc.

### Résultats enrichis (rich results ou rich snippets)
Les résultats enrichis sont les effets visibles que ces données peuvent déclencher dans les résultats de recherche Google.
Par exemple :
- une fiche de personne avec sa photo
- une carte avec les horaires d’un commerce
- des étoiles de notation pour un produit

L'outil https://search.google.com/test/rich-results (version URL ou Code) permet de prévisualiser les microdonnées identifiées pour les résultats enrichis

# Accessibilité
https://www.w3.org/WAI/fundamentals/accessibility-intro/fr
Rendre le web accessible est un avantage pour les internautes, les entreprises et la société. Les standards du web internationaux définissent ce qui est nécessaire pour l’accessibilité.  => Inclusion handicap
Normes existantes pour s'assurer :
- de la lisibilité avec un handicap visuel
- de la navigation et interpretation claire avec un logiciel audio pour les malvoyants par ex

## Standards
L’Initiative pour l’accessibilité du Web, Web Accessibility Initiative du W3C (WAI (en anglais)) développe des spécifications techniques, des règles, des techniques et ressources d’accompagnement qui décrivent des solutions d’accessibilité. Elles sont considérées comme des normes internationales pour l’accessibilité du web ; par exemple, WCAG 2.0 est aussi une norme ISO : ISO/IEC 40500.

## Balises
- Avoir un titre de document
- Intégrer l'attribut "lang" dans la balise html pour signaler la langue du doc
- S'assurer d'avoir des labels sur les champs de formulaires, alt sur les images, title sur les liens
## Organisation
- Structure : respecter la hiérarchie h1 > H2 > H3 etc,
-  attention aux structures horizontales puis verticales (ex Navigation : Heading elements are not in a sequentially-descending order)

## Visibilité 
- Contraste : respecter un contraste minimal entre un texte et son fond
