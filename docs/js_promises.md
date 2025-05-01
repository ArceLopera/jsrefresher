
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