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

