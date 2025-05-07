# The Concept of Web Stacks

Often you will hear programmers referring to various stacks in web development. In the last several years we have seen the proliferation of many stacks, including:

+ MEAN (Mongo, Express, Angular and Node)
+ LAMP (Linux, Apache, MySQL and PHP)
+ Python-Django
+ Ruby on Rails
+ .NET

It’s important to understand that these stacks are constantly being invented, reinvented, iterated upon, and mixed with other stacks. The MEAN stack evolved into the PEAN or NEAP stack when some developers started switching back to using Postgresql instead of Mongo for the database resource related to that particular stack.

Stack is not a technical term. It is a loose term and can be very fluid and sometimes even subjective. It is important, however, to be able to articulate which stacks you feel most comfortable with when you become a full stack developer.

For example, a TypeScript based stack can use Angular and NestJS, one of the newer stacks in web development.

JavaScript and TypeScript can be used in BOTH the front and the back-end of the stack.

## JavaScript and TypeScript throughout the Stack

JavaScript became a popular full stack tool in 2009 after NodeJS was released. Prior to the release of NodeJS, JavaScript was seen as primarily a front-end only tool used for creating widgets, user activity on a page, DOM (web page structure) manipulation and other front-end only tasks. After NodeJS was released, JavaScript was seen as a great tool for creating back-ends and front-ends alike.

TypeScript was released in 2012 by Microsoft because many JavaScript developers had expressed the desire for more structure and clear data types, especially for use in large scale applications. TypeScript has some features like static variable typing and interfaces that are present in well-respected legacy languages like Java and C#.

TypeScript is a superset of JavaScript. What this means is that TypeScript is transpiled into JavaScript. It’s literally translated into JavaScript code when it is compiled and before it is run.

TypeScript is Translated into JavaScript. That’s an important concept to remember! It therefore made logical sense, upon the release of NestJS, that TypeScript could be used throughout the entire web application stack just like JavaScript had been.
One of the creators of Typescript was Microsoft employee Anders Hejlsberg, the creator of C#.

## XHR

The next concept to understand is the request / response nature of full stack applications.

In a restaurant, the food request comes from the dining room, or the front-end.

The customer makes a request to the kitchen. In web applications, this typically comes in the form of an XML/HTTP Request or an XHR.

Let’s break down that term: "XML/HTTP" request. Although the term itself is already showing its age (we don’t use XML as much to send data over the web; JSON is used instead in most instances now), the second part of that term, HTTP, is critically important.

HTTP stands for HyperTextTransfer Protocol and is the foundation of all communication on the web. Think of HTTP as the way in which all web based technologies must communicate with each other.
You can analyze XHR for any website in the browser’s network tab in Chrome developer tools.

### HTTP Error Codes

Yes, XML/HTTP requests can be rejected by the server!

If rejected, the web application server sends an HTTP response back to the client (the front-end). Possible HTTP error status codes are:

+ 404 (not found)
+ 403 (forbidden)
+ 401 (not authorized)
+ 500 (internal server error)
+ 503 (service unavailable)

There are many more HTTP status codes, and they are generally categorized by the first digit in the status code.
Server and client are very common terms in computing. The "server" in full stack development typically refers to web application server, and the client refers to any device that is interacting with the server on the front-end. Common clients include laptop and desktop computers, mobile phones, GPS systems in cars, voice-driven devices like Amazon Alexa, Siri and Google Home, video game consoles, smart watches, and anything else that connects to a back-end.

### HTTP Success Codes

All of the 200 level codes are generally positive status codes:

+ 200 (ok)
+ 201 (created)
+ 202 (accepted), etc.

By contrast, 400 level status codes generally indicate an issue with the request itself, and 500 level status codes generally indicate an error on the back-end.

If the initial request has been accepted by the web application server, and there is a need to retrieve data related to the request, the web application server then queries a database or databases to get the information needed to send back to the user.

The database sends the result of the query back to the web application server, and then the web application server usually formats the data into a format to be sent back to the front-end. JSON (JavaScript Object Notation) is a very common format currently used to send data to clients (the front-end).
200 level codes are positive, 400 level codes are issues and 500 level codes are errors.

### The Angular / NEST flow

As an example, we can think of using TypeScript, a superset of JavaScript, to be building a full stack app called TS Flights that allows users to search for plane flights. The app will also have a page that allows you as an admin to enter new flights to show up in future searches.
On the front-end we will be using Angular. On the back-end we will be using NestJS.
For something like searching for a flight or adding a new flight into the database, our Angular front-end app will make requests to our NestJS back-end using XHR.

If the request is rejected, it will return a negative HTTP status code back to Angular. If the request is accepted, it will then proceed to do the work that it was sent to do...which may include getting all of the flights from New York to Paris or something of that nature.

If the request was accepted and includes a database call, NestJS will make a database query to our database, get the result, and if that database query is a success, return the JSON response to our Angular app with a 200 level status code.

Our Angular app will then use HTML and CSS to make the response pretty so that our users can see all of the flights to Paris on their phone or computer.

You should be able to see with this flow that the user initiates the process on the client, the request goes back to the server, does its work, and then ends up returning back to the client for the end of the process.
Request/response cycles can be incredibly complex, but this very simple flow is the beginning of understanding the volleys between the front and the back end.

