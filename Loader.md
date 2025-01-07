
//************* HOMEPAGE : LOADER******************
@keyframes fadeout{
  0% {
    opacity: 1;
    display: flex;
    visibility: visible;
    pointer-events: auto;
  }
  50% {
    opacity: 0.5;
    display: flex;
    visibility: visible;
    pointer-events: auto;
  }
  100% {
    opacity: 0;
    // même si opacité 0, l'objet prend toujours toute la page et tourne en continu 
    // display none simule la disparition du bloc (fin de la ressource chargement aussi ?)
    // Plus de rendu graphique : Les ressources GPU ne sont plus utilisées pour dessiner le loader (ce qui est significatif pour des animations).
    // Moindre charge CPU : Aucune mise à jour visuelle n’est nécessaire.
    // Ressources associées : Les styles SCSS/CSS, le code HTML, et les références dans le DOM sont encore là. Cela ne devient "gratuit" qu'après une suppression réelle du DOM (via JavaScript).
    display: none;
    // Pour firefox, display none ne suffit pas, j'ajoute donc les propriétés visibility et pointer-events
    visibility: hidden;
    pointer-events: none; 
  }
}

@keyframes spin {
    to {
      transform: rotate(360deg);
    }
}

@use '../Utils/variables' as var;
@use '../Utils/keyframes';
@use '../Utils/maps' as maps;
@use '../Utils/mixins';

.loader {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(255, 255, 255, 0.9);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 9999;
    animation: fadeout 4000ms ease-out forwards;
    opacity: 0;
    pointer-events: none;
    visibility: visible;

    &__icon {
        color: var.$button-purple;
        font-size: 50px;
        animation: spin 1s linear infinite;
        position: fixed;
        top: 0;
        left: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        height: 100%;
    }

}
