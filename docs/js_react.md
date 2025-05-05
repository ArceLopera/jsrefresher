Front-end development refers to what the end user (also commonly referred to as the "client") can see. 
In the most basic forms, front-end development consists of HTML, CSS, and JavaScript.

As a developer, you will find that it is very easy for your front-end (website, web application, etc.) to become very complex and have a lot of different moving parts. 
It makes solving problems much more difficult when you have to go through a maze of code to find the issue.

Eventually, developers decided that there must be a better way to manage all of that code, so they created libraries that could make life easier. React was one of those libraries.
React was created by Facebook and released to the public in May of 2013 and has been consistently maintained since then.

## Why React?

React is one of the most popular JavaScript libraries for front-end web applications.

Here are some of the advantages of React:

+ **Speed** : Interactive websites need to update the DOM (Document Object Model) each time a change happens. This process is generally resourceful and slow.
Compared to other libraries that manipulate the DOM, React uses a Virtual DOM, allowing to update only the parts of the website that have changed. This increases the speed of updates dramatically, as modern web applications may contain thousands of elements.

+ **Ease of Use** : React allows developers to group related code together, thereby making building and maintaining large scale applications much less complex.

+ **Support** : React has an amazingly large community and is open source. It is maintained by Facebook and the community.

## Adding React

React can be added to a website without any special tools and installations.

First, we need to add the React library as two script tags to the head of our HTML document:

```html
<script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script> 
```

Next, we need to add another script, to enable the use of JSX.
JSX is a syntax extension to JavaScript, and it is recommended to be used with React.

```html
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script> 
```

This approach of adding React to a website is only suitable for creating small demos.

After adding the required script tags, we can start building our React app!

We add a container, that will be used to display something using React.

```html
<div id="container"></div>
```

You can use any id for your container. It will be used by React to find the container and add content to it.
Now, it's time for our first React code!
Let's display a simple message as a heading:

```html
<script type="text/babel">
ReactDOM.render(
  <h1>Hello, React!</h1>
  document.getElementById('container')
)
</script>
```

The code finds the container div, and adds the h1 heading to it.

## Create React App

Real web apps have a different scale, contain multiple files, use 3rd party libraries, etc.

Facebook has created a handy tool called Create React App that makes it easy to setup a React project with just a simple command!

To get started, make sure you have a recent version of Node installed on your machine.
Run the following commands in the Terminal to create and start a React app called "my-app":

```bash
npx create-react-app my-app
cd my-app
npm start 
```
This will install all the required dependencies, configure and start the project on `localhost:3000`.

Create React App allows us to focus on the code, rather than installing and configuring different tools.

### Project Structure

Let's explore the structure of our project by opening it using a code editor.
The public folder contains files related to how the application will display on the client, the most important of those being `index.html`, which is the HTML template of our page.
The src folder contains all of the JavaScript, CSS, and image files that will be compiled into a bundle file and injected into `index.html`.

How is React compiled into a bundle file? It uses what is called a "file loader". In the case of Create React App, Webpack is used.
Webpack creates a "bundle" file containing the content of multiple files that need to be "bundled" together and it is all added together into a single file. Instead of making the HTML file go and find multiple files, which can slow down load times tremendously, it only has to find one file.
Remember, all CSS and JS files need to be added to the src folder, otherwise webpack won't see them.

While there are other files in the src folder that come with Create React App when it is generated, the two files below are the only critical files:

+ `index.js`: This file is the entry point into our application. In our code, a method called ReactDOM.render() is used to find an element with id="root" in the HTML and add our React application inside of that element (similar to the previous lesson).
+ `App.js`: This file is the main component that will be rendered to the DOM, which currently includes the React logo image and the default text, that we see in the output.

### Changing the Output

Now, when we know how to create and run a React project, let's change the default output to a simple Hello message.

To do that, we need to open src/index.js and change the code to the following:

```js
ReactDOM.render(
  <h1>Hello, React!</h1>,
  document.getElementById('root')
);
```

A really cool feature of Create React App is Fast Refresh, which automatically reflects the changes made to the code in the browser.

### StackBlitz

To make it easier to play around with React, we will be using StackBlitz as our online playground to enable changing and running real React code.

We have removed all the extra files, such as the logo images, to make the project structure simpler.
Now we have the following files:

+ index.html: The HTML page template.
+ index.js: The entry point of our app.
+ style.css: the stylesheet for our project.
+ package.json: holds various metadata relevant to the project, like dependencies.

