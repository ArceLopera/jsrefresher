# Operators

An operator is a symbol that performs mathematical or logical manipulations.

+ Javascript supports addition (+), subtraction(-), multiplication(*), division(/) and modulus(%). Also increment (++) and decrement (--).
+ You can get the result of a string expression using the eval() function, which takes a string expression argument like eval("10 * 20 + 8") and returns the result. 
+ If the argument is empty, it returns undefined. 10 * '5' or '10' * '5' will give the same result. But trying to multiply a number with string values that aren’t numbers, like 'hello' * 5 will return NaN (Not a Number). 
+ In JavaScript, we can use the modulus operator on integers AND on floating point numbers.

Exponentiation operator was introduced in [ES7](js_ECMAScript.md#ecmascript-2016-es7).

``` js
console.log(3 ** 4);
// expected output: 81

console.log(10 ** -2);
// expected output: 0.01

console.log(2 ** 3 ** 2);
// expected output: 512

console.log((2 ** 3) ** 2);
// expected output: 64
```

User must explicitly enable this feature.

### The Math Object

The Math object allows you to perform mathematical tasks, and includes several properties. Math has no constructor. There's no need to create a Math object first.

``` js
Math.E    //constant e
Math.PI   //constant pi
```

For exponentiation, we must use Math.pow. to calculate a number raised to the power of some other number.

``` js
var number = Math.ceil(Math.random() * 10);
```


+ Math.abs() returns the absolute value of its parameter.
+ Math.ceil() rounds a floating point value up to the nearest integer value. The rounded value is returned as a double
+ Math.floor() rounds a floating point value down to the nearest integer value.
+ Math.max() returns the largest of its parameters.
+ Math.min() returns the smallest parameter.
+ sqrt() for square root, sin() for sine, cos() for cosine

Javascript also provides compound assignment operators that perform an operation and an assignment in one statement. 
In-place operators allow you to write code like 'x = x + 3;' more concisely, as 'x += 3;'.

``` js
var x = 2;
x += 3;
x *= 4;
x /= 2;
```


The increment (and decrement) operator is used to increase (decrease) an integer's value by one.

``` js
x++; //equivalent to x = x + 1
x--; //equivalent to x = x - 1
```

The increment (and decrement) operator has two forms, prefix and postfix. 
Prefix increments the value, and then proceeds with the expression.
Postfix evaluates the expression and then performs the incrementing.

``` js
++x; //prefix
x++; //postfix
```

### Logical Operators 

(Boolean Operators)

Logical operators are used to join multiple expressions and return true or false. 

The AND operator (&&), the OR operator(||) and the NOT operator(!)

### The ?: Operator 

(Conditional (Ternary) Operator)

Exp1 ? Exp2 : Exp3; The ?: operator works the following way: Exp1 is evaluated. 

If it is true, then Exp2 is evaluated and becomes the value of the entire expression. 

If Exp1 is false, then Exp3 is evaluated and its value becomes the value of the expression.

``` js
var msg= (age >= 18) ? "Welcome" : "Sorry" ;
```

---


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
