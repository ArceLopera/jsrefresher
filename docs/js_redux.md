# Intro to Redux

## State Management

In the real world with larger scale applications, we might have to pass down the state data multiple levels to get to the desired component.

Having to pass down data to multiple levels of nested components would make it hard to understand what caused a change to the state, as there might be multiple potential components that can change the state.

This would also cause a lot of redundant code, make it hard to maintain and debug the code.

Redux was created to make state management predictable, providing a single state container and strict rules on how state can be changed.

Redux is a small JavaScript library and can be used with any front-end framework, such as React, Angular, jQuery.

It employs the "single source of truth" pattern.
In short, single source of truth just refers to relocating the application state and all associated logic outside of the application, allowing ANY component to access the data it needs.
Having a single state container makes it easier to manage the state of your application, as you can access and change the data from any component that needs it, without having to pass down the data.

## Core Concepts

**Single source of truth**
The global state of the app is stored in a single store.

**State is read-only**
You can change the state only by dispatching actions. Action are objects, that contain information about what should be changed.

**Pure reducers**
Reducers are functions that handle the actions and return the next state of the application. Reducers need to be pure, meaning they cannot modify the state, they need to return a new state object.



### Store

In Redux, the application's state is stored as a simple object, called store.
There should only be a single store in an app.

For example, a store can look like this:

```js
{
  contacts: [{
    name: 'David'
  }, {
    name: 'Amy'
  }],
  toggle: true
}
```


You cannot change the state directly. Instead, you need to dispatch an action.

### Actions & Reducers

An action is just a plain JavaScript object:

```js
{ 
  type: 'ADD_CONTACT', 
  name: 'James' 
}
```

The code above defines an action with type `ADD_CONTACT` and a name property.

An action clearly describes why the state change happened, and can be dispatched from anywhere in your app.

At this point we just have a store, which includes our state data and an object, that includes some data that needs to be changed in the state. So, how do we actually do the change?
To tie the store and the action together, we need to write a function, called a reducer.
It takes state and action as arguments, and returns the next state of the app.

For example:

```js
function contactsApp(state, action) {
  if (action.type === 'ADD_CONTACT') {
    return [ ...state,  action.name ]
  } else {
    return state
  }
}
```

The code above defines a simple reducer function, that checks the action and returns the new state.

These concepts are basically the idea of Redux: you hold the global state in a store, define actions to describe what to change in the store and write reducer functions to handle those actions.
Notice, we have not touched any React specific syntax, all of the above is plain JavaScript.

#### Action Creators

In order to use the same action with different payloads, as well as create reusable code, we can create Action creators.

Action creators are simple functions that return actions.

For example:

```js
function addContact(person) {
  return {
    type: 'ADD_CONTACT',
    payload: person
  }
}
```


