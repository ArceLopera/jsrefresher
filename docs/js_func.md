# JavaScript Functions

Functions define behavior. A function is a collection of statements that are grouped together to perform an operation. 
You can define your own functions to perform your desired tasks.
Functions have many advantages, including:

- Reusable code.
- Easy to test.
- Modifications to a function do not affect the calling program.
- One function can accept many different inputs.

To define a JavaScript function, use the function keyword, followed by a name, followed by a set of parentheses ().

The code to be executed by the function is placed inside curly brackets {}.
``` javascript
function name() {
    
  //code to be executed
}
```

Function names can contain letters, digits, underscores, and dollar signs (same rules as variables). Parameters should be given names, which are separated by commas within the parentheses. If you pass more arguments than are defined, they will be assigned to an array called arguments. They can be used like this: arguments[0], arguments[1], etc. After defining the function, you can call it as many times as needed.
JavaScript functions do not check the number of arguments received.
If a function is called with missing arguments (fewer than declared), the missing values are set to undefined, which indicates that a variable has not been assigned a value.

``` javascript
//Function definition
function sayHello(name, age)
{
    console.log(name + " is " + age + " years old.");
}
//Function use
sayHello("Cassie", 20);
```

A function can have an optional return statement. It is used to return a value from the function.

This statement is useful when making calculations that require a result.
When JavaScript reaches a return statement, the function stops executing.

``` javascript
//Function definition
function myFunction(a, b)
{
     return a*b;
}
//Function use
var res= myFunction(3,2);
```

If you do not return anything from a function, it will return undefined.


## JavaScript Objects
JavaScript variables are containers for data values. Objects are variables too, but they can contain many values.

Think of an object as a list of values that are written as name:value pairs, with the names and the values separated by colons. You can access object properties in two ways.

``` javascript
objectName.propertyName
//or
objectName['propertyName']
```

``` javascript
var person = {
 name: "John", age: 31, 
 favColor: "green", height: 183
};

var x = person.age; //the same as:
var y = person['age'];
```

These values are called properties. JavaScript objects are containers for named values.
JavaScript's built-in length property is used to count the number of characters in a property or string. An object method is a property that contains a function definition.
Use the following syntax to access an object method.

``` javascript
objectName.methodName()
```

Methods are functions that are stored as object properties.

### Constructor Function

Sometimes, we need to set an "object type" that can be used to create a number of objects of a single type.
The standard way to create an "object type" is to use an object constructor function.

``` javascript
function person(name, age, color) {
  this.name = name;
  this.age = age;
  this.favColor = color;
}
```

The above function (person) is an object constructor, which takes parameters and assigns them to the object properties.
The this keyword refers to the current object.

Note that this is not a variable. It is a keyword, and its value cannot be changed.

Once you have an object constructor, you can use the new keyword to create new objects of the same type.

``` javascript
var p1 = new person("Amid", 42, "purple");
var p2 = new person("Jessie", 39, "red");
```

p1 and p2 are now objects of the person type. Their properties are assigned to the corresponding values.

### Object Initialization

Use the object literal or initializer syntax to create single objects.

``` javascript
var John = {name: "John", age: 25};
var James = {name: "James", age: 21};
```


Objects consist of properties, which are used to describe an object. Values of object properties can either contain primitive data types or other objects.

### Object Methods

Methods are functions that are stored as object properties.

Use the following syntax to create an object method:

``` javascript
methodName = function() { code lines }
```


Access an object method using the following syntax:

``` javascript
objectName.methodName()
```

A method is a function, belonging to an object. It can be referenced using the this keyword.
The this keyword is used as a reference to the current object, meaning that you can access the objects properties and methods using it.

Defining methods is done inside the constructor function.

``` javascript
function person(name, age, color) {
  this.name = name;
  this.age = age;
  this.changeName = function(name){
        this.name=name;
  }
}

var p = new person("David", 21);
p.changeName("Jhon");
```


You can also define the function outside of the constructor function and associate it with the object.

``` javascript
function person(name, age) {
  this.name= name;  
  this.age = age;
  this.yearOfBirth = bornYear;
}
function bornYear() {
  return 2016 - this.age;
}

var p = new person("David", 21);
console.log(p.yearOfBirth());
```

Note that it's not necessary to write the function's parentheses when assigning it to an object.
Call the method by the property name you specified in the constructor function, rather than the function name.

---


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

---


## ES6 Rest Parameters

Prior to ES6, if we wanted to pass a variable number of arguments to a function, we could use the arguments object, an array-like object, to access the parameters passed to the function.
For example, let's write a function that checks if an array contains all the arguments passed:

``` js
function containsAll(arr){
    for(let k=1; k < arguments.length; k++){
         let num = arguments[k];
         if(arr.indexOf(num) === -1){
             return false;
         }
    }
    return true;
}
let x =[2,4,6,7];
console.log(containsAll(x,2,4,7));
console.log(containsAll(x,6,4,9));
```


We can pass any number of arguments to the function and access it using the arguments object.

While this does the job, ES6 provides a more readable syntax to achieve variable number of parameters by using a rest parameter:

``` js
function containsAll(arr, ...nums){
    for(let num of nums){
         if(arr.indexOf(num) === -1){
             return false;
         }
    }
    return true;
}
```


The ...nums parameter is called a rest parameter. It takes all the "extra" arguments passed to the function. The three dots (...) are called the Spread operator.
Only the last parameter of a function may be marked as a rest parameter. If there are no extra arguments, the rest parameter will simply be an empty array; the rest parameter will never be undefined.

---