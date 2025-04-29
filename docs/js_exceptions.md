
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

---