## What is JSX?

We will start with the `<h1>Hello, React!</h1>` element.

As you can see, the element is not in quotes to represent a string. It's like an HTML element, however we use it right in the JavaScript code!
This is called JSX, and it is a syntax extension to JavaScript. It allows us to build UI elements right in the JavaScript code!
React does not require using JSX, however, it is common practice in the React community to use JSX as it eases the development of user interfaces, as well as allows React to show useful error and warning messages.

### Intro to JSX

Let's have a look at our code again:

```js
ReactDOM.render(
  <h1>Hello, React!</h1>,
  document.getElementById('root')
); 
```

The code calls React's render method, and passes it two arguments, a JSX element and a container. The render method displays the provided element in the container, which, in our case, is the HTML element with id="root".


When you call the render method, any existing content of the container gets replaced. That is why, usually, the containers are empty in the HTML.

### Expressions in JSX

We can use any JavaScript expression inside JSX using curly braces.

For example:

```js
const name = "David";
const el = <p>Hello, {name}</p>;

ReactDOM.render(
  el,
  document.getElementById('root')
); 
```


In the example above, we use the variable name in the JSX element.
As you can see, JSX can be used just like JavaScript expressions. You can assign a JSX expression to a variable, return it from a function, etc.

### Attributes in JSX

We can specify attributes using quotes, just like in HTML:

```html
<div id="name"></div>
```

When using a JavaScript expression as the attributes value, the quotes should not be used:

```html
<div id={user.id}></div> 
```

React DOM uses camelCase property naming convention instead of HTML attribute names.
For example, class becomes className in JSX.

#### How Does JSX Work?

When the JSX expressions are compiled, they are converted into JavaScript objects, representing React elements.
React then uses these elements to build the corresponding HTML DOM and display it in the browser.

Let's create a counter app, that increments a counter variable every second and displays it on the page as a paragraph:

```js
let counter = 0;

function show() {
  counter++;
  const el = <p>{counter}</p>;
  ReactDOM.render(
    el, document.getElementById('root')
  );
}

setInterval(show, 1000); 
```


Try it on StackBlitz

We use setInterval to call the show function every second and render the counter element on the page.

One of the great features of React is that it updates only the elements that need an update. You can inspect the HTML output of the example above and see that only the text in the paragraph gets updated every second.
In practice, most React apps call ReactDOM.render() once.

## Virtual DOM

We learned in the previous part that React updates only the elements that are necessary.
This allows React apps to be much faster than apps built with other front-end technologies.

But how does React achieve that?
React uses a Virtual DOM, which is a lightweight representation of the DOM.
When an element gets changed, it is first updated in the Virtual DOM. That process is fast, as the virtual DOM is represented by simple objects.

After that, React compares the Virtual DOM to its previous state and only applies the DOM updates necessary to bring the DOM to the desired state.
DOM stands for Document Object Model and is a tree-like representation of the HTML page.

### Components

Components let you split the page into independent and reusable parts.
Notice that the page can be split into multiple parts. Each of these "parts" are a component.
The heading is a component, the button is a component, and the search bar is its own component.
This makes organizing the page leaps and bounds easier, but even more importantly, components allow us as the developers to separate concerns from one another.
Separation of concerns is a programming principle that states that each concern should be separated into individual pieces.

#### Functional Components

In React, there are two types of components that you can use: Functional Components and Class Components.
In this part, we will talk about functional components.

A functional component is a simple JavaScript function:

```js
function Hello() {
  return <h1>Hello world.</h1>;
}
```

The code above defined a functional component called Hello, that returns a simple React element.
Notice that the name of the functional component begins with a capital letter. This is absolutely critical. If we start the name of a component with a lowercase letter, the browser will treat our component like a regular HTML element instead of a Component.

#### Rendering Components

In order to display the component, we need to create the corresponding JSX element.

For example, for our user-defined component Hello:

```js
const el = <Hello />; 
```


Now, we can use our user-defined element and render it on the page:

```js
function Hello() {
  return <h1>Hello world.</h1>;
}

const el = <Hello />; 
ReactDOM.render(
  el, 
  document.getElementById('root')
);
```
Remember, all component names need to start with a capital letter.

#### Class Components

Class components are typically used when there are more advanced user interactions, like forms, and animations.

All class components need to extend the React.Component class.

We can rewrite our Hello functional component as a class component:

