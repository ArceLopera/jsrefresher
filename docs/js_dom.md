# The DOM

When you open any webpage in a browser, the HTML of the page is loaded and rendered visually on the screen.
To accomplish that, the browser builds the Document Object Model of that page, which is an object oriented model of its logical structure.

JavaScript can be used to manipulate the DOM of a page dynamically to add, delete and modify elements.
The DOM represents a document as a tree structure.
HTML elements become interrelated nodes in the tree.
All those nodes in the tree have some kind of relations among each other.
Nodes can have child nodes. Nodes on the same tree level are called siblings.

![dom](./Images/dom.png)

For the example above:

``` html
<html> has two children (<head>, <body>);
<head> has one child (<title>) and one parent (<html>);
<title> has one parent (<head>) and no children;
<body> has two children (<h1> and <a>) and one parent (<html>);
```

It is important to understand the relationships between elements in an HTML document in order to be able to manipulate them with JavaScript.

### The document Object

There is a predefined document object in JavaScript, which can be used to access all elements on the DOM.
In other words, the document object is the owner (or root) of all objects in your webpage.
So, if you want to access objects in an HTML page, you always start with accessing the document object.

For example:

``` js
document.body.innerHTML = "Some text";
```


As body is an element of the DOM, we can access it using the document object and change the content of the innerHTML property.
The innerHTML property can be used on almost all HTML elements to change its content.

### Selecting Elements


All HTML elements are objects. And as we know every object has properties and methods.
The document object has methods that allow you to select the desired HTML element.
These three methods are the most commonly used for selecting HTML elements:

``` js
//finds element by id
document.getElementById(id) 

//finds elements by class name
document.getElementsByClassName(name) 

//finds elements by tag name
document.getElementsByTagName(name)
```


In the example below, the getElementById method is used to select the element with id="demo" and change its content:

``` js
var elem = document.getElementById("demo");
elem.innerHTML = "Hello World!";
```


The example above assumes that the HTML contains an element with id="demo", for example `<div id="demo"></div>.`

The getElementsByClassName() method returns a collection of all elements in the document with the specified class name.
For example, if our HTML page contained three elements with class="demo", the following code would return all those elements as an array:

``` js
var arr =  document.getElementsByClassName("demo");
//accessing the second element
arr[1].innerHTML = "Hi";
```


Similarly, the getElementsByTagName method returns all of the elements of the specified tag name as an array.
The following example gets all paragraph elements of the page and changes their content:

``` js
<p>hi</p>
<p>hello</p>
<p>hi</p>
<script>
var arr = document.getElementsByTagName("p");
for (var x = 0; x < arr.length; x++) {
  arr[x].innerHTML = "Hi there";
}
</script>
```

The script will result in the following HTML:

``` js
<p>Hi there</p>
<p>Hi there</p>
<p>Hi there</p>
``` 

We used the length property of the array to loop through all the selected elements in the above example.

### Working with DOM

Each element in the DOM has a set of properties and methods that provide information about their relationships in the DOM:

+ element.childNodes returns an array of an element's child nodes.
+ element.firstChild returns the first child node of an element.
+ element.lastChild returns the last child node of an element.
+ element.hasChildNodes returns true if an element has any child nodes, otherwise false.
+ element.nextSibling returns the next node at the same tree level.
+ element.previousSibling returns the previous node at the same tree level.
+ element.parentNode returns the parent node of an element.

We can, for example, select all child nodes of an element and change their content:

``` html
<html>
     <body>
            <div id="demo">hi
               <p>hi</p>
               <p>hello</p>
            </div>
            <script>
                   var a = document.getElementsById("demo");
	             var arr = a.childNodes;
                   for (var x = 0; x < arr.length; x++) {
                        arr[x].innerHTML = "Hi there";
                   }
             </script>
    </body>
</html>
```


### Changing Elements

Once you have selected the element(s) you want to work with, you can change their attributes.
As we have seen in the previous lessons, we can change the text content of an element using the innerHTML property.
Similarly, we can change the attributes of elements.
For example, we can change the src attribute of an image:

``` html
<img id="myimg" src="orange.png" alt="" />
<script>
var el = document.getElementById("myimg");
el.src = "apple.png";
</script>
```


We can change the href attribute of a link:

