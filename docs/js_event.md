# Events

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

## Handling Events

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



## Event Listeners

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

## Event Propagation

There are two ways of event propagation in the HTML DOM: bubbling and capturing.


Event propagation allows for the definition of the element order when an event occurs. If you have a `<p>` element inside a `<div>` element, and the user clicks on the `<p>` element, which element's "click" event should be handled first?

In bubbling, the innermost element's event is handled first and then the outer element's event is handled. The `<p>` element's click event is handled first, followed by the `<div>` element's click event.

In capturing, the outermost element's event is handled first and then the inner. The `<div>` element's click event is handled first, followed by the `<p>` element's click event.
Capturing goes down the DOM.
Bubbling goes up the DOM.

## Capturing vs. Bubbling

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

### Image Slider - Example


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
### Form Validation


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