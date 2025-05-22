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

In the following code below we have 4 parts of a component: 


```ts

// This section is the imports section.
import { Component } from '@angular/core';


// This section is the decorator section. It points to code automatically generated by Angular; we don't have to touch this part unless we want to change it.
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']  
})

// This section is the class section.
export class AppComponent {
  name = "Star student";

  speak() {}

}
```

#### Class vs Method Variables

Let's put some code into our speak() method to see what instance variables vs method variables look like in practice:

```ts
export class AppComponent {
  name = "Star student";

  speak() {
    const sentence = "Abiye" + this.name;
    console.log(sentence);
  }

}
```

The variables prefix and name are class variables. They belong to the class.

Inside of the speak() method, if we want to invoke class members, we have to use this keyword.

Also, note that inside of the speak() method, we are using the const keyword to declare the sentence variable. Inside of methods, you must use a keyword like var, let or const to declare variables. We chose const because const keywords declare a value that is a constant. It will not change.

We did not use static typing for the prefix, name, and sentence variables because the type was inferred when we initialized these variables with strings.

The name variable is a method variable. It belongs to the speak() method.

## Arrays and iterations

### Iterating through String Arrays

With Angular, noted in code as ng, we can use the *ngFor command in the HTML file (the view) to loop through arrays declared in the component.

Given this array in the Angular component:

```ts
colors:string[] = ['red', 'blue', 'green', 'purple'];
```

We can loop through the colors in the accompanying HTML file in Angular like this:

```html
<div *ngFor='let color of colors'> 
  {{color}} 
</div>
```


The result in your browser will look like this:

```
red
blue
green
purple
```

Where each of the colors, red, blue, green, etc. are wrapped within a div. *ngFor essentially creates a loop where the html tag that it's declared within loops for as many times as there are elements in the array that it's invoking.

*ngFor is a structural directive. Structural directives modify HTML according to variable data that they are associated with.

### Iterating with Indices

Sometimes it's helpful, when iterating through an array, to have access to an index within each iteration of the loop.

Here's how we do that in Angular:

```html
<div *ngFor='let fruit of fruits; let i=index'>
   Fruit {{ i }} is {{ fruit }} 
</div>
```


The result in your browser will look like this:

```
Fruit 0 is apple
Fruit 1 is orange
Fruit 2 is pear
Fruit 3 is peach
```

Note that our 'iterator' variable is named i. This variable can be named anything; we just used the letter i out of convention. The 'index' keyword cannot be changed. Angular knows that the 'index' is the index of each iteration as we loop through the array.


Indices during iteration are helpful when iterating through lists of things, like shopping cart items, that are associated with database ids from the back end.

### Iterating through Custom Types

We will now connect what you learned about interfaces with our *ngFor looping mechanism.

Let's make an interface for a Car and put it in its own file called car.ts (.ts is the extension for TypeScript files)

```ts
export interface Car {
  make: string;
  model: string;
  miles: number;
}
```

Now that we have a Car interface, we can import that interface into our component as such:

```ts
import { Car } from './car';
```

Now we can create 3 entities of the Car type:

```ts
subaru: Car = {make: 'Subaru', model: 'Outback', miles: 58232};
honda: Car = {make: 'Honda', model: 'Accord', miles: 39393};
bmw: Car = {make: 'BMW', model: 'X3', miles: 4400};
cars:Car[ ] = [this.subaru, this.honda, this.bmw];
```


And finally we can loop through all of our cars in the HTML file:

```html
<div *ngFor="let car of cars">
   {{car.make}} {{car.model}}  with a mileage of {{car.miles}}
</div>
```

Here is our output:

```
Subaru Outback with a mileage of 58232
Honda Accord with a mileage of 39393
BMW X3 with a mileage of 4400
```

When you iterate over a custom type, like a Car in this instance, you must use dot notation ( car.make, car.model, car.miles, etc.) to access the members of that entity because interfaces are made up of various fields, similar to a JavaScript object.

## Angular Services