``` html
<a href="http://www.google.com/">Some URL</a>
<script>
var el=document.getElementByTagName("a");
el[0].href="http://myurl.com/";
</script>
```

The style of HTML elements can also be changed using JavaScript.
All style attributes can be accessed using the style object of the element.
All CSS properties can be set and modified using JavaScript. Just remember, that you cannot use dashes (-) in the property names: these are replaced with camelCase versions, where the compound words begin with a capital letter.
For example: the background-color property should be referred to as backgroundColor.

``` html
<div id="demo" style="width:200px"> Some text</div>
<script>
var el = document.getElementById("demo");
el.style.color = "6600FF";
el.style.width = "100px";
</script>
```


### Creating Elements

Use the following methods to create new nodes:

+ element.cloneNode() clones an element and returns the resulting node.
+ document.createElement(element) creates a new element node.
+ document.createTextNode(text) creates a new text node.

``` html
var node = document.createTextNode("Some new text");
```


This will create a new text node, but it will not appear in the document until you append it to an existing element with one of the following methods:

+ element.appendChild(newNode) adds a new child node to an element as the last child node.
+ element.insertBefore(node1, node2) inserts node1 as a child before node2.

``` html
<div id="demo"> Some Text </div>
<script>
    //create a new paragraph
    var p = document.createElement("p");
    var node = document.createTextNode("Some new text");
    //adding the text to paragraph
    p.appendChild(node);
    
    var div = document.getElementById("demo");
    //adding  the paragraph  to the div 
    div.appendChild(p);
</script>
```


To remove an HTML element, you must select the parent of the element and use the removeChild(node) method.
An alternative way of achieving the same result would be the use of the parentNode property to get the parent of the element we want to remove:

``` html
var child = document.getElementById("p1");
child.parentNode.removeChild(child);
```

To replace an HTML element, the element.replaceChild(newNode, oldNode) method is used.

### Animations

To create an animation, we need to change the properties of an element at small intervals of time. We can achieve this by using the setInterval() method, which allows us to create a timer and call a function to change properties repeatedly at defined intervals (in milliseconds).

For example:

``` js
var t = setInterval(move, 500); 
```

This code creates a timer that calls a move() function every 500 milliseconds.
Now we need to define the move() function, that changes the position of the box.

``` js
// starting position
var pos = 0; 
//our box element
var box = document.getElementById("box");

function move() {
  pos += 1;
  box.style.left = pos+"px"; //px = pixels
}
```


The move() function increments the left property of the box element by one each time it is called.

The following code defines a timer that calls the move() function every 10 milliseconds:

``` js
var t = setInterval(move, 10);
```

However, this makes our box move to the right forever. To stop the animation when the box reaches the end of the container, we add a simple check to the move() function and use the clearInterval() method to stop the timer.

``` js
function move() {
  if(pos >= 150) {
    clearInterval(t);
  }
  else {
    pos += 1;
    box.style.left = pos+"px";
  }
}
```

When the left attribute of the box reaches the value of 150, the box reaches the end of the container, based on a container width of 200 and a box width of 50.

### Events

You can write JavaScript code that executes when an event occurs, such as when a user clicks an HTML element, moves the mouse, or submits a form.
When an event occurs on a target element, a handler function is executed.
Common HTML events:

|Event|Description|
|---|---|
|onchange|	An HTML element has been changed|
|onclick|	The user clicks an HTML element|
|onmouseover|	The user moves the mouse over an HTML element|
|onmouseout|	The user moves the mouse away from an HTML element|
|onkeydown|	The user pushes a keyboard key|
|onload|	The browser has finished loading the page|

Corresponding events can be added to HTML elements as attributes.
For example: 

``` html
<p onclick="someFunc()">some text</p>
```

#### Handling Events

Let's display an alert popup when the user clicks a specified button:

``` html
<button onclick="show()">Click Me</button>
<script>
function show(){
    alert("hello");
}
</script>
```


Event handlers can be assigned to elements.
For example:

``` html
var x=document.getElementById("demo");
x.onclick = function () {
       document.body.innerHTML = Date();
}
```



The onload and onunload events are triggered when the user enters or leaves the page. These can be useful when performing actions after the page is loaded.

``` html
<body onload="doSomething()">
```


Similarly, the window.onload event can be used to run code after the whole page is loaded.

