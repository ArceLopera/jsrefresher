# Classes in ES6

In this lesson we'll explain how to create a class that can be used to create multiple objects of the same structure.
A class uses the keyword class and contains a constructor method for initializing.

``` js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```


A declared class can then be used to create multiple objects using the keyword new.

``` js
const square = new Rectangle(5,5);
const poster = new Rectangle(2,3);
```


Class Declarations are not hoisted while Function Declarations are. If you try to access your class before declaring it, ReferenceError will be returned.

You can also define a class with a class expression, where the class can be named or unnamed.
A named class looks like:

``` js
var Square = class Rectangle {
      constructor(height, width){
           this.height = height;
           this.width = width
       }
};
```


In the unnamed class expression, a variable is simply assigned the class definition:

``` js
var Square = class {
      constructor(height, width){
           this.height = height;
           this.width = width
       }
};
```

The constructor is a special method which is used for creating and initializing an object created with a class. There can be only one constructor in each class.

### Class Methods in ES6

ES6 introduced a shorthand that does not require the keyword function for a function assigned to a method's name. One type of class method is the prototype method, which is available to objects of the class.

``` js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  get area(){
        return this.calcArea();
  }
  calcArea(){
        return this.height*this.width
  }
}
const square = new Rectangle(5,5);
console.log(square.area);  //25
```


In the code above, area is a getter, calcArea is a method.
Another type of method is the static method, which cannot be called through a class instance. Static methods are often used to create utility functions for an application.

``` js
class Point {
   constructor (x, y){
       this.x = x;
       this.y = y;
   }
   static distance(a, b) {
        const dx = a.x - b.x;
        const dy = a.y - b.y;
        return Math.hypot(dx, dy);
   }
}
const p1 = new Point(7, 2);
const p2 = new Point(3, 8);

console.log(Point.distance(p1,p2));

// 5.385164807134504
```

As you can see, the static distance method is called directly using the class name, without an object.

### Inheritance in ES6

The extends keyword is used in class declarations or class expressions to create a child of a class. The child inherits the properties and methods of the parent.

``` js
class Animal {
    constructor(name){
        this.name = name; 
    }
    speak(){
        console.log(this.name + 'makes noise');
    }
}

class Dog extends Animal {
     speak() {
        console.log(this.name + 'Woof!');
     }
}

let dog = new Dog('Sparky');
dog.speak();
```


In the code above, the Dog class is a child of the Animal class, inheriting its properties and methods.
If there is a constructor present in the subclass, it needs to first call super() before using this. Also, the super keyword is used to call parent's methods.
For example, we can modify the program above to the following:

``` js
class Animal {
    constructor(name){
        this.name = name; 
    }
    speak(){
        console.log(this.name + 'makes noise');
    }
}

class Dog extends Animal {
     speak() {
        super.speak();
        console.log(this.name + 'Woof!');
     }
}

let dog = new Dog('Sparky');
dog.speak();
```

In the code above, the parent's speak() method is called using the super keyword.

---