The action creator function takes a person parameter and uses that as the actions payload.
Now, we can use the action creator to create multiple new contacts by passing it the corresponding data.
Action creators are not built into the Redux library by default. It is a pattern that was implemented to create code that reflects a more DRY (Don't Repeat Yourself) approach.

#### Reducer Function

Reducers are functions that handle the actions.
The function takes the current state and the action as its parameters and returns the new state.

A reducer can handle multiple actions, so usually it includes a switch statement for each action case.

For example:

```js
function contactsApp(state, action) {
  switch (action.type) {
    case 'ADD_CONTACT':
      return [ ...state,  action.person ]
    default:
      return state
  }
}
```


In the code above, our reducer function uses a switch statement to handle the appropriate actions.
As the default case, it just returns the current state.

Remember, the reducer has to be a pure function, meaning it cannot modify the current state. It has to return a new state object instead.
The default case is added for handling unknown actions.

#### Multiple Reducers

If you have more than one entity (i.e. users, products, invoices, orders, etc.), it's typically a good idea to break them into multiple reducer functions to separate concerns.

Redux gives us a method that we can use called combineReducers. This allows us to use more than one reducer so that when an action gets dispatched, the action would get run through all of the reducers instead of only one. It also allows us to separate the concerns of our store state.

For example:

```js
const contactsApp = combineReducers({
  addContacts,
  doSomething
})
```


Now, our contactsApp is combining two reducers into one.
It's a good practice to provide each reducer only the part of the state that it needs to manage. This is called reducer composition, and is a fundamental pattern of building Redux apps.

## Redux with React

Now, that we know what Redux is, we can start building React apps that use Redux!

First, we need to install Redux:

```bash
npm install redux
``` 

This will install the Redux library.
However, Redux itself is just a small library, that can be used with different technologies.
To use it with React, we need to install another library, called react-redux:

```bash
npm install react-redux
```

The react-redux library binds React with Redux, allowing React components to read data from a Redux store, and dispatch actions to the store to update data.

### Counter App

As our first example, let's build the Counter app we made in the previous module using Redux!

First, we need to create our action and corresponding reducer.

```js
function incrementCounter(num) {
  return { 
    type: 'INCREMENT', 
    num: num 
  }
}
```


The code above declares an action creator function named incrementCounter(), which returns an action with type INCREMENT and the corresponding payload.

Our reducer:

```js
const initialState = {
  count: 0
};

function reducer(state = initialState, action) {
  switch(action.type) {
    case 'INCREMENT':
      return { count: state.count + action.num };
    default:
      return state;
  }
}
```


The code above defines a reducer function, which returns the new state based on the given action. We increment the count state variable by the provided num value.

We also provide a default value for our state using the initialState variable.
Nothing fancy until now, we just created two simple functions, one returning our action object, the other one returning a new state with the incremented count.

### Creating the Store

To create the store, we call the createStore() function, which takes the reducer as its parameter:

```js
const store = createStore(reducer);
```


But how do we pass the store to our components?
That is achieved using a special `<Provider>` element. It makes the store available to any nested child component.

So, for our counter, we would have the following:

```js
const el = <Provider store={store}>
    <Counter/>
  </Provider>; 
```


Provider takes the store as an attribute and makes it available to its child component.
We need to import `{ createStore }` and `{ Provider }` using the following syntax:

```js
import { Provider } from 'react-redux';
import { createStore } from 'redux';
```

### Connecting to the Store

At this point, we have created our action, the reducer, the store, and made it available to our Counter component using the Provider element.

In order to connect our component to the store, we need to call the connect() function.
The connect() function returns a new component, that wraps the component you passed to it and connects it to the store using its special parameter functions.

#### function connect(mapStateToProps?, mapDispatchToProps?) 

`connect()` takes two optional parameters:

**mapStateToProps**

This function is called every time the store state changes. It receives the state as a parameter and returns the state for the component.
For example, for our Counter, we need to return the count state variable:

```js
function mapStateToProps(state) {
  return {
    count: state.count
  };
}
```

Now, our component can access the count variable using its props! Just as the name of the function states, it maps the state to the props.

**mapDispatchToProps**

As you may have guessed from the name, this parameter is used to map the dispatch functions to props.
It can be a simple object, defining the function that needs to be mapped:

```js
const mapDispatchToProps = {
  incrementCounter
}
```

This might seem a bit confusing, but its very straightforward: mapStateToProps simply returns the state variables as props to our component, while mapDispatchToProps allows to define how we dispatch actions and make the dispatching functions available as props.

Both are optional, as, for example, your component might only need to read from the store.
mapDispatchToProps can also be defined as a function. Take a look at the official documentation for more details.
Note, that we need to import the connect function: `import { connect } from 'react-redux';`

### Accessing The Store

Inside our component we just access the store properties using props

```js
function Counter(props) {
  function handleClick() {
    props.incrementCounter(1);
  }
    return <div>
    <p>{props.count}</p>
    <button onClick={handleClick}>Increment</button>
    </div>;
}
```

Notice, that we pass 1 as the argument to our incrementCounter(), making our counter increment by 1. We can change the value to any other number, and our counter will behave as expected, because we handled the increment parameter in our reducer.

Now, the only thing left is to call the connect() function for our Counter component and render it on the page:

```js
const Counter = connect(mapStateToProps, mapDispatchToProps)(Counter);

const el = <Provider store={store}>
          <Counter/>
        </Provider>;
```

Remember, connect() returns a new component, which wraps the component it received.
Now we have a fully functional React+Redux app!
This might seem too much code for a simple counter app, however this architecture is great when building large scale apps, that use many components, multiple levels of nesting and manage a lot of data.

## Project Structure

To make our project more manageable, we can use separate source files (and folders) for components, reducers and actions.
For example, we can move our Counter component and the action creator function to a separate Counter.js file.

In order to use the Counter component in our index.js, we need to export it first:

```js
export default connect(mapStateToProps, mapDispatchToProps)(Counter); 
```

Notice, we export the connected component.

Now, we can import the component in index.js:

```js
import Counter from './Counter'; 
```

We use the ES6 modules system, which allows use to export and import modules.

