
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

---


### Array Destructuring in ES6

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

---

## ES6 Collections

### ES6 Map

A Map object can be used to hold key/value pairs. A key or value in a map can be anything (objects and primitive values).

The syntax new Map([iterable]) creates a Map object where iterable is an array or any other iterable object whose elements are arrays (with a key/value pair each).

An Object is similar to Map but there are important differences that make using a Map preferable in certain cases:

1. The keys can be any type including functions, objects, and any primitive.
2. You can get the size of a Map.
3. You can directly iterate over Map.
4. Performance of the Map is better in scenarios involving frequent addition and removal of key/value pairs.

The size property returns the number of key/value pairs in a map.

``` js
let map = new Map([['k1','v1'],['k2','v2']]);
Console.log(map.size);   //2
```


##### Methods

+ set(key, value) Adds a specified key/value pair to the map. If the specified key already exists, value corresponding to it is replaced with the specified value.
+ get(key) Gets the value corresponding to a specified key in the map. If the specified key doesn't exist, undefined is returned.
+ has(key) Returns true if a specified key exists in the map and false otherwise.
+ delete(key) Deletes the key/value pair with a specified key from the map and returns true. Returns false if the element does not exist.
+ clear() Removes all key/value pairs from map.
+ keys() Returns an Iterator of keys in the map for each element.
+ values() Returns an Iterator of values in the map for each element.
+ entries() Returns an Iterator of array[key, value] in the map for each element.

``` js
let map = new Map();
map.set('k1','v1').set('k2','v2');
console.log(map.get('k1'));    // v1
console.log(map.has('k2'));    // true

for(let kv of map.entries()){
     console.log(kv[0] + " : " + kv[1]);
}

// k1 : v1
// k2 : v2
```

The above example demonstrates some of the ES6 Map methods.
Map supports different data types i.e. 1 and "1" are two different keys/values.

### ES6 Set

A Set object can be used to hold unique values (no repetitions are allowed).
A value in a set can be anything (objects and primitive values).

The syntax new Set([iterable]) creates a Set object where iterable is an array or any other iterable object of values.

The size property returns the number of distinct values in a set.
For example:

``` js
let set = new Set([1, 2, 4, 2, 59, 9, 4, 9, 1]);
console.log(set.size);   //5
```


##### Methods

+ add(value) Adds a new element with the given value to the Set.
+ delete(value) Deletes a specified value from the set.
+ has(value) Returns true if a specified value exists in the set and false otherwise.
+ clear() Clears the set.
+ values() Returns an Iterator of values in the set.

``` js
let set = new Set();

set.add(5).add(9).add(59).add(9);
console.log(set.has(9));

for(let v of set.values()){
    console.log(v);
}

// 5
// 9
// 59
```

Set supports different data types i.e. 1 and "1" are two different values.
NaN and undefined can also be stored in Set.

---