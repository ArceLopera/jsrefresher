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

## Variable Declaration

Since [ES6](js_ECMAScript.md#ecmascript-6-2015--a-major-milestone) we have three ways of declaring variables:

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

---



### Repeating Strings

Before ES6 the following syntax was the correct way to repeat a string multiple times:


``` js

console.log(Array(3 + 1).join("foo"));   //foofoofoo
```


With the new syntax, it becomes:


``` js

console.log("foo".repeat(3));   //foofoofoo
```


### Searching Strings

Before ES6 we only used the indexOf() method to find the position of the text in the string. For example:	


``` js

"Hello World!".indexOf("Wo");
"Hello World!".indexOf("Wo")===6;
```


ES6 has replaced this with a version that has cleaner and more simplified syntax:


``` js

"Hello World!".startsWith("He");
"Hello World!".endsWith("He");
"Hello World!".includes("He");
```

---



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

---
