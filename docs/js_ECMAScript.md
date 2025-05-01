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
