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

In JavaScript we commonly use the for loop to iterate over values in a list:

``` js
let arr = [1,2,3];
for(let k =0 ; k < arr.length;k++){
    console.log(arr[k]);
}
```


### For..in loop

The for...in loop is intended for iterating over the enumerable keys of an object.
For example:

``` js
let obj = {a:1,b:2,c:3};
for (let v in obj){
    console.log(v);
}
```


The for...in loop should NOT be used to iterate over arrays because, depending on the JavaScript engine, it could iterate in an arbitrary order. Also, the iterating variable is a string, not a number, so if you try to do any math with the variable, you'll be performing string concatenation instead of addition.

### For...of loop

ES6 introduces the new for...of loop, which creates a loop iterating over iterable objects.

For example:

``` js
let list=["x","y","z"];
for (let val of list){
    console.log(val);
}
```


During each iteration the val variable is assigned the corresponding element in the list.

The for...of loop works for other iterable objects as well, including strings

``` js
for (let val of "Hello"){
    console.log(val);
}
```


The for...of loop also works on the newly introduced collections (Map, Set, WeakMap, and WeakSet).

## Functions in ECMAScript 6

Prior to ES6, a JavaScript function was defined like this:

``` js
function add(x,y){
    var sum= x+y;
    console.log(sum);
}
```


ES6 introduces a new syntax for writing functions. The same function from above can be written as:

``` js
const add = (x,y) => {
    let sum= x+y;
    console.log(sum);
}
```


This new syntax is quite handy when you just need a simple function with one argument.
You can skip typing function and return, as well as some parentheses and braces.

For example:

``` js
const greet = x => "Welcome "+ x;
console.log(greet("John"));
```

The code above defines a function named greet that has one argument and returns a message.

If there are no parameters, an empty pair of parentheses should be used, as in

``` js
const  x = () => alert("Hi");
```


The syntax is very useful for inline functions. For example, let's say we have an array, and for each element of the array we need to execute a function. We use the forEach method of the array to call a function for each element:

``` js
var arr = [2,3,7,8];

arr.forEach(function(el) {
    console.log(el * 2);
});
```

However, in ES6, the code above can be rewritten as following:

``` js
var arr = [2,3,7,8];

arr.forEach(v => {
    console.log(v * 2);
});
```


### Default Parameters in ES6

In ES6, we can put the default values right in the signature of the functions.

``` js
function test(a, b = 3, c = 42){
  return a + b + c;
}
console.log(test(5)); //50 
```

And here's an example of an arrow function with default parameters:

``` js
const test = (a, b = 3, c = 42) => {
  return a + b + c;
}
console.log(test(5)); //50 
```

Default value expressions are evaluated at function call time from left to right. This also means that default expressions can use the values of previously-filled parameters.

## ES6 Objects

JavaScript variables can be Object data types that contain many values called properties.
An object can also have properties that are function definitions called methods for performing actions on the object.
ES6 introduces shorthand notations and computed property names that make declaring and using objects easier to understand.

The new method definition shorthand does not require the colon (:) or function keyword, as in the grow function of the tree object declaration:

``` js
let tree = {
    height:10,
    color: 'green',
    grow() {
        this.height +=2;
    }
};
tree.grow();
console.log(tree.height);  //12
```

You can also use a property value shorthand when initializing properties with a variable by the same name.
For example, properties height and health are being initialized with variables named height and health

``` js
let height = 5;
let health = 100;

let athlete = {
      height,
      health
};

console.log(athlete.height); //5
console.log(athlete.health); //100
```

When creating an object by using duplicate property names, the last property will overwrite the prior ones of the same name.
For Example:

``` js
var a = {x: 1,x: 2,x: 3,x: 4};
console.log(a.x); //4
```

Duplicate property names generated a SyntaxError in ES5 when using strict mode. However, ES6 removed this limitation.

### Computed Property Names

With ES6, you can now use computed property names. Using the square bracket notation [], we can use an expression for a property name, including concatenating strings. This can be useful in cases where we want to create certain objects based on user data (e.g. id, email, and so on).
It is very useful when you need to create custom objects based on some variables.
Here are three examples:

**Example 1**

``` js
let prop = 'name';
let id = '1234';
let mobile = '12345678';

let user = {
    [prop]: 'Jack',
    [`user_${id}`]: `${mobile}`
};
```

