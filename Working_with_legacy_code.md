# Prerequis
Check dans les readme les versions requises

# Versions de node.js 
Outil de gestion de versions : NVM
 
 1. Installer nvm pour Windows :
- Télécharge l’installeur ici : https://github.com/coreybutler/nvm-windows/releases
- Prends le fichier nvm-setup.exe et installe-le.
- Une fois installé, ouvre Git Bash ou PowerShell.
2. Changer de version de Node :
```
nvm install 18.18.2   # par exemple, installe la version souhaitée
 ```
 ```
nvm use 18.18.2       # utilise cette version
 ```
vérifier la version active avec : 
 ```
node -v
 ```
Pour voir toutes les versions installées : 
 ```
nvm list
 ```

# Cohérence des versions

Selon la version de node utilisée, la version de npm doit s'adapter, toutes les versions ne sont pas compatibles entre elles

## Comment connaitre la compatibilité ?

- https://nodejs.org/en/about/previous-releases => voir le tableau Looking for the latest release of a version branch?
- Avec NVM :
Si tu utilises nvm, tu peux demander directement quelle version de npm vient avec une version donnée :
```
nvm install 16.14.1
nvm use 16.14.1
npm -v
```
