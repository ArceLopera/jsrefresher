ECMAScript (ES) is a scripting language specification created to standardize JavaScript.

The Sixth Edition, initially known as ECMAScript 6 (ES6) and later renamed to ECMAScript 2015, adds significant new syntax for writing complex applications, including classes and modules, iterators and for/of loops, generators, arrow functions, binary data, typed arrays, collections (maps, sets and weak maps), promises, number and math enhancements, reflection, and proxies.

In other words, ES6 is a superset of JavaScript (ES5). The reason that ES6 became so popular is that it introduced new conventions and OOP concepts such as classes.

## Variable Declaration

In ES6 we have three ways of declaring variables:

``` js
var x = 5;
let y = 5;
const z = 5;
```

The type of declaration used depends on the necessary scope. Scope is the fundamental concept in all programming languages that defines the visibility of a variable.

### var & let

Unlike the var keyword, which defines a variable globally, or locally to an entire function regardless of block scope, let allows you to declare variables that are limited in scope to the block, statement, or expression in which they are used.

``` js
if(true){
    let name ='Jack';
}
alert(name);//generates error
```

In this case, the name variable is accessible only in the scope of the if statement because it was declared as let.

To demonstrate the difference in scope between var and let, consider this example:

``` js
function varTest(){
    var x = 1;
    if(true){
       var x = 2;          // same variable
       console.log(x); // 2
    }
    console.log(x); //2
}
function letTest(){
    let x = 1;
    if(true){
       let x = 2;          // different variable
       console.log(x); // 2
    }
    console.log(x); //1
}

varTest();
letTest();
```

One of the best uses for let is in loops:

``` js  
for(let i = 0; i < 10; i++){
    console.log(i);
}
```
let is not subject to Variable Hoisting, which means that let declarations do not move to the top of the current execution context.

### const

const variables have the same scope as variables declared using let. The difference is that const variables are immutable - they are not allowed to be reassigned.
For example, the following generates an exception:

``` js
const x = 5;
x = 6;
```

const is not subject to Variable Hoisting too, which means that const declarations do not move to the top of the current execution context.
Also note that ES6 code will run only in browsers that support it. Older devices and browsers that do not support ES6 will return a syntax error.

## Template Literals in ES6

Template literals are a way to output variables in the string.
Prior to ES6 we had to break the string, for example:

``` js
var name = 'John';
var text = 'My name is ' + name;
```

Now we can use template literals:

``` js
var name = 'John';
var text = `My name is ${name}`;
```

Notice that template literals are enclosed by the backtick (` `) character instead of double or single quotes.
The ${expression} is a placeholder, and can include any expression, which will get evaluated and inserted into the template literal.

``` js
let a = 8;
let b = 3;
let msg = `The sum is ${a+b}!`;
console.log(msg);
```

To escape a backtick in a template literal, put a backslash \ before the backtick.

## Loops