**Example 2**

``` js
var i = 0;
var a = {
     ['foo' + ++i]: i,
     ['foo' + ++i]: i,
     ['foo' + ++i]: i
};
```

**Example 3**

``` js
var param = 'size';
var config = {
   [param]: 12,
   ['mobile' + param.charAt(0).toUpperCase() + param.slice(1)]: 4
};
console.log(config.mobileSize);
```

### Object.assign() in ES6

ES6 adds a new Object method assign() that allows us to combine multiple sources into one target to create a single new object.
Object.assign() is also useful for creating a duplicate of an existing object.

Let's look at the following example to see how to combine objects:

``` js
let person = {
     name: 'Jack',
     age: 18,
     sex: 'male'
};

let student = {
     name: 'Bob',
     age: 20,
     xp: '2'
};
let student = Object.assign({}, person, student);
```

Here we used Object.assign() where the first parameter is the target object you want to apply new properties to.
Every parameter after the first will be used as sources for the target. There are no limitations on the number of source parameters. However, order is important because properties in the second parameter will be overridden by properties of the same name in third parameter, and so on.

In the example above, we used a new object {} as the target and used two objects as sources.

Now, let's see how we can use assign() to create a duplicate object without creating a reference (mutating) to the base object.
In the following example, assignment was used to try to generate a new object. However, using = creates a reference to the base object. Because of this reference, changes intended for a new object mutate the original object:

``` js
let person = {
     name: 'Jack',
     age: 18
};
let newPerson = person;  //newPerson references person
newPerson.name = 'Bob';

console.log(person.name); //Bob
console.log(newPerson.name); //Bob
```


To avoid this (mutations), use Object.assign() to create a new object.
For example:

``` js
let person = {
     name: 'Jack',
     age: 18
};
let newPerson = Object.assign({},person);  
newPerson.name = 'Bob';

console.log(person.name); //Jack
console.log(newPerson.name); //Bob
```

Finally, you can assign a value to an object property in the Object.assign() statement.

For example:

``` js
let person = {
     name: 'Jack',
     age: 18
};
let newPerson = Object.assign({},person, {name: 'Bob'});  

console.log(person.name); //Jack
console.log(newPerson.name); //Bob
```

## Array Destructuring in ES6

The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.
ES6 has added a shorthand syntax for destructuring an array.

The following example demonstrates how to unpack the elements of an array into distinct variables:

``` js
let arr = ['1','2','3'];
let [one, two, three] = arr;

console.log(one); //1
console.log(two); //2
console.log(three); //3
```

We can also destructure an array returned by a function.

``` js
let a = () => {
     return [1,2,3];
};
let [one,,two] = a();

console.log(one); //1
console.log(two); //3
```


Notice that we left the second argument's place empty.

The destructuring syntax also simplifies assignment and swapping values:

``` js
let a, b, c = 4, d=8;
[a, b = 6] = [2];  // a=2,  b=6
[c, d] = [d, c];  // c=8, d = 4

console.log(a); //2
console.log(b); //6
console.log(c); //4
console.log(d); //8
```

## Object Destructuring in ES6

Similar to Array destructuring, Object destructuring unpacks properties into distinct variables.

For example:

``` js
let obj = {h:100, s: true};
let {h, s} = obj;

console.log(h); //100
console.log(s); //true
```

We can assign without declaration, but there are some syntax requirements for that:

For example:

``` js
let a,b;
({a, b} = {a: 'Hello', b: 'world!'});

console.log(a); //Hello
console.log(b); //world!
```

The () with a semicolon (;) at the end are mandatory when destructuring without a declaration. However, you can also do it as follows where the () are not required:

``` js
let {a, b} = {a: 'Hello', b: 'world!'};

console.log(a); //Hello
console.log(b); //world!
```

You can also assign the object to new variable names.

For example:

``` js
var o = {h: 42, s:true};
var {h: foo, s: bar} = o;

//console.log(h); //Error
console.log(foo); //42
console.log(bar); //true
```


Finally you can assign default values to variables, in case the value unpacked from the object is undefined.

For example:

``` js
var obj = {id: 42, name:'Carlos'};
let  {id =10, age = 20} = obj;

console.log(id); //42
console.log(age); //20
```

## ES6 Rest Parameters