```js
class Hello extends React.Component {
  render() {
    return <h1>Hello world.</h1>;
  }
} 
```

Class components need to have a render method, which is in charge of telling what the page should show.

#### Props

Functional components can accept arguments, similar to JavaScript functions. These arguments are called props, and represent an object.

For example, we can use props in our Hello component:

```js
function Hello(props) {
  return <p>Hello, {props.name}!</p>;
}
```

Now, we can add a name attribute to our element:

```js
const el = <Hello name="David" />; 
```


The attribute value will be passed to the component when rendered.

An element can have multiple custom attributes, which will be passed to the component using the props object. You can use any custom names for your attributes.

#### Components using Components

Components can use other components to generate an output.

For example:

```js
function App() {
  return <div>
    <Hello name="David" />
    <Hello name="James" />
    <Hello name="Amy" />
  </div>;
}
```


Here, our App component uses the Hello component three times, each times with a new name attribute.

Generally, it is a good practice to split complex components into multiple smaller components, that are reusable.
For example, a Post component can use an Avatar component, an Image component, a Date component, etc.

#### Props in Class Components

Props can be accessed in class components using this.props.

For example:

```js
class Hello extends React.Component {
  render() {
    return <p>Hello, {this.props.name}!</p>;
  }
} 
```

An important thing to consider is that props are read-only, meaning components cannot modify their props.
Interactive apps generally need to change data and the page elements.

### An Example

Now that we know how to create components and pass them data, let's create a shopping list.

Each item in our list will have a name and a price.

For example:

```js
<Item name="Cheese" price="4.99" /> 
```


The Item component will render a simple div element with the data:

```js
function Item(props) {
  return <div className="item">
  <b>Name:</b> {props.name} <br />
  <b>Price:</b> {props.price}
  </div>;
}
```


Now we can use our component and create multiple items for our shopping list:

```js
<Item name="Cheese" price="4.99" />
<Item name="Bread" price="1.5" />
<Item name="Ice cream" price="24" />
```

We have added some simple CSS styles to separate the items visually.

### State

Up until this point, we have learned how to pass data to components using props.

Many web apps need their components to change their data, for example, after user interaction (clicking a button, submitting a form, etc.).
However, props cannot be changed.

In order to allow components to manage and change their data, React provides a feature called state.
State is an object that is added as a property in class components.

For example:

```js
class Hello extends React.Component {
  state = {
    name: "James"
  }

  render() {
    return <h1>Hello {this.state.name}.</h1>;
  }
}
```

As you can see, state is just a simple object, that contains key:value pairs.
Similar to props, the values can be accessed using this.state.

Now, when the component renders, the state is initialized with the given value and there will be a heading that says `"Hello James."`.

The state object can contain multiple key:value pairs, separated by commas.

#### Changing State

State should not be modified directly. Instead, React provides a setState() method, that can be used to modify state.

For example:

```js
this.setState({ 
  name: "James",
  age: 25
}); 
```


You need to pass an object with the new key:value pairs to the setState method.

Why should we use setState, instead of simply changing the values of the object properties directly?
The answer uncovers one of the most useful features of React: when setState is called, React automatically re-renders the affected component with the new state!

Usually, the change in state happens in event handlers. We will look at an example in the next part!
When state changes using the setState method, React gets informed and immediately re-renders the component with the updated state.

## Counter App

To better understand how state works, let's create a counter app, which increments the counter each time a button is clicked.
We start by creating our Counter component, which includes the counter and a button:

```js
class Counter extends React.Component {
  state = {
    counter: 0
  }
  render() {
    return <div>
    <p>{this.state.counter}</p>
    <button>Increment</button>
    </div>;
  }
} 
```


We have initialized our counter to the value 0 in the state.

Now, we need to add a click event handler to the button and increment the counter in the state.
Here is the final code:

```js
class Counter extends React.Component {
  state = {
    counter: 0
  }
  increment = () => {
    this.setState({
     counter: this.state.counter+1});
  }
  render() {
    return <div>
    <p>{this.state.counter}</p>
    <button onClick={this.increment}>Increment</button>
    </div>;
  }
}
```

The onClick event calls the increment function of our component, which uses setState to change the value of our counter. When the state is changed, React automatically triggers a re-render of the component.

Notice that the event handler uses camelCase syntax and that the handler function is passed in curly braces.

## Props vs State

As a recap, here is a summary of the main differences between props and state:

