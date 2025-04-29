# Control Flow
## For-Loops

A for loop executes a set of statements a specific number of times. The init and increment statements may be left out, if not needed, but remember that the semicolons are mandatory. 
for (; ;) {} is an infinite loop.

``` js
for ( var i=0; i <10;  i++ ) {
     //...;
}
```

## While-Loops

A while loop repeatedly executes a block of code as long as a given condition is true.

``` js
var num = 1;
while(num < 6 )
{
       console.log(num);
       num++;
}
```

## Do-While Loops

A do-while loop is similar to a while loop, except that a do-while loop is guaranteed to execute at least one time.

``` js
var a = 0;
do {
      console.log(a);
      a++;
}while( a < 5);
```

## Loops since ES6

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


## Conditionals
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
Use relational operators (Comparison Operators) to evaluate conditions. 

+ They only work when they’re comparing the same data type; numbers with numbers, strings with strings. 
+ In addition to the less than (<) and greater than (>) operators, the following operators are available: >=, <=, ==(Equal to), !=(Not Equal to), ===(Identical, Equal and same type), !==(Not identical).
+ Remember, that an if can have zero or more else if's and they must come before the last else, which is optional. Once an else if succeeds, none of the remaining else if's or else clause will be tested.

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

## Break and Continue
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

---
