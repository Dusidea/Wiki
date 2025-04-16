# Outils principaux
- La **console** est un environnement interactif où vous allez pouvoir créer des variables et des fonctions, exécuter du code ou afficher des informations sur l’état de votre application.
- L’**inspecteur** vous permet de consulter votre HTML et votre CSS. Vous pourrez modifier votre code HTML (en ajoutant des classes par exemple) mais aussi activer et désactiver des règles CSS.
- Le **débogueur** vous permet de suivre le déroulement de votre code étape par étape grâce à des breakpoints (ou points de rupture). À chaque breakpoint, votre code se stoppe et vous permet de consulter l’état de votre application.
  - outils de dev de **Firefox**
  - extension pour **vscode** à configurer depuis Vscode (pour chrome) :
    -   /!\ bien veiller à lancer l'app avant de lancer le debug (dans le terminal npm start ou yarn start, selon le cas)
    -   dans vs code, menu de gauche, cliquer sur run and debug (flèche play avec insecte)
    -   cela ouvre un fichier de config, le modifier comme suit
   
    ```
          {
      "version": "0.2.0",
      "configurations": [
        {
          "type": "chrome",
          "request": "launch",
          "name": "Launch Chrome aginst localhost",
          "url": "http://localhost:3000/",
          "webRoot": "${workspaceFolder}/src"
        }
      ]
    }
    ```

    - en bas de vs code cliquer sur le meme symbole et choisir de lancer [nom que vous avez choisi dans la config)
- L’onglet **Network** (ou réseau en français) est utilisé tant pour analyser des requêtes HTTP que pour optimiser le chargement de votre site.

# Logique
1. observer et théoriser
2. écrire un test répétable (comment reproduire le bug ?)
3. élaborer et tester sa téhorie
4. modifier le code (et retester ?)
