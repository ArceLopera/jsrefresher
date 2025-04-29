ECMAScript (ES) is a scripting language specification created to standardize JavaScript.

The Sixth Edition, initially known as ECMAScript 6 (ES6) and later renamed to ECMAScript 2015, adds significant new syntax for writing complex applications, including classes and modules, iterators and for/of loops, generators, arrow functions, binary data, typed arrays, collections (maps, sets and weak maps), promises, number and math enhancements, reflection, and proxies.

In other words, ES6 is a superset of JavaScript (ES5). The reason that ES6 became so popular is that it introduced new conventions and OOP concepts such as classes.


## ES6 Promises

A Promise is a better way for asynchronous programming when compared to the common way of using a setTimeout() type of method.

Consider this example:

``` js
setTimeOut(function() {
    console.log("Work 1");
    setTimeOut(function() { console.log("Work 2");}, 1000);
    }, 1000);
console.log("End");

// End
// Work 1
// Work 2   
```


It prints "End", "Work 1" and "Work 2" in that order (the work is done asynchronously). But if there are more events like this, the code becomes very complex.

ES6 comes to the rescue in such situations. A promise can be created as follows:

``` js
new Promise(function(resolve, reject) {
    // Work
    if (success)
        resolve(result);
    else
        reject(Error("failure"));
}); 
```


Here, resolve is the method for success and reject is the method for failure.

If a method returns a promise, its calls should use the then method which takes two methods as input; one for success and the other for failure.

For Example:

``` js
function asyncFunc(work){
    return new Promise(function(resolve, reject) {
    if (work === "")
        reject(Error("failure"));        
    setTimeOut(function(){resolve(work);}, 1000);
});
}

asyncFunc("Work1")  //Task1
.then(function(result) {
   console.log(result);
   return asyncFunc("Work2");   //Task2
}, function(error) {
    console.log(error);
})
.then(function(result) {
   console.log(result);
}, function(error) {
    console.log(error);
});
console.log("End");

// End
// Work1    
// Work2        
```

It also prints "End", "Work 1" and "Work 2" (the work is done asynchronously). But, this is clearly more readable than the previous example and in more complex situations it is easier to work with.

## Iterators & Generators

Symbol.iterator is the default iterator for an object. The for...of loops are based on this type of iterator.

In the example below, we will see how we should implement it and how generator functions are used.
Example:

``` js
let myIterableObj = {
   [Symbol.iterator] : function* () {
        yield 1; yield 2; yield 3;
...
console.log([...myIterableObj]);

// [1, 2, 3]
```


First, we create an object, and use the Symbol.iterator and generator function to fill it with some values.

In the second line of the code, we use a * with the function keyword. It's called a generator function (or gen function).

For example, here is a simple case of how gen functions can be useful:

``` js
function* idMaker(){
    let index = 0;
    while (index < 5) {
       yield index++;
    }
}
var gen = idMaker();
console.log(gen.next().value);

// 0
```


We can exit and re-enter generator functions later. Their variable bindings (context) will be saved across re-entrances. They are a very powerful tool for asynchronous programming, especially when combined with Promises. They can also be useful for creating loops with special requirements.

We can nest generator functions inside each other to create more complex structures and pass them arguments while we are calling them.
The example below will show a useful case of how we can use generator functions and Symbol.iterators together.
Example:

``` js
const arr = ['0','1','4','a','9','c','16'];
const my_obj = {
     [Symbol.iterator] : function* () {
         for(let index of arr){
             yield `${index}`;
         }
     }
};
const all = [...my_obj]
    .map(i => parseInt(i,10))
    .map(Math.sqrt)
    .filter((i) => i < 5)
    .reduce((i, d) => i + d);
console.log(all);

// 3.1622776601683795
```

We create an object of 7 elements by using Symbol.iterator and generator functions. In the second part, we assign our object to a constant all. At the end, we print its value.

## Modules

It is a good practice to divide your related code into modules. Before ES6 there were some libraries which made this possible (e.g., RequireJS, CommonJS). ES6 is now supporting this feature natively.

Considerations when using modules:
The first consideration is maintainability. A module is independent of other modules, making improvements and expansion possible without any dependency on code in other modules.

