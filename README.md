# From EggHead

## Redux
- State tree is redonding (can't modify)
- Action is the representation of the change of the data
	- need to have type property (can't be undefined)
  - ```Previous state``` + ```action``` dispatched => ```next state``` object (!== object than ```previous state```)
- We can change the ```State``` tree by dispatching an ```Action``` (JS Object)
- Component dispatch ```action```

## Pure Functions
- No side effect
- No database cause
- predictable
- given same argument -> same output
- eg create new array rather than modify it
- .map, .slice, ...

## Impure Functions
- call database, network
- side effects, operate on the DOM

__functions written in redux have to be pure__
__state mutation: 'reducer' function (pure) take previous state & action dispatched
to return next state app__

## Sample redux App

The ```Store``` is the object that brings them together. The store has the following responsibilities:

- Holds application state;
- Allows access to state via getState()```;
- Allows state to be updated via ```dispatch(action)```;
- Registers listeners via ```subscribe(listener)```;
- Handles unregistering of listeners via the function returned by - ```subscribe(listener)```.

```
const counter = ( state = 0, action ) => {
  switch ( action.type ) {
    case 'INCREMENT':
      return STATE + 1;
    case 'DECREMENT':
      return state - 1;
    default:
      return state;
  }
}

const ( createStore ) = Redux;
// import { createStore } from 'redux';

const store = createStore(counter);

const render = () => {
  document.body.innerText = store.getState();
  //initial value of app state
};

store.subscribe( render );
//.subscribe let us register a callback that will fire each time an action trigger
render();

document.addEventListener('click', () => {
  store.dispatch({ type: 'INCREMENT' })
  //.dispatch trigger an action to change app state
});
```