- We use props to pass data to components.
- Components use state to manage their data.
- Props are read-only and cannot be modified.
- State can be modified by its component using the setState() method.
- The setState() method results in re-rendering the component affected.


Components that have state are called stateful, while components that do not use state are called stateless.

## Hooks

Earlier version of React allowed to use state only with class components.
In recent iterations of React, a new feature called hooks was introduced, allowing to use state inside of functional components.

First, we need to import the useState hook:

```js
import React, { useState } from 'react'; 
```


useState returns a pair, the current state value and a function, that lets you change the state.
useState takes one argument, which is the initial value of the state.

Let's look at an example:

```js
function Hello() {
  const [name, setName] = useState("David");

  return <h1>Hello {name}.</h1>;
}
```


In the example above, we create a name state variable and a setName function. The square brackets syntax is called array destructuring. It assigns the name variable to the current state value, and setName to the function that allows to change the state. You can name these variables anything you like.
Then, we pass "David" as the initial value for our name variable to useState().
You can create multiple state variables with their corresponding set methods. Just use separate statements for each variable using the useState hook.

### Counter App using Hooks

Now we can rewrite our Counter app from the previous lesson using a functional component and hooks!

Here is the code:

```js
function Counter() {
  const [counter, setCounter] = useState(0);

  function increment() {
    setCounter(counter+1);
  }

  return <div>
  <p>{counter}</p>
  <button onClick={increment}>
    Increment
  </button>
  </div>;
} 
```

As you can see, compared to the class component, the code is much shorter and easier to read and understand. That was one of the reasons why the React team created Hooks.
Remember, hooks can only be used inside functional components.
Hooks are functions that allow to "hook into" React features from function components.

### Lifecycle Methods

React provides special lifecycle methods for class components, which are called when components are mounted, updated or unmounted.

Mounting is the process when a component is rendered on the page.
Unmounting is the process when a component is removed from the page.

The componentDidMount method is called when a component is rendered on the page.

For example, we can use componentDidMount in our Counter app to set the initial value of the counter:

```js
componentDidMount() {
  this.setState({counter: 42});
}
```

This will set an initial value of the counter when the component is rendered.

componentDidMount is typically used for populating the state inside of a component when it initially mounts to the DOM.
Similarly, the componentWillUnmount() lifecycle method is called right before the component is removed from the DOM. It can be used to free up resources taken by the component.

#### componentDidUpdate

Another lifecycle method is componentDidUpdate(), which is called when a component is updated in the DOM.

We can, for example, alert the current counter value when it is incremented:

```js
componentDidUpdate() {
  alert("Number of clicks: " + this.state.counter);
}
```


componentDidUpdate() is only called when the component is updated.

#### The useEffect Hook

The lifecycle methods we covered are only available for class components.
However, React provides a special Hook called useEffect to make lifecycle methods available in functional components. It combines the componentDidMount, componentDidUpdate, and componentWillUnmount methods into one.

For example, we can achieve the behavior of our last example using a functional Counter component:

```js
function Counter() {
  const [counter, setCounter] = useState(0);

  useEffect(() => {
    alert("Number of clicks: " + counter);
  });

  function increment() {
    setCounter(counter+1);
  }
  return <div>
  <p>{counter}</p>
  <button onClick={increment}>Increment</button>
  </div>;
}
```

When you run the code, you'll notice that the alert dialog appears also during the first render. This is caused by the fact that, by default, useEffect runs both, after the first render and after every update.

To call the method only when something changes, we can provide it a second argument:

```js
useEffect(() => {
  //do something
}, [count]);  
```


Now, the useEffect() method will run only if count changes.

To mimic componentWillUnmount, useEffect may return a function that cleans up after it:

```js
useEffect(() => {
  // do something
  
  return () => {
    // cleanup
  }; 
});
```


You can have multiple effects in the same component.
Just like with the useState hook, we need to import useEffect to be able to use it: 

```js
import React, { useState, useEffect } from 'react';
```

## Event Handling

Handling events in React is very similar to handling events in the DOM.

The only difference is that event names use camelCase syntax and the event handler needs to be passed in curly braces.

For example, to handle the click event on a button:
<button onClick={handleClick}>
  My Button
</button> 


Clicking the button will call the handleClick function of the component.

Let's explore our Counter app:
function Counter() {
  const [counter, setCounter] = useState(0);

  function increment() {
    setCounter(counter+1);
  }
  return <div>
  <p>{counter}</p>
  <button onClick={increment}>Increment</button>
  </div>;
}