The second consideration is namespacing. In an earlier lesson, we talked about variables and scope. As you know, vars are globally declared, so it's common to have namespace pollution where unrelated variables are accessible all over our code. Modules solve this problem by creating a private space for variables.

Another important consideration is reusability. When we write code that can be used in other projects, modules make it possible to easily reuse the code without having to rewrite it in a new project.

Let's see how we should use modules in JS files.
For Example:

``` js
// lib/math.js
export ​let sum = (x, y) => { return x + y; }
export ​let pi = 3.14

// app.j

import * ​as math from "lib/mat"
console.log(`2p = + ${math.sum(math.pi, math.pi)

// 6.28
```


Here we are exporting the sum function and the pi variable so we can use them in different files.
ES6 supports modules officially, however, some browsers are not supporting modules natively yet. So, we should use bundlers (builders) such as Webpack or Browserify to run our code.

## Built-in Methods

ES6 also introduced new built-in methods to make several tasks easier. Here we will cover the most common ones.

### Array Element Finding

The legacy way to find the first element of an array by its value and a rule was the following:


``` js

[4, 5, 8, 1, 2, 0].filter(function (x) {
     return x > 3;
})[0];
```


The new syntax is cleaner and more robust:


``` js

[4, 5, 8, 1, 2, 0].find(x => x > 3);
```


You can also get the index of the item above by using the findIndex() method:


``` js

[4, 5, 8, 1, 2, 0].findIndex(x => x > 3);
```


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

## What is ECMAScript?

**ECMAScript (often abbreviated ES)** is the standardized specification that defines the core of the JavaScript language.  
It is maintained by **ECMA International** through the **TC39 committee**.

JavaScript, along with other languages like JScript and ActionScript, is based on the ECMAScript standard to ensure consistent behavior across different environments.

---

# A Brief History of ECMAScript Versions

| Version | Year | Highlights |
|:--------|:-----|:-----------|
| **ES1** | 1997 | First official edition. |
| **ES2** | 1998 | Editorial updates for ISO/IEC standards. |
| **ES3** | 1999 | Regular expressions, `try/catch`, new control statements. |
| **ES4** | *Cancelled* | Too ambitious; replaced by a more incremental approach. |
| **ES5** | 2009 | `strict mode`, `JSON`, getters/setters, array extras (`forEach`, `map`, `filter`, etc.). |
| **ES5.1** | 2011 | Minor corrections to align with ISO standards. |
| **ES6 (ES2015)** | 2015 | Major update: classes, modules, `let`, `const`, promises, template literals, arrow functions. |
| **ES7 (ES2016)** | 2016 | `Array.includes()`, exponentiation operator (`**`). |
| **ES8 (ES2017)** | 2017 | `async/await`, `Object.values()`, `Object.entries()`, `padStart()`, `padEnd()`. |
| **ES9 (ES2018)** | 2018 | Asynchronous iteration (`for await...of`), object rest/spread, new regex features. |
| **ES10 (ES2019)** | 2019 | `Array.flat()`, `flatMap()`, `Object.fromEntries()`, `trimStart()`, `trimEnd()`. |
| **ES11 (ES2020)** | 2020 | Optional chaining (`?.`), nullish coalescing (`??`), `Promise.allSettled()`, `globalThis`, BigInt. |
| **ES12 (ES2021)** | 2021 | Logical assignment operators (`&&=`, `||=`, `??=`), numeric separators, `Promise.any()`. |
| **ES13 (ES2022)** | 2022 | Top-level `await`, class static blocks, `.at()` method, error cause. |
| **ES14 (ES2023)** | 2023 | `toSorted()`, `toReversed()`, `toSpliced()`, `with()`, `findLast()`, `findLastIndex()`. |
| **ES15 (ES2024)** | 2024 | `Set` methods (`union`, `intersection`, `difference`), `Array.groupBy()`, iterator helpers. |

---

## Detailed Version-by-Version Breakdown

### ECMAScript 1 (1997)
- First standardized version of JavaScript.
- Basic syntax and types were defined.

### ECMAScript 2 (1998)
- Editorial updates for international standardization.
- No major new features.

### ECMAScript 3 (1999)
- Introduced:
    - **Regular expressions**
    - **`try...catch`** error handling
    - **`do...while`**, **`switch`**, new control structures
- Became the widely adopted baseline version for years.

### ECMAScript 4 (Cancelled)
- Proposed major changes (like classes, modules, type annotations), but deemed too ambitious and abandoned.

### ECMAScript 5 (2009)
- Important modernizations:
    - **Strict Mode** (`"use strict"`)
    - **JSON support** (`JSON.parse()`, `JSON.stringify()`)
    - **Getters and setters**
    - Array methods: `forEach()`, `map()`, `filter()`, `reduce()`, `some()`, `every()`
    - Object methods: `Object.create()`, `Object.defineProperty()`

### ECMAScript 5.1 (2011)
- Small corrections and clarifications.

---

### ECMAScript 6 (2015) — A Major Milestone

**Key Features:**

| Feature | Description |
|:--------|:------------|
| `let`, `const` | Block-scoped variable declarations. |
| Arrow Functions | Concise anonymous functions (`(a) => a * 2`). |
| Template Literals | Embedded expressions inside strings. |
| Classes | Native syntax for OOP. |
| Destructuring | Unpacking values from arrays/objects. |
| Default Parameters | Default values in function parameters. |
| Rest/Spread Syntax | Expand/collect elements using `...`. |
| Promises | Native support for asynchronous workflows. |
| Modules | `import`/`export` syntax for modular JavaScript. |
| `Map`, `Set`, `WeakMap`, `WeakSet` | New data structures. |
| Symbols | New primitive for unique object keys. |
| Iterators and Generators | Build custom iterable sequences. |

---

### ECMAScript 7–15 (2016–2024): Yearly Improvements

#### ECMAScript 2016 (ES7)
- `Array.prototype.includes()`
- Exponentiation operator (`**`)

#### ECMAScript 2017 (ES8)
- `async/await` for asynchronous code.
- `Object.entries()`, `Object.values()`
- String padding: `padStart()`, `padEnd()`
- `SharedArrayBuffer`, `Atomics` for low-level memory handling.

#### ECMAScript 2018 (ES9)
- Object Rest/Spread (`{...obj}`)
- Asynchronous iteration (`for await...of`)
- New RegExp features: named capture groups, lookbehind.

#### ECMAScript 2019 (ES10)
- `Array.flat()`, `Array.flatMap()`
- `Object.fromEntries()`
- String `trimStart()`, `trimEnd()`
- Optional catch binding (`catch {}` without error param)

#### ECMAScript 2020 (ES11)
- Optional Chaining (`a?.b`)
- Nullish Coalescing (`a ?? b`)
- `Promise.allSettled()`
- `globalThis`
- Dynamic `import()`
- `BigInt`

#### ECMAScript 2021 (ES12)
- Logical assignment operators (`&&=`, `||=`, `??=`)
- Numeric separators (`1_000_000`)
- `Promise.any()`
- WeakRef and FinalizationRegistry (advanced memory control)

#### ECMAScript 2022 (ES13)
- Top-level `await`
- Class static initialization blocks
- `.at()` method for arrays/strings (`array.at(-1)`)
- `Error.cause`

#### ECMAScript 2023 (ES14)
- Immutable array methods:
  - `toSorted()`
  - `toReversed()`
  - `toSpliced()`
  - `with()`
- New find methods:
  - `findLast()`
  - `findLastIndex()`

#### ECMAScript 2024 (ES15)
- **New Set methods**:
    - `union()`, `intersection()`, `difference()`, `symmetricDifference()`
- **Array.groupBy()**:
    - Groups elements by a callback function.
- **Iterator Helpers**:
    - Methods like `map()`, `filter()`, `take()`, `drop()` on iterators.
- **Symbols as WeakMap keys**:
    - Symbols can now be used as keys in WeakMap/WeakSet.

---

# Conclusion

From the humble beginnings of **ES1** to the rich feature set of **ES15 (2024)**, ECMAScript continues to evolve and power JavaScript development across browsers, servers, and beyond.  
Keeping up with these changes ensures developers write **modern, robust, efficient** code that leverages the best features of the language.

---
