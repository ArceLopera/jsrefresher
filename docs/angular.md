# The Angular Framework

Angular is a front-end JavaScript framework. A framework is a set of connected libraries designed around a specific programming language. Frameworks provide conventions that support doing things a certain way. A front-end framework typically has specific conventions around how HTML is handled, how forms are created, how interactive elements on a web page are handled, how variables are interpolated inside of HTML views, etc.

AngularJS or Angular 1.x was the first iteration of the Angular framework. With the release of Angular 2, Angular was completely redesigned using TypeScript and component based architecture. Although component based architecture was available in the later releases of Angular 1.x, components are now the very foundation of Angular 2 and all subsequent releases after version 2. After 2, Angular 4 was released and versions counted upwards from there (there was no version 3).

It is important to know that when developers say Angular, they mean Angular versions 2 and higher. AngularJS refers to version 1 of Angular only.

## DataTypes

AngularJS used Javascript as its primary language. Angular began using TypeScript starting in Angular 2. Since then, TypeScript has become the primary language of Angular.

### Strings in TypeScript

Variables in TypeScript can be statically typed. Statically typed variables must always retain the data type that they start out with. Once a variable is statically typed as a string, for example, that variable cannot hold any other data type.

TypeScript uses JavaScript’s var, let, and const keywords to initialize variables.

It also uses a colon after the variable name to designate the type.

Javascript:

```js
let name = 'Fred'
console.log(name)
```


TypeScript:

```ts
let name: string = 'Fred'
console.log(name)
```


Based on this convention, we could initialize a shoeColor string in TypeScript as such:

```ts
let shoeColor: string = 'blue' ;
console.log(shoeColor);
```


It is possible to change variable values over time:

```ts
shoeColor = 'red' ;
console.log(shoeColor); 
// Now "shoeColor" has a value of red. Note that once a variable has been typed, you don't have to declare a type again when the value of the variable changes.
```


TypeScript does not require you to statically type variables. Plain Javascript syntax WILL work in TypeScript. However, by convention, most programmers statically type variables in TypeScript because it helps to provide structure and prevent programmer errors.

### Numbers in TypeScript

Another TypeScript data type is the number data type.

We can initialize a seatCount number variable in TypeScript like this:

```ts
let seatCount: number = 42;
console.log(seatCount);
```


TypeScript does not designate between integers and floating point or decimal numbers like other languages when it comes to typing. Initializing a decimal number is just like initializing an integer:

```ts
let registrationPercentage: number = 92.87;
console.log(registrationPercentage);
```


Note that registrationPercentage will always have to be of a number type. If you were to try to reassign registrationPercentage to a string value in another line of that program, the program would not compile, and your text editor would most likely throw an error.

```ts
registrationPercentage = 'Ninety Two';

// WILL CAUSE AN ERROR because registrationPercentage is statically typed as a number.
```


Typescript includes all methods that you are used to using in JavaScript. For example, string methods like parseInt() and parseFloat() that return numbers will also work in TypeScript.

### Booleans in TypeScript

Boolean values are either true or false. In TypeScript, you can declare and statically type a variable without initializing it with a value. For example:

```ts
let isRegistered: boolean;
console.log(isRegistered); // undefined
```


If you try to use isRegistered at this point in the program, however, you will get an error. Some programmers declare variables and type them without initializing them because the value of the variable is completely unknown at the start of the program. Later, you can assign it.

```ts
isRegistered = false;
console.log(isRegistered); // false
```


Booleans always return true or false values. These values are not strings, they are actually their own data type.

### Enums in TypeScript

Enum values in Typescript are collections of constants. Think of an Enum as a type of fixed array of things that you use as a reference, such as days of the week, states in the USA, etc. The number of elements never changes during the run of the program and the order of elements doesn’t change either.

Let’s create an enum called spiceLevel:

```ts
enum spiceLevel {
  NONE = "no spice",
  LOW = "barely spicy",
  MEDIUM = "medium spicy",
  HIGH = "hot"
}

console.log(spiceLevel.MEDIUM); 
// outputs "medium spicy"
```


