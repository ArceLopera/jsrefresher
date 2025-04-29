# ES6 Objects

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

---


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