Try it on StackBlitz

The onClick event calls the increment function, which is incrementing the counter state variable.
Check out the same Counter app built using a class component here.

Handling User Input

One of the common ways that users interact with web pages is through text fields.

We can handle user input in React using the onChange event of the text field.
When the value of the text field changes, the event handler is called, updating the value of the field in the component's state.
This way you always have the actual value of the text field in the state.

Let's make an app to convert Km to Miles. We will take the Km value from a text field and calculate the miles value upon input:
function Converter() {
  const [km, setKm] = useState(0);

  function handleChange(e) {
    setKm(e.target.value);
  }
  function convert(km) {
    return (km/1.609).toFixed(2);
  }

  return <div>
  <input type="text" value={km}
     onChange={handleChange} />
  <p> {km} km is {convert(km)} miles </p>
  </div>;
}


Try it on StackBlitz

Our Converter component includes a text field, which calls the handleChange function when its value changes.
The handleChange function updates the state with the current value of the textfield, causing the component to re-render and show the corresponding miles value, which is calculated using the convert function.
The value of the text field is accessed via the e object, which represents the React event. It is passed to the event handler function as an argument and can be used to access the event object.

Forms

In the previous part, we learned how to handle user input in text fields. Text fields are usually part of a form.

Similar to the previous example, React form elements keep their state and update it based on user input.
This way you always have the data of your form at your disposal in the state.

To demonstrate this, we will create a form, that will add numbers every time the form is submitted and display the sum.
Our form contains an input field and a submit button:
function AddForm() {
  const [sum, setSum] = useState(0);
  const [num, setNum] = useState(0);

  function handleChange(e) {
    setNum(e.target.value);
  }

  function handleSubmit(e) {
    setSum(sum + Number(num));
    e.preventDefault();
  }

  return <form onSubmit={handleSubmit}>
  <input type="number" value={num} onChange={handleChange} />
  <input type="submit" value="Add" />
  <p> Sum is {sum} </p>
  </form>;
}


Try it on StackBlitz

In the code above, the value of the input is controlled by React (we keep the value in the state).
When the form is submitted using the submit button, the handleSubmit function gets called, which updates the value of sum in the state.

An input form element whose value is controlled by React in this way is called a "controlled component".
Notice the e.preventDefault(); statement. This statement prevents the default behavior of the form, which, by default, reloads the page when submitted. In JavaScript we would use return false; for that, but in React we need to call preventDefault().

Lists

Web apps commonly contain repeating elements, such as lists or sections, where the same DOM element is repeated with a different data set.

Consider an array of strings:
const arr = ["A", "B", "C"];


We need to render a list <li> element for each item in the array.
We can define a MyList component and pass it the array as a prop using a custom data attribute:
<MyList data={arr} />


Now, when the array is accessible via props, we can write the component logic:
function MyList(props) {
  const arr = props.data;
  const listItems = arr.map((val) =>
    <li>{val}</li>
  );
  return <ul>{listItems}</ul>;
}


Try it on StackBlitz

We take the input array from the incoming props, loop through the array using the JavaScript map function and return a <li> element for each item.
The resulted array is stored in the listItems variable.
Then, the component returns the listItems array inside a <ul> tag.

This code results in a warning, saying that each element needs a unique key

Keys

Each element in a list must have a key attribute.
Keys act as a unique identity, identifying each element.
Usually, these are IDs from your data, or can be auto-generated indexes.

For example:
const listItems = arr.map((val, index) =>
  <li key={index}>{val}</li>
);


Try it on StackBlitz

Keys are important, because they uniquely identify elements, helping React understand which items have changed, are added, or are removed.

Example : Contact Manager

Now, that we know how to create components, pass them data using props and manage their data using state, let's start building our Contact Manager.

Our Contact Manager will allow to view the list of contacts and add new ones to the list.

By looking at the mockup, it makes sense to have two components:
AddPersonForm: a form with the text field and Add button.
PeopleList: a list of contacts.

Let's create these components.
AddPersonForm uses state to manage the value of the text field:
function AddPersonForm() {
  const [ person, setPerson ] = useState("");

  function handleChange(e) {
    setPerson(e.target.value);
  }

  function handleSubmit(e) {
    e.preventDefault();
  }
  return (
    <form onSubmit={handleSubmit}>
    <input type="text" 
    placeholder="Add new contact" 
    onChange={handleChange} 
    value={person} />
    <button type="submit">Add</button>
    </form>
    );
}


