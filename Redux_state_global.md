# Redux
 is a library for managing global application state => 
 Pourquoi une gestion du state global ?

Besoin de partager un même state à plusieurs composants, or un state est local et transmettable par le parent uniquement. On peut faire remonter d'un niveau mais cela complique pas mal les choses.


 
- Redux is typically used with the **React-Redux library** for integrating Redux and React together
- **Redux Toolkit** is the standard way to write Redux logic

# Logic

Redux's update pattern separates "what happened" from "how the state changes"
- **Actions** are plain objects with a type field, and describe "what happened" in the app
- **Reducers** are functions that calculate a new state value based on previous state + an action
A Redux store runs the root reducer whenever an action is dispatched

## Actions
event that describes something that happened in the application. Type field = string
Naming:  string like "domain/eventName", where the first part is the feature or category that this action belongs to, and the second part is the specific thing that happened. other fields with additional information about what happened (payload)

## Action creators
function that creates and returns an action object

## Reducers
function that receives the current state and an action object, decides how to update the state if necessary, and returns the new state: (state, action) => newState. Similar as an event listener which handles events based on the received action (event) type.

## Store
The current Redux application state lives in an object called the store . The store is created by passing in a reducer, and has a method called getState that returns the current state value
## Dispatch
The Redux store has a method called dispatch. The only way to update the state is to call store.dispatch() and pass in an action object. The store will run its reducer function and save the new state value inside, and we can call getState() to retrieve the updated value

## Slices
- Utiliser les **slices** nous permet de découper le store en plusieurs parties.
- Chaque slice est typiquement associé à une fonctionnalité spécifique de l'application, organisée dans des dossiers séparés.
- _createSlice_ génère automatiquement des reducers, des actions, et des action creators à partir d'un objet définissant l'état initial et les fonctions réductrices.
- Elle nous épargne la nécessité de créer nos actions.

## Selectors
- Utiliser les **selectors** nous permet de réécrire les accès au state dans chacun de nos composants.
- _useSelector_  est un **hook** qui permet à la fois d’utiliser nos selectors et de connecter le composant aux changements du store.  
Selectors are functions that know how to extract specific pieces of information from a store state value. As an application grows bigger, this can help avoid repeating logic as different parts of the app need to read the same data:


## Composants et état partagé

- Partager les données du state revient à brancher chaque composant au store.
- Cela permet de gérer l'état de l'application de manière cohérente et centralisée à travers différents composants.
- Les composants peuvent interagir avec le store en dispatchant des actions.
- Le mécanisme est identique, qu’il s’agisse d’une application React ou non.    


# Architecture
- nous stockons un **état général** dans ce qu’on appelle des **stores** ;
- les **composants** qui ont besoin d’une valeur de ce state viennent **consulter le store** et **s’abonner aux changements** de ce state ;
- le store possède un mécanisme qui à chaque changement du state, **va informer chaque composant abonné qu’un changement a eu lieu **;
- chaque composant peut alors** relire le contenu du state et mettre à jour son état local**

# Flow
## Redux uses a "one-way data flow" app structure
- State describes the condition of the app at a point in time, and UI renders based on that state
- When something happens in the app:
  - The UI dispatches an action
  - The store runs the reducers, and the state is updated based on what occurred
  - The store notifies the UI that the state has changed
- The UI re-renders based on the new state

 ## Initial Setup
 - A Redux **store** is created using a** root reducer function**
- The store calls the root reducer once, and saves the return value as its initial _state_
- When the UI is first rendered, UI components access the current state of the Redux store, and use that data to decide what to render. They also subscribe to any future store updates so they can know if the state has changed.

 ## Updates
- Something happens in the app, such as a user clicking a button
- The app code dispatches an action to the Redux store, like dispatch({type: 'counter/increment'})
- The store runs the reducer function again with the previous state and the current action, and saves the return value as the new state
- The store notifies all parts of the UI that are subscribed that the store has been updated
- Each UI component that needs data from the store checks to see if the parts of the state they need have changed.
- Each component that sees its data has changed forces a re-render with the new data, so it can update what's shown on the screen

# Utiliser Redux dans un projet
Possibilité d'installer les paquets Redux pour react 
```
npm install @reduxjs/toolkit
```
If you need React bindings:
```
npm install react-redux
```
ou d'utiliser le toolkit et générer une app redux avec la structure adaptée

## React Toolkit
The recommended way to start new apps with React and Redux Toolkit is by using our official Redux Toolkit + TS template for Vite, or by creating a new Next.js project using Next's with-redux template.
```
npx degit reduxjs/redux-templates/packages/vite-template-redux my-app

```

## structure des fichiers

Chaque composant a un sous dossier à son nom (généralement dans le dossier feature). Dans le dossier du composant on a composant.jsx et composantSlice.js
Dans le dossier app on créera le store.js qui va configurer le store et appeler les reducers

## Documentation

https://redux-toolkit.js.org/introduction/getting-started#using-create-react-app
https://redux.js.org/tutorials/essentials/part-1-overview-concepts
https://redux.js.org/tutorials/fundamentals/part-1-overview

