# String, Variables and Assignments

+ Each statement in JavaScript must end with a **semicolon (;)**. 
+ A comment beginning with two slashes (//) is called a single-line comment. 
+ Comments that require multiple lines begin with /* and end with */ at the end of the comment block.

``` js
// this is a single-line comment
var x = 5; // a single-line comment after code
/*  This is also a
    comment spanning
    multiple lines 
*/
```


## JSDocs

``` js
/**
 * This is a function.
 *
 * @param {string} n - A string param
 * @return {string} A good string
 *
 * @example
 *
 *     foo('hello')
 */
function foo(n) {
  return n
}
```


## Data Types

Declaring a variable is as simple as using the keyword var. 

JavaScript variable names are case-sensitive. 

- The first character of a variable name must be a letter, underscore (_), or a dollar sign ($) (Subsequent characters can be letters, digits, underscores, or dollar signs).
- The first character of a variable name can’t be a number.
- Variable names can’t include a mathematical or logical operator in their name. For instance, 2*something or this+that;
- Variable names can’t contain spaces.
- You’re not allowed to use any special symbols, like my#num, num%, etc.

``` js
var x = 10;
var y = 10.55;
var name = "John";
var isAlive = true;
var myNull = null;
var myUndefined = undefined;
```


Single or double quotes, it doesn’t matter, so long as you’re consistent with them. Like this:

``` js
var name = 'John';
var text = "My name is John Smith";
```

You can use quotes inside a string, as long as they don't match the quotes enclosing the string itself. 

``` js
var name = 'John';
var text = "My name is 'John' ";
```

You can get double quotes inside of double quotes using the escape character like this: \" or \' inside of single quotes. If you start a string with a single quote, then you need to end it with a single quote too. This applies to double quotes. Otherwise, JavaScript will get confused.

### Booleans

``` js
var isActive = true; 
var isAlive = false;
```


The Boolean value of 0 (zero), null, undefined, empty string is false.
Everything with a "real" value is true.


### First JavaScript Program

On the web, JavaScript code lives inside the HTML document, and needs to be enclosed by <script> and </script>:

``` html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>JavaScript Mastery</title>
  </head>
  <body>
    <h1>JavaScript Mastery</h1>
    <script>
      document.write("<h1>Hello World!</h1>")
      console.log("Hello Console!") 
    </script>
  </body>
</html>
``` 



## PopUp Boxes

JavaScript offers three types of popup boxes, the Alert, Prompt, and Confirm boxes.

### Alert Box

An alert box is used when you want to ensure that information gets through to the user.
When an alert box pops up, the user must click OK to proceed.
The alert function takes a single parameter, which is the text displayed in the popup box. To display line breaks within a popup box, use a backslash followed by the character n.

``` js
alert("Hello World!\nBye");
```

Be careful when using alert boxes, as the user can continue using the page only after clicking OK.

### Prompt Box

A prompt box is often used to have the user input a value before entering a page.
When a prompt box pops up, the user will have to click either OK or Cancel to proceed after entering the input value.
If the user clicks OK, the box returns the input value. If the user clicks Cancel, the box returns null.

The prompt() method takes two parameters.

- The first is the label, which you want to display in the text box.
- The second is a default string to display in the text box (optional).

``` js
var user = prompt("Enter your name");
if (user != null)
{
        alert("Hello " + user);
}
else
{
        alert("Bye");
}
```

When a prompt box pops up, the user will have to click either "OK" or "Cancel" to proceed after entering an input value. Do not overuse this method, because it prevents the user from accessing other parts of the page until the box is closed.

### Confirm Box

A confirm box is often used to have the user verify or accept something.
When a confirm box pops up, the user must click either OK or Cancel to proceed.
If the user clicks OK, the box returns true. If the user clicks Cancel, the box returns false.

The confirm() method takes a single parameter, which is the text displayed in the popup box.

``` js
var result = confirm("Want to exit?");
if (result)
{
        alert("Bye!");
}
else
{
        alert("Continue");
} 
```


## Operators

An operator is a symbol that performs mathematical or logical manipulations.

Javascript supports addition (+), subtraction(-), multiplication(*), division(/) and modulus(%). Also increment (++) and decrement (--).

You can get the result of a string expression using the eval() function, which takes a string expression argument like eval("10 * 20 + 8") and returns the result. 

If the argument is empty, it returns undefined. 10 * '5' or '10' * '5' will give the same result. 

But trying to multiply a number with string values that aren’t numbers, like 'hello' * 5 will return NaN (Not a Number). 

In JavaScript, we can use the modulus operator on integers AND on floating point numbers.

Exponentiation operator was introduced in ES7.

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

## Exceptions

An exception is a problem that occurs during program execution. Exceptions cause abnormal termination of the program.
An exception can occur for many different reasons. Some examples:

- A user has entered invalid data.
- A file that needs to be opened cannot be found.
- A network connection has been lost in the middle of communications.
- Insufficient memory and other issues related to physical resources.


JavaScript (similar to Java and C#) provides a flexible mechanism called the try-catch statement to handle exceptions so that a program won't crash when an error occurs.
The code that might generate an exception is placed in the try block. If an exception occurs, the catch blocks is executed without stopping the program.
The type of exception you want to catch appears in parentheses following the keyword catch.
We use the general Exception type to handle all kinds of exceptions. We can also use the exception object e to access the exception details, such as the original error message (e.Message):
A single try block can contain multiple catch blocks that handle different exceptions separately.
Exception handling is particularly useful when dealing with user input.

``` js
try {
  nonExistentFunction();
} catch (error) {
  console.error(error);
  // expected output: ReferenceError: nonExistentFunction is not defined
  // Note - error messages will vary depending on browser
}
```

An optional finally block can be used after the catch blocks. The finally block is used to execute a given set of statements, whether an exception is thrown or not.

``` js
try {
  try_statements
}
catch (exception_var) {
  catch_statements
}
finally {
  finally_statements
}
```

``` js
try {
  myroutine(); // may throw three types of exceptions
} catch (e) {
  if (e instanceof TypeError) {
    // statements to handle TypeError exceptions
  } else if (e instanceof RangeError) {
    // statements to handle RangeError exceptions
  } else if (e instanceof EvalError) {
    // statements to handle EvalError exceptions
  } else {
    // statements to handle any unspecified exceptions
    logMyErrors(e); // pass exception object to error handler
  }
}
```


### throw

The throw keyword allows you to manually generate exceptions from your methods. A common use case for this is to only catch (and silence) a small subset of expected errors, and then re-throw the error in other cases:

``` js
try {
  myRoutine();
} catch (e) {
  if (e instanceof RangeError) {
    // statements to handle this very common expected error
  } else {
    throw e;  // re-throw the error unchanged
  }
}
```


## JavaScript Arrays

An array is a special type of object.
An array uses numbers to access its elements, and an object uses names to access its members.

``` js
var courses = new Array(3);
courses[0]="HTML";
courses[1]="CSS";
courses[2]="JS";
```

You refer to an array element by referring to the index number written in square brackets.
This statement accesses the value of the first element in courses and changes the value of the second element.

``` js
var courses = new Array("HTML", "CSS", "JS"); 
var course = courses[0]; // HTML
courses[1] = "C++"; //Changes the second element 
```

JS[0] is the first element in an array. [1] is the second. Array indexes start with 0. Attempting to access an index outside of the array, returns the value undefined.
JavaScript arrays are dynamic, so you can declare an array and not pass any arguments with the Array() constructor. You can then add the elements dynamically.

``` js
var courses = new Array();
courses[0]="HTML";
courses[1]="CSS";
courses[2]="JS";
courses[3]="CS";
```


### Array Literal

For greater simplicity, readability, and execution speed, you can also declare arrays using the array literal syntax.

``` js
var course = ["HTML","CSS";"JS"];
```

This results in the same array as the one created with the new Array() syntax.
You can access and modify the elements of the array using the index number, as you did before.
The array literal syntax is the recommended way to declare arrays.


### Arrays Properties and Methods

The length property returns the number of elements of the array. The length property is always one more than the highest array index. If the array is empty, the length property returns 0.
JavaScript's concat() method allows you to join arrays and create an entirely new array.

``` js
var c1 =["HTML","CSS"];
var c2=["JS","CS"];
var courses=c1.concat(c2);
```

The concat operation does not affect the c1 and c2 arrays - it returns the resulting concatenation as a new array.

### Associative Arrays

Remember that JavaScript does not support arrays with named indexes.
In JavaScript, arrays always use numbered indexes.
It is better to use an object when you want the index to be a string (text).
Use an array when you want the index to be a number.
If you use a named index, JavaScript will redefine the array to a standard object.

## Date Object
#### setInterval

The setInterval() method calls a function or evaluates an expression at specified intervals (in milliseconds).
It will continue calling the function until clearInterval() is called or the window is closed.

``` js
function myAlert()[
     	alert("HI");
}
setInterval(myAlert, 3000);
```

This will call the myAlert function every 3 seconds (1000 ms = 1 second).
Write the name of the function without parentheses when passing it into the setInterval method.

The Date object enables us to work with dates.
A date consists of a year, a month, a day, an hour, a minute, a second, and milliseconds.

Using new Date(), create a new date object with the current date and time

``` js
var d = new Date();
//d stores the current date and time
```


The other ways to initialize dates allow for the creation of new date objects from the specified date and time

- new Date(milliseconds)
- new Date(dateString)
- new Date(year, month, day, hours, minutes, seconds, milliseconds)


JavaScript dates are calculated in milliseconds from 01 January, 1970 00:00:00 Universal Time (UTC). One day contains 86,400,000 millisecond.
For example:

``` js
//Fri Jan 02 1970 00:00:00
var d1 = new Date(86400000); 

//Fri Jan 02 2015 10:42:00
var d2 = new Date("January 2, 2015 10:42:00");

//Sat Jun 11 1988 11:42:00
var d3 = new Date(88,5,11,11,42,0,0);
```

JavaScript counts months from 0 to 11. January is 0, and December is 11.
Date objects are static, rather than dynamic. The computer time is ticking, but date objects don't change, once created.
When a Date object is created, a number of methods make it possible to perform operations on it. getMonth(), getDate(), getDay(),etc…

``` js
var d = new Date();
var hours= d.getHours();
//hours equals to the current hour
```

## Control Flow
### For-Loops

A for loop executes a set of statements a specific number of times. The init and increment statements may be left out, if not needed, but remember that the semicolons are mandatory. 
for (; ;) {} is an infinite loop.

``` js
for ( var i=0; i <10;  i++ ) {
     //...;
}
```

### While-Loops

A while loop repeatedly executes a block of code as long as a given condition is true.

``` js
var num = 1;
while(num < 6 )
{
       console.log(num);
       num++;
}
```

### Do-While Loops

A do-while loop is similar to a while loop, except that a do-while loop is guaranteed to execute at least one time.

``` js
var a = 0;
do {
      console.log(a);
      a++;
}while( a < 5);
```

### Conditionals
The general form of the if statement is:

``` js
if(x == 3)
{
      //....
}
else if (x == 0)
{
      //....
}
else
{
      //....
}
```
Use relational operators (Comparison Operators) to evaluate conditions. They only work when they’re comparing the same data type; numbers with numbers, strings with strings. In addition to the less than (<) and greater than (>) operators, the following operators are available: >=, <=, ==(Equal to), !=(Not Equal to), ===(Identical, Equal and same type), !==(Not identical).
Remember, that an if can have zero or more else if's and they must come before the last else, which is optional. Once an else if succeeds, none of the remaining else if's or else clause will be tested.

The switch statement provides a more elegant way to test a variable for equality against a list of values.
Each value is called a case, and the variable being switched on is checked for each switch case. The default code executes when none of the cases matches the switch expression.

``` js
// Or using a switch:
switch(x) {
  case 3:
    // ...
    break;
  case 0:
    // ...
    break;
  default:
    // ...
    break;
}
```

### Break and Continue
When the break statement is encountered inside a loop, the loop is immediately terminated and the program execution moves on to the next statement following the loop body. If you are using nested loops (i.e., one loop inside another loop), the break statement will stop the execution of the innermost loop and start executing the next line of code after the block.
The continue statement is similar to the break statement, but instead of terminating the loop entirely, it skips the current iteration of the loop and continues with the next iteration.

``` js
for( var i = 0; i < 10; i++)
{
        if( i % 2 == 0)  continue;
        if( i == 6) break;
        console.log(i);
}
```