For now, we just prevent the default behavior when the form is submitted.

PeopleList received an array representing the contacts and renders a list on the page:
function PeopleList(props) {
  const arr = props.data;
  const listItems = arr.map((val, index) =>
    <li key={index}>{val}</li>
  );
  return <ul>{listItems}</ul>;
}


Now we can render our components on the page and include some initial data:
const contacts = ["James Smith", "Thomas Anderson", "Bruce Wayne"];

const el = (
  <div>
    <AddPersonForm />
    <PeopleList data={contacts} />
  </div>
);


Try it on StackBlitz

Adding a new contact does not work, as we have not built the logic in the handleSubmit function yet.

Sharing State

Right now, our AddPersonForm independently keeps its state. How can we add a new contact to our PeopleList then, when the form is submitted?

To accomplish that, we need to share the state between the components. We can do that by lifting the state up to a parent component. This means that the parent component will hold the data that needs to be shared between the components. In our case, that is the contacts list.

Let's create a parent component called ContactManager, which includes the AddPersonForm and PeopleList as child components and holds the contacts list in its state:
function ContactManager(props) {
  const [contacts, setContacts] = useState(props.data);

  return (
    <div>
      <AddPersonForm />
      <PeopleList data={contacts} />
    </div>
  );
} 


Try it on StackBlitz

The ContactManager component receives the initial contacts list using props, saves it in its state.
Then it passes down the contacts list to its child component.
Data can be passed from the parent to the child, but not from the child to the parent. React uses what is called unidirectional data flow, in other words, data only flows downward, so to speak.

Adding a Contact

Now, we can create an addPerson() function to our ContactManager component to add a new person to our contacts state array:
function ContactManager(props) {
  const [contacts, setContacts] = useState(props.data);

  function addPerson(name) {
    setContacts([...contacts, name]);
  }
 ...
} 


But how are we going to call this function from our child AddPersonForm component, where the data for the new person is stored?
Just like we passed down data using props, React allows us to pass down function references!
function ContactManager(props) {
  const [contacts, setContacts] = useState(props.data);

  function addPerson(name) {
    setContacts([...contacts, name]);
  }

  return (
    <div>
      <AddPersonForm handleSubmit={addPerson} />
      <PeopleList data={contacts} />
    </div>
  );
} 


Similar to passing the contacts list to our PeopleList component, we passed down the addPerson() function to our AddPersonForm using a prop called handleSubmit.

Now, our PeopleList can call the handleSubmit function that it received when the form is submitted, to add a new person to the list:
function AddPersonForm(props) {
  const [ person, setPerson ] = useState('');
    
  function handleChange(e) {
    setPerson(e.target.value);
  }
    
  function handleSubmit(e) {
    props.handleSubmit(person);
    setPerson('');
    e.preventDefault();
  }
  return (
    <form onSubmit={handleSubmit}>
      <input type="text" 
        placeholder="Add new contact" 
        onChange={handleChange} 
        value={person} />
      <button type="submit">Add</button>
    </form>
  );
} 


Try it on StackBlitz
We also clear the value of the text field using setPerson('') after adding a new person.

Summary

An important takeaway from this lesson is that props can be used to pass down not only state, but also functions, that may manipulate the state.
This way, we are able to store the application state in the parent and allow its child components to use and manipulate the state.

Now, when our app is fully functional, we can add some CSS styles and a check, to prevent creation of blank contacts.

Try It on StackBlitz

Intro to Redux

State Management

In the previous module we built a Contact Manager app, which stores the state in the parent component, and passes it down to the corresponding child components.

In the real world with larger scale applications, this can get far more complex. We might have to pass down the state data multiple levels to get to the desired component.

Having to pass down data to multiple levels of nested components would make it hard to understand what caused a change to the state, as there might be multiple potential components that can change the state.

This would also cause a lot of redundant code, make it hard to maintain and debug the code.

Redux was created to make state management predictable, providing a single state container and strict rules on how state can be changed.

Redux is a small JavaScript library and can be used with any front-end framework, such as React, Angular, jQuery.

It employs the "single source of truth" pattern.
In short, single source of truth just refers to relocating the application state and all associated logic outside of the application, allowing ANY component to access the data it needs.
Having a single state container makes it easier to manage the state of your application, as you can access and change the data from any component that needs it, without having to pass down the data.

Core Concepts

Store

Let's look into the core concepts of Redux.