Modern Integrated development environments ( IDEs ) like Visual Studio Code help you complete enum values and other coding constructs by using autocomplete. Enums help to ensure that commonly used constants in your program are all consistent. This helps to avoid typos and general errors.

### The 'any' Type in TypeScript

Finally, we will examine the any data type.
The 'any' type is essentially a wild card. It can hold anything.

We can declare an 'any' data type in TypeScript like this:

```ts
let userData: any;
```


`userData` will now be a container that can hold any data type. Once userData is initialized, however, it will infer the type from the value given to it.

```ts
let userData: any;

userData = 22;
console.log(userData + 2);
// logs 24

userData = "free";
console.log(userData + "man");
// logs "freeman";
```

Note that with an any data type, even though the type is inferred upon assignment, you can re-assign the variable to another data type and it still works.

Why in the world would you ever need an 'any' type? Well, in certain situations, like getting user data from a server, you might be accepting variable data that could conceivably be of any data type.
Any types not only accommodate data from any source, but they also signal to other developers the fact that this particular variable is of an unknown type and that the data should be handled with care.

### Custom Types

If you thought for a minute that TypeScript was limited to number, string, boolean, and other familiar types, then we have a pleasant surprise for you! In TypeScript, you can create your OWN types and use them the same way that you would primitive types like numbers and strings.

One way to do this is by creating an interface. An interface in TypeScript is a data structure that defines the shape of data. Let’s see this in action:

```ts
interface Order {
  customerName: string,
  itemNumbers: number[],
  isComplete: boolean
}
```


The interface keyword is used to initialize an interface, which shows us the SHAPE of the data that’s coming. Think of an interface like a factory mold. This interface is used to stamp out Order types for a store. Now let’s actually use the Order interface to type a variable:

```ts
let order1: Order;
order1 = {
  customerName: "Abiye",
  itemNumbers: [123,44,232],
  isComplete: false
}
```


Let’s analyze the order1 variable. It is of an "Order" type, so it must have 3 fields: the first field is a string, the second field is an array of integers, and the third field is a boolean. It MUST have each of those fields in order to fulfill the contract of the interface. Try omitting one of the fields in order1 (for example, remove the customerName). You will receive an error because the contract has not been fulfilled.
An interface contract is simply the list of fields in that interface that any variable needs if it wants to use that type. All of the normal fields within an interface must be implemented in any variable that uses that type.

## Optional Fields in Interfaces

We can use optional fields in an interface in TypeScript. Optional fields are not part of the strict interface contract. You can omit them when creating an instance of that interface.

```ts
interface Order {
  customerName: string,
  itemNumbers: number[],
  isComplete?: boolean
}
```


Notice the question mark after isComplete. isComplete? means that we can omit that value and the code will still compile. This is useful for fields within an interface that are not mandatory.

```ts
let order1: Order;
order1 = {
  customerName: "Abiye",
  itemNumbers: [123, 44, 232]
}
```


Order1 only has 2 fields now and it still compiles because isComplete is an optional field.
Optional fields are helpful when getting data from a database or an API call where some fields may be missing or incomplete.


## Angular Files

Up until this point, we have been creating simple TypeScript files that run in any environment that runs TypeScript. From this point on, however, we will be writing ALL of our TypeScript in Angular!

In Angular, each component has at least 4 files that work in harmony together.

The only two files that we will concern ourselves with here are the app.component.ts file, which we will call the component, and the app.component.html file which we will call the view.

The component is where variables are declared and modified.

The view is an HTML file that receives variables from the component and displays them.

We have built a 'hello world' example to show you how these files communicate with each other.

**COMPONENT**

```ts
name = "Star student";
```


**VIEW**

```html
<div class='container'>
  <div class='box'>
    Hello, {{name}} ! 
  </div>
</div>
```


Result:
![img](./Images/img.png)

We have set up this code on StackBlitz, which is an online Angular editor, that allows you to run the code on your phone! In StackBlitz, the files are on the far left, the code is in the middle, and a small browser is on the right. You can view and or edit the code and see the result within seconds.

The double curly braces around {{name}} demonstrates what we call interpolation. Interpolation is the insertion of variable content from the component into the view.

### Parts of a Component
