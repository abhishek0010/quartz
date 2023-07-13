---
title: Javascript Classes
tags: 
- javascript
---
-----------------
Date Created : `21-01-2023`

Tags: #javascript, #publish 


----------------------------
# `Javascript Classes`.
## Introduction
So, what exactly is a `class`? That’s not an entirely new language-level entity, as one might think.

Let’s unveil any magic and see what a class really is. That’ll help in understanding many complex aspects.

In JavaScript, a class is a kind of function.

Here, take a look:

```javascript
class User {
  constructor(name) { this.name = name; }
  sayHi() { alert(this.name); }
}

// proof: User is a function
alert(typeof User); // function
```

## Not just a syntactic sugar

Sometimes people say that `class` is a “syntactic sugar” (syntax that is designed to make things easier to read, but doesn’t introduce anything new), because we could actually declare the same thing without using the `class` keyword at all:

```javascript
// rewriting class User in pure functions

// 1. Create constructor function
function User(name) {
  this.name = name;
}
// a function prototype has "constructor" property by default,
// so we don't need to create it

// 2. Add the method to prototype
User.prototype.sayHi = function() {
  alert(this.name);
};

// Usage:
let user = new User("John");
user.sayHi();
```

The result of this definition is about the same. So, there are indeed reasons why `class` can be considered a syntactic sugar to define a constructor together with its prototype methods.

Still, there are important differences.

1.  First, a function created by `class` is labelled by a special internal property `[[IsClassConstructor]]: true`. So it’s not entirely the same as creating it manually.
    
    The language checks for that property in a variety of places. For example, unlike a regular function, it must be called with `new`:
    
    ```javascript
    class User {
      constructor() {}
    }
    
    alert(typeof User); // function
    User(); // Error: Class constructor User cannot be invoked without 'new'
    ```
    
    Also, a string representation of a class constructor in most JavaScript engines starts with the “class…”

    ```javascript
    class User {
      constructor() {}
    }
    
    alert(User); // class User { ... }
    ```
    
    There are other differences, we’ll see them soon.
    
2.  Class methods are non-enumerable. A class definition sets `enumerable` flag to `false` for all methods in the `"prototype"`.
    
    That’s good, because if we `for..in` over an object, we usually don’t want its class methods.
    
3.  Classes always `use strict`. All code inside the class construct is automatically in strict mode.

What `class User {...}` construct really does is:

1.  Creates a function named `User`, that becomes the result of the class declaration. The function code is taken from the `constructor` method (assumed empty if we don’t write such method).
2.  Stores class methods, such as `sayHi`, in `User.prototype`.
## Features
-   Classes create objects through the [`new`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new) operator.
-   Each object has some properties (data or method) added by the class.
-   The class stores some properties (data or method) itself, which are usually used to interact with instances.
```javascript
class MyClass {
  // Constructor
  constructor() {
    // Constructor body
  }
  // Instance field
  myField = "foo";
  // Instance method
  myMethod() {
    // myMethod body
  }
  // Static field
  static myStaticField = "bar";
  // Static method
  static myStaticMethod() {
    // myStaticMethod body
  }
  // Static block
  static {
    // Static initialization code
  }
  // Fields, methods, static fields, and static methods all have
  // "private" forms
  #myPrivateField = "bar";
}
```
- The folowing code is equivalent to
```javascript
function MyClass() {
  this.myField = "foo";
  // Constructor body
}
MyClass.myStaticField = "bar";
MyClass.myStaticMethod = function () {
  // myStaticMethod body
};
MyClass.prototype.myMethod = function () {
  // myMethod body
};

(function () {
  // Static initialization code
})();
```
## Class Expression
Here is an example
```javascript
const MyClass = class MyClassLongerName {
  // Class body. Here MyClass and MyClassLongerName point to the same class.
};
new MyClassLongerName(); // ReferenceError: MyClassLongerName is not defined
```
## Constructor
Can be a of three types:
- Default constructor with no argument
- parameterized constructor with some argument/s
- custom constructor without es6 syntactic sugar
```javascript
class Color {
  constructor(r, g, b) {
    // Assign the RGB values as a property of `this`.
    this.values = [r, g, b];
  }
}

//Equivalent to

function createColor(r, g, b) {
  return {
    values: [r, g, b],
  };
}

```
## Instance Methods
```javascript
class Color {
  constructor(r, g, b) {
    this.values = [r, g, b];
  }
  getRed() {
    return this.values[0];
  }
}

const red = new Color(255, 0, 0);
console.log(red.getRed()); // 255
```
- Method within constructors also works but it wastes memory
## Private Fields
- use `#value` within class to declare private fields
- Can `only be accessed and modified by class methods`
- `One instance` of the same class `can access` private `fields of other instance`
- Same private field` cant be declared twice`
- Methods, getters and setters can be private as well and can be useful for internal methods which needs to be encapsulated
## Static  Properties
- [_Static properties_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static) are a group of class features that are `defined on the class itself,` rather than on individual instances of the class. 
- These features include:
	- `Static methods`
	- `Static fields`
	- `Static getters and setters`
- Similar to java static in which `no need to instanciate a class to use static members`, infact here `instances cannot access them`
- They are not accessible from instances.
There is also a special construct called a [_static initialization block_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Static_initialization_blocks), which is a block of code that runs when the class is first loaded.

```javascript
class MyClass {
  static const a = 10;
  constructor() {
	  this.b = 20;
  }
  static {
    MyClass.myStaticProperty = "foo";
  }
}

console.log(MyClass.myStaticProperty); // 'foo'

let newClass = new MyClass();
console.log(newClass.a);//THrows error since a is a static member
```

## Extends & Inheritence
- The derived class has access to all public properties of the parent class. 
- Any constructor that can be called with [`new`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new) and has the [`prototype`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/prototype) property can be the candidate for the parent class.
- In JavaScript, derived classes are declared with an [`extends`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends) clause, which indicates the class it extends from.
```javascript
class Color {
  #values;
  constructor(r, g, b, a = 1) {
    this.#values = [r, g, b, a];
  }
  get alpha() {
    return this.#values[3];
  }
  set alpha(value) {
    if (value < 0 || value > 1) {
      throw new RangeError("Alpha value must be between 0 and 1");
    }
    this.#values[3] = value;
  }
}

class ColorWithAlpha extends Color {
  #alpha;
  constructor(r, g, b, a) {
    super(r, g, b);
    this.#alpha = a;
  }
  get alpha() {
    return this.#alpha;
  }
  set alpha(value) {
    if (value < 0 || value > 1) {
      throw new RangeError("Alpha value must be between 0 and 1");
    }
    this.#alpha = value;
  }
}
```

There are a few things that have immediately come to attention.
	 - First is that in the constructor, we are calling `super(r, g, b)`. It is a language requirement to call [`super()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super) before accessing `this`. 
	 - The `super()` call calls the parent class's constructor to initialize `this` — here it's roughly equivalent to `this = new Color(r, g, b)`. 
	 - You can have code before `super()`, but you cannot access `this` before `super()` — the language prevents you from accessing the uninitialized `this`.

- `Derived classes can also override methods from the parent class.`

- Within derived classes, you can `access the parent class's methods` by using `super`. This allows you to build enhancement methods and avoid code duplication.

- When you use `extends`, the `static methods` inherit from each other as well, so you `can also override` or enhance them. `This is opposite in case of JAVA where static members cannot be overriden.
`
- `Derived `classes `don't have access` to the `parent` class's `private fields`

- A class can only extend from one class.




---
References:
- 