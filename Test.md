# Types de test

## 1. Tests unitaires : 
Très bas niveau, près de la source de votre application. Ils consistent à tester les méthodes et fonctions individuelles des classes, des composants ou des modules utilisés par votre logiciel. => index.test.js
## 2. Tests d'intégration : 
vérifient que les différents modules ou services utilisés par votre application fonctionnent bien ensemble. Par exemple, ils peuvent tester l'interaction avec la base de données ou s'assurer que les microservices fonctionnent ensemble comme prévu. 
## 3. Tests fonctionnels : 
se concentrent sur les exigences métier d'une application. Ils vérifient uniquement la sortie d'une action et non les états intermédiaires du système lors de l'exécution de cette action.
## 4. Tests de bout en bout : 
reproduisent le comportement d'un utilisateur avec le logiciel dans un environnement applicatif complet. Ils vérifient que les différents flux d'utilisateurs fonctionnent comme prévu et peuvent être aussi simples que le chargement d'une page Web ou la connexion. Des scénarios beaucoup plus complexes peuvent aussi vérifier les notifications par e-mail, les paiements en ligne, etc.
## Confusion possible => Différence tests d'intégration vs fonctionnels : 
un test d'intégration peut vérifier que vous pouvez interroger la base de données, tandis qu'un test fonctionnel s'attend à obtenir une valeur spécifique de la base de données

# Outils

## React script "test"
Si présent dans package.json dans scripts > Test
Va lancer tous les fichiers appelés nomDuFichierDuComposant.test.js (sur le composant dans le fichier nomDuFichierDuComposant.js)

## Jest
Jest, script test ?

## Commandes de test 

