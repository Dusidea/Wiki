# Acronymes
**SASS** Syntactically Awesome Style Sheets
**SCSS** Sassy CSS

# Compilation
Compilation nécessaire dans un terminal : 
sass .\SASS\main.scss .\public\main.css
commande : [sass] [chemin du fichier main.scss] [chemin du fichier généré main.css]
=> en sortie un fichier main.css vers lequel les fichiers HTML vont pointer
<link rel="stylesheet" href="public/main.css">

# Structure
**Nesting**
**&_**
modules, fichiers partiels 
@use (ex @import) pour appeler les fichiers partiels (commençant par "_") dans le fichier main.scss
Pattern 7.1 pour structurer les fichiers SASS https://louisetiennegirard.fr/blog/structurez-sass-avec-le-systeme-7-1