In Redux, the application's state is stored as a simple object, called store.
There should only be a single store in an app.

For example, a store can look like this:
{
  contacts: [{
    name: 'David'
  }, {
    name: 'Amy'
  }],
  toggle: true
}


You cannot change the state directly. Instead, you need to dispatch an action.

Actions & Reducers

An action is just a plain JavaScript object:
{ 
  type: 'ADD_CONTACT', 
  name: 'James' 
}


The code above defines an action with type ADD_CONTACT and a name property.

An action clearly describes why the state change happened, and can be dispatched from anywhere in your app.

At this point we just have a store, which includes our state data and an object, that includes some data that needs to be changed in the state. So, how do we actually do the change?
To tie the store and the action together, we need to write a function, called a reducer.
It takes state and action as arguments, and returns the next state of the app.

For example:
function contactsApp(state, action) {
  if (action.type === 'ADD_CONTACT') {
    return [ ...state,  action.name ]
  } else {
    return state
  }
}


The code above defines a simple reducer function, that checks the action and returns the new state.

These concepts are basically the idea of Redux: you hold the global state in a store, define actions to describe what to change in the store and write reducer functions to handle those actions.
Notice, we have not touched any React specific syntax, all of the above is plain JavaScript.

Core Concepts

Redux can be described using the following principles:

Single source of truth
The global state of the app is stored in a single store.

State is read-only
You can change the state only by dispatching actions. Action are objects, that contain information about what should be changed.

Pure reducers
Reducers are functions that handle the actions and return the next state of the application. Reducers need to be pure, meaning they cannot modify the state, they need to return a new state object.

Actions

Action can be viewed as payloads of information that send data to the store.
Actions are represented by simple JavaScript object and need to have a type property:
{
  type: 'ADD_CONTACT',
  name: 'James'
}



In the example above, we define an action with the type ADD_CONTACT and provide it a name property as its payload.
Notice that for the type we're using all uppercase letters and words separated by underscores. This is also called "snake case". This is the generally accepted way to create an action type.
You can use any naming and structure for the other properties defining the data in the action.

You can, for instance, call it payload, and provide it an object with the data:
{
    type: 'ADD_CONTACT',
    payload: {
        name: "Jimmy Barnes"
    }
 }


You should pass as little data in each action as possible. That keeps the actions clean and easy to read.

Action Creators

In order to use the same action with different payloads, as well as create reusable code, we can create Action creators.

Action creators are simple functions that return actions.

For example:
function addContact(person) {
  return {
    type: 'ADD_CONTACT',
    payload: person
  }
}