``` js
window.onload ​= function() {

  ​//some code
}
```


The onchange event is mostly used on textboxes. The event handler gets called when the text inside the textbox changes and focus is lost from the element.



#### Event Listeners

The addEventListener() method attaches an event handler to an element without overwriting existing event handlers. You can add many event handlers to one element.
You can also add many event handlers of the same type to one element, i.e., two "click" events.

``` js
element.addEventListener(event, function, useCapture);
```


+ The first parameter is the event's type (like "click" or "mousedown").
+ The second parameter is the function we want to call when the event occurs.
+ The third parameter is a Boolean value specifying whether to use event bubbling or event capturing. This parameter is optional, and will be described in the next lesson.

Note that you don't use the "on" prefix for this event; use "click" instead of "onclick".

Example:

``` js
element.addEventListener("click", myFunction);
element.addEventListener("mouseover", myFunction);

function myFunction() {
  alert("Hello World!");
}
```


This adds two event listeners to the element.
We can remove one of the listeners:

``` js
element.removeEventListener("mouseover", myFunction);
```

Internet Explorer version 8 and lower do not support the addEventListener() and removeEventListener() methods. However, you can use the `document.attachEvent()` method to attach event handlers in Internet Explorer.

#### Event Propagation

There are two ways of event propagation in the HTML DOM: bubbling and capturing.


Event propagation allows for the definition of the element order when an event occurs. If you have a `<p>` element inside a `<div>` element, and the user clicks on the `<p>` element, which element's "click" event should be handled first?

In bubbling, the innermost element's event is handled first and then the outer element's event is handled. The `<p>` element's click event is handled first, followed by the `<div>` element's click event.

In capturing, the outermost element's event is handled first and then the inner. The `<div>` element's click event is handled first, followed by the `<p>` element's click event.
Capturing goes down the DOM.
Bubbling goes up the DOM.

#### Capturing vs. Bubbling

The addEventListener() method allows you to specify the propagation type with the "useCapture" parameter.

``` js
addEventListener(event, function, useCapture)
```

The default value is false, which means the bubbling propagation is used; when the value is set to true, the event uses the capturing propagation.

``` js
//Capturing propagation
elem1.addEventListener("click", myFunction, true); 

//Bubbling propagation
elem2.addEventListener("click", myFunction, false);
```


This is particularly useful when you have the same event handled for multiple elements in the DOM hierarchy.

##### Image Slider - Example


Now we need to handle the Next and Prev button clicks and call the corresponding functions to change the image. js

``` html
HTML:
<div>
  <button onclick="prev()"> Prev </button>
  <img id="slider" src="http://www.mysite.com/uploads/slider/1.jpg" 
    width="200px" height="100px"/>
  <button onclick="next()"> Next </button>
</div>
```

``` js
//JS:
var images = [
   "http://www.mysite.com/uploads/slider/1.jpg", 
   "http://www.mysite.com/uploads/slider/2.jpg", 
   "http://www.mysite.com/uploads/slider/3.jpg"
];

var num=0;
function next() {
     var slider = document.getElementById("slider");
     num++;
     if(num >=images.length){
           num=0;
    }
    slider.src = images[num];
}

function prev(){
     var slider = document.getElementById("slider");
     num--;
     if(num < 0){
           num=images.length -1;
    }
    slider.src = images[num];
}
```
##### Form Validation


HTML5 adds some attributes that allow form validation. For example, the required attribute can be added to an input field to make it mandatory to fill in.
More complex form validation can be done using JavaScript.
The form element has an onsubmit event that can be handled to perform validation.
For example, let's create a form with two inputs and one button. The text in both fields should be the same and not blank to pass the validation.

``` html
<form onsubmit="return validate()" method="post">
  Number: <input type="text" name="num1" id="num1" />
  <br />
  Repeat: <input type="text" name="num2" id="num2" />
  <br />
  <input type="submit" value="Submit" />
</form>
```

``` js
function validate() {
    var n1 = document.getElementById("num1");
    var n2 = document.getElementById("num2");
    if(n1.value != "" && n2.value != ""){
                if(n1.value == n2.value){
                       return true;
                }
    }
    alert("The values should be equal and not blank");
    return false;

}
```

The form will not get submitted if its onsubmit event returns false