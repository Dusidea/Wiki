**HTML** HyperText Markup Lnanguage, langage de balises pour créer la structure d'une page web

**CSS** Cascading Style Sheets, feuilles de style en cascade : décrit la présentation d'un doc HTML (ou XML)

validation du W3C pour HTML et CSS 

**Frameworks** CSS : Tailwind, Bootstrap, Foundation

## HTML vs CSS: 
* Le HTML constitue la structure d'une page web.
* Le CSS permet d'ajouter du style.
* Les deux langages se complètent avec un rôle bien défini pour chacun.
* Le navigateur est un logiciel qui permet de lire les langages du Web : HTML et CSS.
* Tous les navigateurs embarquent des outils de développement, dont l'outil d'inspection qui permet d'accéder au HTML et au CSS d'une page.

## HTML Basics:
* Pour créer une page web, on crée un fichier ayant l'extension  .html  , qui pourra être ouvert dans le navigateur web simplement en faisant un double-clic dessus.
* Chaque fichier HTML est constitué de balises.
* Les balises peuvent avoir plusieurs formes :
	* <balise> </balise>  : balises en paires, elles s'ouvrent et se ferment pour délimiter le contenu (début et fin d'un titre, par exemple) ;
	* <balise>  : balises orphelines (on ne les insère qu'en un seul exemplaire), elles permettent d'insérer un élément à un endroit précis (par exemple une image).
* Les balises sont parfois accompagnées d'attributs pour donner des indications supplémentaires, ou paramétrer un élément (exemple :  <img src="photo.jpg">  ).
* Une page web est constituée de deux sections principales : l'en-tête<head> </head>  dont le contenu n'apparaît pas dans l'affichage de la page et le corps <body> </body>  qui, lui, apparaît.


## Syntaxe CSS
CSS : sélecteur {
		propriété : valeurs ;
		}
ex : p {
		color : blue;
	}

## Intégrer le CSS
* CSS est un autre langage qui vient compléter le HTML. Son rôle est de mettre en forme votre page web.
* Pour écrire le code CSS, on crée un fichier séparé portant l'extension .css  comme style.css.
* Pour lier les fichiers CSS et HTML, on rajoute une ligne dans la balise <head> </head> du fichier HTML :  <link href="style.css" rel="stylesheet"> pour indiquer au navigateur d'aller chercher la feuille de style (stylesheet en anglais) afin d'afficher la page web avec les propriétés de style qu'on lui a appliquées.
* En CSS, on sélectionne les portions de la page HTML qu'on veut modifier, et on change leur présentation avec des propriétés CSS



Il existe plusieurs façons de sélectionner la portion de page que l'on veut mettre en forme. Par exemple, on peut viser :
 * toutes les balises d'un même type, en écrivant simplement leur nom (h1 par exemple) ;
* certaines balises spécifiques, auxquelles on a donné des noms à l'aide des attributs class ou id(.nom-classe ou #nom-id) ;
* uniquement les balises qui se trouvent à l'intérieur d'autres balises (h3,em).

### Spécificité 
- Style dans l'html >
- Sélecteur d'identifiant # >
- Classes, pseudo classes et attributs > ?
- Type/élément  (p, img, etc)
- Sélecteur universel *
  => attention il y a un cumul, si dans un sélecteur j'ai un ID + une classe cela cumule les prio


##Modifier l’apparence du texte : 
* On modifie la taille du texte avec la propriété CSS **font-size**.
* On peut indiquer la taille en pixels, comme 16px ; ou encore en “em”, comme 1.3em.
* On indique la police du texte avec la propriété CSS  **font-family** . 
* De nombreuses propriétés de mise en forme du texte existent : 
	* **font-style** pour l'italique, 
	* **font-weight** pour la mise en gras, 
	* **text-decoration** pour le soulignement.
* Le texte peut être aligné avec la propriété CSS **text-align**  .

##Ajouter de la couleur et un fond

* On change la 
	* **couleur du texte** avec la propriété  **color**  et 
	* la **couleur de fond** avec la propriété **background-color**.
* On peut indiquer une couleur en écrivant 
	* son **nom en anglais**, black  par exemple, 
	* sous forme **hexadécimale**, comme  #FFC8D3, 
	* ou en notation **RGB**, comme  rgb(250,25,118).
* On peut ajouter une image de fond avec la propriété  **background-image**. On peut choisir de fixer l'image de fond, ou encore de la positionner où on veut sur la page.
* On peut rendre une portion de la page transparente avec la propriété  **opacity**  ou avec la notation  **RGBA** (une extension de la notation RGB, où la quatrième valeur indique le niveau de transparence).

##Créez des bordures et des ombres
* On peut appliquer une bordure à un élément avec la super-propriété CSS  **border**. Il faut indiquer 
	* la largeur de la bordure, 
	* sa couleur 
	* et son type (simple, double, pointillés, tirets).
* On peut arrondir les bordures avec la propriété CSS  **border-radius**.
* On peut ajouter une ombre aux blocs de texte avec  **box-shadow.** On doit indiquer 
	* le décalage vertical et horizontal de l'ombre, 
	* son niveau d'adoucissement 
	* et sa couleur.
* Le texte peut lui aussi avoir une ombre avec  **text-shadow.**

##Créez des apparences dynamiques
* En CSS, on peut modifier l'apparence de certaines sections dynamiquement, après le chargement de la page, lorsque certaines **interactions** se produisent. On utilise pour cela les pseudo-classes.
* La pseudo-classe  **:hover**   modifie l'apparence d'un élément au **survol** (par exemple : a:hover  modifie l'apparence des liens hypertextes lorsque la souris pointe dessus).
* La pseudo-classe  **:active**  modifie l'apparence des liens hypertextes au moment du **clic.**
* La pseudo-classe **:visited** modifie l'apparence des liens hypertextes lorsqu'un lien a **déjà été visité**.
* La pseudo-classe  **:focus**  modifie l'apparence d'un élément **sélectionné via la touche "tab"**.
* Encore aujourd'hui, certaines propriétés ne sont pas totalement reconnues par tous les navigateurs.


##Conventions de nommage
Pour le nommage des classes, tout se fait en minuscule, un tiret en guise de séparateur pour les noms composés que ce soit un bloc, un élément ou un modificateur.

Ensuite, deux underscores devant le nom de notre élément et deux tirets devant le modificateur ?

[OCSS&BEM](https://www.alsacreations.com/article/lire/1641-Bonnes-pratiques-en-CSS--BEM-et-OOCSS.html)
###OCSS:  (Object Oriented CSS)

###BEM : Block-element-modifier

* Block : Standalone entity that is meaningful on its own.
Examples : header, container, menu, checkbox, input

* Element : A part of a block that has no standalone meaning and is semantically tied to its block.
Examples : menu item, list item, checkbox caption, header title

* Modifier : A flag on a block or element. Use them to change appearance or behavior.
Examples ; disabled, highlighted, checked, fixed, size big, color yellow


## Problèmes courant
### Forcer un élément à prendre toute la hauteur disponible
 (same pour largeur)
-  min-height: 100vh; 