The action creator function takes a person parameter and uses that as the actions payload.
Now, we can use the action creator to create multiple new contacts by passing it the corresponding data.
Action creators are not built into the Redux library by default. It is a pattern that was implemented to create code that reflects a more DRY (Don't Repeat Yourself) approach.

Reducer Function

Reducers are functions that handle the actions.
The function takes the current state and the action as its parameters and returns the new state.

A reducer can handle multiple actions, so usually it includes a switch statement for each action case.

For example:
function contactsApp(state, action) {
  switch (action.type) {
    case 'ADD_CONTACT':
      return [ ...state,  action.person ]
    default:
      return state
  }
}


In the code above, our reducer function uses a switch statement to handle the appropriate actions.
As the default case, it just returns the current state.

Remember, the reducer has to be a pure function, meaning it cannot modify the current state. It has to return a new state object instead.
The default case is added for handling unknown actions.

Multiple Reducers

If you have more than one entity (i.e. users, products, invoices, orders, etc.), it's typically a good idea to break them into multiple reducer functions to separate concerns.

Redux gives us a method that we can use called combineReducers. This allows us to use more than one reducer so that when an action gets dispatched, the action would get run through all of the reducers instead of only one. It also allows us to separate the concerns of our store state.

For example:
const contactsApp = combineReducers({
  addContacts,
  doSomething
})


Now, our contactsApp is combining two reducers into one.
It's a good practice to provide each reducer only the part of the state that it needs to manage. This is called reducer composition, and is a fundamental pattern of building Redux apps.

Redux with React

Now, that we know what Redux is, we can start building React apps that use Redux!

First, we need to install Redux:
npm install redux 

This will install the Redux library.
However, Redux itself is just a small library, that can be used with different technologies.
To use it with React, we need to install another library, called react-redux:
npm install react-redux

The react-redux library binds React with Redux, allowing React components to read data from a Redux store, and dispatch actions to the store to update data.

Counter App

As our first example, let's build the Counter app we made in the previous module using Redux!

First, we need to create our action and corresponding reducer.
function incrementCounter(num) {
  return { 
    type: 'INCREMENT', 
    num: num 
  }
}


The code above declares an action creator function named incrementCounter(), which returns an action with type INCREMENT and the corresponding payload.

Our reducer:
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


The code above defines a reducer function, which returns the new state based on the given action. We increment the count state variable by the provided num value.

We also provide a default value for our state using the initialState variable.
Nothing fancy until now, we just created two simple functions, one returning our action object, the other one returning a new state with the incremented count.

Creating the Store

To create the store, we call the createStore() function, which takes the reducer as its parameter:
const store = createStore(reducer);


But how do we pass the store to our components?
That is achieved using a special <Provider> element. It makes the store available to any nested child component.

So, for our counter, we would have the following:
const el = <Provider store={store}>
    <Counter/>
  </Provider>; 


Provider takes the store as an attribute and makes it available to its child component.
We need to import { createStore } and { Provider } using the following syntax:
import { Provider } from 'react-redux';
import { createStore } from 'redux';

Connecting to the Store

At this point, we have created our action, the reducer, the store, and made it available to our Counter component using the Provider element.

In order to connect our component to the store, we need to call the connect() function.
The connect() function returns a new component, that wraps the component you passed to it and connects it to the store using its special parameter functions.
function connect(mapStateToProps?, mapDispatchToProps?) 


connect() takes two optional parameters:

mapStateToProps
This function is called every time the store state changes. It receives the state as a parameter and returns the state for the component.
For example, for our Counter, we need to return the count state variable:
function mapStateToProps(state) {
  return {
    count: state.count
  };
}


Now, our component can access the count variable using its props! Just as the name of the function states, it maps the state to the props.

mapDispatchToProps
As you may have guessed from the name, this parameter is used to map the dispatch functions to props.
It can be a simple object, defining the function that needs to be mapped:
const mapDispatchToProps = {
  incrementCounter
}


This might seem a bit confusing, but its very straightforward: mapStateToProps simply returns the state variables as props to our component, while mapDispatchToProps allows to define how we dispatch actions and make the dispatching functions available as props.

Both are optional, as, for example, your component might only need to read from the store.
mapDispatchToProps can also be defined as a function. Take a look at the official documentation for more details.
Note, that we need to import the connect function: import { connect } from 'react-redux';

Accessing The Store

Inside our component we just access the store properties using props
function Counter(props) {
  function handleClick() {
    props.incrementCounter(1);
  }
    return <div>
    <p>{props.count}</p>
    <button onClick={handleClick}>Increment</button>
    </div>;
}


Notice, that we pass 1 as the argument to our incrementCounter(), making our counter increment by 1. We can change the value to any other number, and our counter will behave as expected, because we handled the increment parameter in our reducer.

Now, the only thing left is to call the connect() function for our Counter component and render it on the page:
const Counter = connect(mapStateToProps, mapDispatchToProps)(Counter);

const el = <Provider store={store}>
          <Counter/>
        </Provider>;


Try in on StackBlitz

Remember, connect() returns a new component, which wraps the component it received.
Now we have a fully functional React+Redux app!
This might seem too much code for a simple counter app, however this architecture is great when building large scale apps, that use many components, multiple levels of nesting and manage a lot of data.

Project Structure

In our Counter example, we wrote the whole code in a single source file.
Usually, web apps contain multiple component, reducers and actions.

To make our project more manageable, we can use separate source files (and folders) for components, reducers and actions.
For example, we can move our Counter component and the action creator function to a separate Counter.js file.

In order to use the Counter component in our index.js, we need to export it first:
export default connect(mapStateToProps, mapDispatchToProps)(Counter); 


Notice, we export the connected component.

Now, we can import the component in index.js:
import Counter from './Counter'; 


Try it on StackBlitz

We use the ES6 modules system, which allows use to export and import modules.

Contact Manager

Let's change our Contact Manager app to use Redux!

We created a separate folder named components for our components.

We use Redux to keep the contacts list.

The ADD_PERSON action is used to add a new person to the list.
Check out the complete project code on StackBlitz!

Notice, that we manage the new contact form's state in React, not Redux, because the data is used only by the AddPersonForm component to temporarily keep the input value. You can move it to Redux, if you want to; we just used local component state for simplicity.

