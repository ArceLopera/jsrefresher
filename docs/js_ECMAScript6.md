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

## ES6 The Spread Operator

This operator is similar to the Rest Parameter, but it has another purpose when used in objects or arrays or function calls (arguments).

**Spread in function calls**

It is common to pass the elements of an array as arguments to a function. Before ES6, we used the following method:

``` js
function myFunction(w, x, y, z){
       console.log(w+x+y+z);
}
var args =[1,2,3];
myFunction.apply(null, args.concat(4));
```


ES6 provides an easy way to do the example above with spread operators.

``` js
const myFunction = (w, x, y, z) => {
       console.log(w+x+y+z);
};
let args =[1,2,3];
myFunction( ...args, 4);
```


Example:

``` js
var dateFields = [1981,11,26];
var date = new Date(...dateFields);
console.log(date);
```


**Spread in array literals**

Before ES6, we used the following syntax to add an item at middle of an array:

``` js
var arr = ["One", "Two", "Five"];

arr.splice(2, 0,"Three");
arr.splice(3, 0, "Four");
console.log(arr);
```


You can use methods such as push, splice, and concat, for example, to achieve this in different positions of the array. However, in ES6 the spread operator lets us do this more easily:

``` js
let newArr = ['Three','Four'];
let arr = ['One', 'Two', ...NewArr, 'Five'];
console.log(arr);
```


**Spread in object literals**

In objects it copies the own enumerable properties from the provided object onto a new object.

``` js
const obj1 = {foo: 'bar', x: 42};
const obj2 = {foo: 'baz', y: 5};

const cloneObj = {...obj1};  //{foo: 'bar', x: 42}
const mergedObj = {...obj1, ...obj2};  //{foo: 'baz', x: 42, y: 5}
```


However, if you try to merge them you will not get the result you expected:

``` js
const obj1 = {foo: 'bar', x: 42};
const obj2 = {foo: 'baz', y: 5};
const merge = (...objects) => ({...objects});

let mergedObj = merge(obj1, obj2);  
// { 0: {foo: 'bar', x: 42}, 1:  {foo: 'baz', y: 5} }

let mergedObj2 = merge({},obj1,obj2);
// { 0: {}, 1: {foo: 'bar', x: 42}, 2:  {foo: 'baz', y: 5} }
```

Shallow cloning or merging objects is possible with another operator called Object.assign().

## Classes in ES6

In this lesson we'll explain how to create a class that can be used to create multiple objects of the same structure.
A class uses the keyword class and contains a constructor method for initializing.

``` js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```


A declared class can then be used to create multiple objects using the keyword new.

``` js
const square = new Rectangle(5,5);
const poster = new Rectangle(2,3);
```


Class Declarations are not hoisted while Function Declarations are. If you try to access your class before declaring it, ReferenceError will be returned.

You can also define a class with a class expression, where the class can be named or unnamed.
A named class looks like:

``` js
var Square = class Rectangle {
      constructor(height, width){
           this.height = height;
           this.width = width
       }
};
```


In the unnamed class expression, a variable is simply assigned the class definition:

``` js
var Square = class {
      constructor(height, width){
           this.height = height;
           this.width = width
       }
};
```

The constructor is a special method which is used for creating and initializing an object created with a class. There can be only one constructor in each class.

### Class Methods in ES6

ES6 introduced a shorthand that does not require the keyword function for a function assigned to a method's name. One type of class method is the prototype method, which is available to objects of the class.

``` js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  get area(){
        return this.calcArea();
  }
  calcArea(){
        return this.height*this.width
  }
}
const square = new Rectangle(5,5);
console.log(square.area);  //25
```


In the code above, area is a getter, calcArea is a method.
Another type of method is the static method, which cannot be called through a class instance. Static methods are often used to create utility functions for an application.

``` js
class Point {
   constructor (x, y){
       this.x = x;
       this.y = y;
   }
   static distance(a, b) {
        const dx = a.x - b.x;
        const dy = a.y - b.y;
        return Math.hypot(dx, dy);
   }
}
const p1 = new Point(7, 2);
const p2 = new Point(3, 8);

console.log(Point.distance(p1,p2));

// 5.385164807134504
```

As you can see, the static distance method is called directly using the class name, without an object.

### Inheritance in ES6

The extends keyword is used in class declarations or class expressions to create a child of a class. The child inherits the properties and methods of the parent.

``` js
class Animal {
    constructor(name){
        this.name = name; 
    }
    speak(){
        console.log(this.name + 'makes noise');
    }
}

class Dog extends Animal {
     speak() {
        console.log(this.name + 'Woof!');
     }
}

let dog = new Dog('Sparky');
dog.speak();
```


In the code above, the Dog class is a child of the Animal class, inheriting its properties and methods.
If there is a constructor present in the subclass, it needs to first call super() before using this. Also, the super keyword is used to call parent's methods.
For example, we can modify the program above to the following:

``` js
class Animal {
    constructor(name){
        this.name = name; 
    }
    speak(){
        console.log(this.name + 'makes noise');
    }
}

class Dog extends Animal {
     speak() {
        super.speak();
        console.log(this.name + 'Woof!');
     }
}

let dog = new Dog('Sparky');
dog.speak();
```

In the code above, the parent's speak() method is called using the super keyword.

## ES6 Collections