Services are special files in Angular that are used to manage data. They usually pull data from XHR (XML/HTTP Requests), but they can also store data on their own.
A service is like a 'brain' in an Angular app that either returns data from the service itself or data retrieved from an external source. It can be viewed as a 'data manager'.

### Generating an Angular Service

Angular can generate a service for you with a simple command so you don't have to remember how to build the basic structure.

In order to do this, we use this command in the computer terminal:

```bash
ng generate service transportation
```

This generates an empty service within the Angular application.

```ts
import { Injectable } from '@angular/core';
@Injectable({
  providedIn: 'root'
})
export class TransportationService {
  constructor() { }
}
```


We will only concern ourselves with two parts of this service:

1. The top of the file where the imports live. This is where we will import files that the service will use.
2. The class body where it says export class TransportationService. The class body is contained within the curly brackets after the word TransportationService.

Methods within the class body of the service are used to export data out of the service.

#### Import Interface into a Service

Our Transportation Service will contain an array of Car types. To do that, we need to import our Car interface that we created earlier. We learned that the top of the file is where we import things.

We can add this line to the top section of the transportation service:

```ts
import { Car } from './car';
```


This allows us to use the Car type to make an array of Cars. Our transportation service has now IMPORTED the interface from the car.ts file.

The car.ts file EXPORTS the interface and the transportation service IMPORTS that same interface for use. That will now allow us to create an array of Car types in our service.

The import / export functionality we see in Angular is derived from NodeJS. This same import / export system is seen in almost every front-end JavaScript framework, as most of these frameworks are built using Node.

#### Recreating Car Array in a Service

Now that we've imported the car resource, we can create an array of Car types in our transportation service. The last thing we need to do after we do this is to create a getCars( ) method to export the car data out of the service. Here is the completed service:

```ts
import { Injectable } from '@angular/core';
 import { Car } from './car';
 
 @Injectable({
  providedIn: 'root'
 })
 export class TransportationService {
  // NEW CODE
  subaru: Car = {make: 'Subaru', model: 'Outback', miles: 58232};
  honda: Car = {make: 'Honda', model: 'Accord', miles: 39393};
  bmw: Car = {make: 'BMW', model: 'X3', miles: 4400};
 
  cars:Car[] = [this.subaru, this.honda, this.bmw];
 
  constructor() { }
 
  // NEW CODE
  getCars() {
    return this.cars;
  }
 }
```

This service is now ready to use by our component.

Services export methods that will later be invoked by Angular components that use the service. One service can conceivably be used by multiple components.

### Dependency Injection

Now that our service is actually exporting data, our component needs to pull it in.

In Angular we use something called dependency injection to pull a service into a component.

This service is now ready to use by our component.

```ts
import { Component, OnInit } from '@angular/core';
// Import the TransportationService.
import { TransportationService } from './transportation.service';
import { Car } from './car';
 
@Component({
  selector: 'app-angular',
  templateUrl: './angular.component.html',
  styleUrls: ['./angular.component.css']
})
export class AngularComponent implements OnInit {
 
  cars: Car[];
 
  // Inject the TransportationService into the component.
  constructor(private transportationService: TransportationService) {
    this.cars = this.transportationService.getCars(); 

  }
 
  ngOnInit() {
    this.cars = this.transportationService.getCars();
  }
 
}
```

This component is now ready to use the data that the service exports.
Dependency injection is a common design pattern in object oriented programming.

Think of dependency injection like installing a weather app on your phone. Every phone that installs the weather app gets the same app. It can be installed on multiple phones, and every phone that clicks a "get weather" button for a city will get the same weather. The weather service is a central service that provides data for everyone who subscribes to it. That's what a service does through dependency injection. It usually provides data to all of its subscribers, along with other functionality.
  
Note how we create a private variable called transportationService that is of the type TransportationService. transportationService (with the lowercase t) is the variable and TransportationService (with an upperCase T) is the type. Those two naming conventions are called camelCase and PascalCase, respectively. Using camelCase for class variables and PascalCase for class and interface names is a convention seen throughout Angular.

## Event Binding
