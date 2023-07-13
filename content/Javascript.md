---
title: Javascript
tags: 
- languages
- javascript
---
<div>

# Javascripts notes

</div>

-----------------
Date Modified : `16-12-2022`

Tags: #javascript  #languages #publish


----------------------------
# `Javascript.

## To Prepare
Frameworks Explainers:
- [[ReactJS]]
- [[NextJS]]

Package Managers:
- [[npm]]
- [[yarn]]

Bundler:
- [[webpack]]
- [[ViteJS]]

Packages notes:
- [[ESLint]]
- [[NX]]

CSS 
- [[PostCSS]]

Testing [Automated testing with Mocha](https://javascript.info/testing-mocha)
- Mocha
- Chai
- Sinon

## TO LEARN
- Decorators [Decorators and forwarding, call/apply](https://javascript.info/call-apply-decorators)
- factories
- template literals [Template literals (Template strings) - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_templates)
- [Garbage collection](https://javascript.info/garbage-collection)


## Summarize
- [Constructor, operator "new"](https://javascript.info/constructor-new) Using Typescript instead
- [Symbol type](https://javascript.info/symbol) Another type to create unique string, not accessable by object property iterator
- 
## Introduction
JavaScript is a _synchronous_ [[programming language]]. But thanks to callback functions we can make it function like an _asynchronous_ programming language.

Good resources that show the current state of support for various features:

-   [https://kangax.github.io/compat-table/es6/](https://kangax.github.io/compat-table/es6/) – for pure JavaScript.
-   [https://caniuse.com/](https://caniuse.com/) – for browser-related functions.
## Syntax
Syntax can be found in [[Syntax-JS]]

## Variable Declaration & Types
- `var` has global scope outside and within blocks
- Use `let` & `const` which create [temporal dead zones](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#temporal_dead_zone_tdz) , which throws `ReferenceError`, when used outside scope. Different from `var` which throws `undefined` as value.
### var vs let, const
- **`var` has no block scope(like if , for blocks etc)**, it has `function and global scope` but it ignore block scope, unlinke `let` & `const` (For this reasom IIEF were used to block scope of `var`)
- **`var` tolerates redeclerations**, unlike `let ` & `const` which throws redecleration errors
- **`var`  variables can be used before initializations** (also called `hoisting`) which is dangerous if declared in block scope. NOTE -  d`eclerations are hoisted but initializations are not.`
- Convention to use `camelCase` for let and `UPPER_CASE` for const.

### Primitive Types
There are 8 data types:

-   `number` for both floating-point and integer numbers,
-   `bigint` for integer numbers of arbitrary length,
-   `string` for strings,
-   `boolean` for logical values: `true/false`,
-   `null` – a type with a single value `null`, meaning “empty” or “does not exist”,
-   `undefined` – a type with a single value `undefined`, meaning “not assigned”,
-   `object` and `symbol` – for complex data structures and unique identifiers, we haven’t learnt them yet.

The `typeof` operator returns the type for a value, with two exceptions:

```javascript
typeof null == "object" // error in the language
typeof function(){} == "function" // functions are treated specially
```
### Wrapper for primitives(Refer [[Data Types in JS]])

- Except `undefined` & `null`, all other primitive types have wrapper methods.
-   Formally, these methods work via temporary objects, but JavaScript engines are well tuned to optimize that internally, so they are not expensive to call.
## Types of quotes
- `' '` & `" "` are normal quotes, where ` `` ` used for functional expressions.
- Mainly used for strings, refer [[Data Types in JS#^aca574]]

## Type Conversions
The three most widely used type conversions are to string, to number, and to boolean.

**`String Conversion`** – Occurs when we output something. Can be performed with `String(value)`. The conversion to string is usually obvious for primitive values.

**`Numeric Conversion`** – Occurs in math operations. Can be performed with `Number(value)`.

The conversion follows the rules:
- `undefined` = `NaN`
- `null` = `0`
- `true / false` = `1 / 0`
- `string` = The string is read “as is”, whitespaces (includes spaces, tabs `\t`, newlines `\n` etc.) from both sides are ignored. An empty string becomes `0`. An error gives `NaN`.

**`Boolean Conversion`** – Occurs in logical operations. Can be performed with `Boolean(value)`.

Follows the rules:
- `0`, `null`, `undefined`, `NaN`, `""` = `false`
- any other value = `true`

Most of these rules are easy to understand and memorize. The notable exceptions where people usually make mistakes are:

-   `undefined` is `NaN` as a number, not `0`.
-   `"0"` and space-only strings like `" "` are true as a boolean.

## Comparison and Difference Between == and === in Javascript

S.no |  == | === 
-----|-----|----
1 |Compares two operands | Compares two operands
2 | returns _true_ if operands have the same data type and same value, returns _false_ if the values differ. | returns _true_ only if operands are of same data type and same value, otherwise returns _false_
3 | In case both operands are of different data types, it performs type conversion of one operand in order to make the data types of the operands the same. | In case both operands are of different data type, it doesn't perform type conversion of the operands.
4 | Also known as _loose equality_ | Also known as _strict equality_
5 | Follows abstract equality comparison algorithm | Follows strict equality comparison algorithm

## `&&` , `||` & `??`
- Returns first falsy value
- returns first truthy value
- refurns first defined value

## Objects
### Introduction
- Objects are `collection of properties.`(Like a key value pair)
- An object can be created with figure brackets `{…}` with an optional list of _properties_. A property is a “key: value” pair, where `key` is a string (also called a “property name”), and `value` can be anything.
- An `empty object` can be created using one of two syntaxes:
```javascript
let user = new Object(); // "object constructor" syntax
let user = {};  // "object literal" syntax
```
- Its `property can also contain another object`
- Properties can be accessed using `.` notation
- To remove a property, we can use the `delete` operator:
```javascript
delete user.age;
```
- The last property in the list may end with a `comma:`

```javascript
let user = {
  name: "John",
  age: 30,
}
```

That is called a “trailing” or “hanging” comma. Makes it easier to add/remove/move around properties, because all lines become alike.
- We can use both normal properties and `shorthands` in the same object:

```javascript
let user = {
  name,  // same as name:name
  age: 30
};
```

- All objects have [[Javascript Prototypes]]

- Nonexistent properties of an object have value [`undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined) (and not [`null`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/null)).
- `in`  & `for..in` keywords are used for accessing object properties. Refer [[Syntax-JS#^696138]]
- Methods can also be added as properties of an object
- Prototypes can act as an inheritence feature
- GEters and setters can also be added within a method

### Object Copying and Referencing
- **A variable assigned to an object stores not the object itself, but its “address in memory” – in other words “a reference” to it.**
- **When an object variable is copied, the reference is copied, but the object itself is not duplicated.**

### Object cloning and merging, `Object.assign`
```javascript
let user = {
  name: "John",
  age: 30
};

let clone = {}; // the new empty object

// let's copy all user properties into it
for (let key in user) {
  clone[key] = user[key];
}

// now clone is a fully independent object with the same content
clone.name = "Pete"; // changed the data in it

alert( user.name ); // still John in the original object
```

We also can use `Object.assign` to perform a simple object cloning:

```javascript
let user = {
  name: "John",
  age: 30
};

let clone = Object.assign({}, user);

alert(clone.name); // John
alert(clone.age); // 30
```
There are also other methods of cloning an object, e.g. using the [spread syntax](https://javascript.info/rest-parameters-spread) `clone = {...user}`, covered later in the tutorial.
### Multi word keys(`[]` notation)
#### Introduction
- We can `also use multiword property names, but then they must be quoted`
- `Square brackets` also provide a way to obtain the property name as the result of any expression – as opposed to a literal string – like from a variable as follows:
```javascript
let key = "likes birds";

// same as user["likes birds"] = true;
user[key] = true;
```
Here, the variable `key` may be calculated at run-time or depend on the user input. And then we use it to access the property. That gives us a great deal of flexibility.

For instance:

```javascript
let user = {
  name: "John",
  age: 30
};

let key = prompt("What do you want to know about the user?", "name");

// access by variable
alert( user[key] ); // John (if enter "name")
```

The dot notation cannot be used in a similar way:
```javascript
let user = {
  name: "John",
  age: 30
};

let key = "name";
alert( user.key ) // undefined
```
#### Computed Properties
We can use square brackets in an object literal, when creating an object. That’s called _computed properties_.

For instance:
```javascript
let fruit = prompt("Which fruit to buy?", "apple");

let bag = {
  [fruit]: 5, // the name of the property is taken from the variable fruit
};

alert( bag.apple ); // 5 if fruit="apple"
```
We can use more complex expressions inside square brackets:

```javascript
let fruit = 'apple';
let bag = {
  [fruit + 'Computers']: 5 // bag.appleComputers = 5
};
```

Square brackets are much more powerful than dot notation. They allow any property names and variables. But they are also more cumbersome to write.

So most of the time, when property names are known and simple, the dot is used. And if we need something more complex, then we switch to square brackets.

#### BEWARE:
- Beware of using `square brackets `to access properties whose names are given by external input. This may make your code susceptible to [object injection attacks](https://github.com/nodesecurity/eslint-plugin-security/blob/main/docs/the-dangers-of-square-bracket-notation.md)**


### [Object.keys, values, entries](https://javascript.info/keys-values-entries#object-keys-values-entries)

For plain objects, the following methods are available:

-   [Object.keys(obj)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys) – returns an array of keys.
-   [Object.values(obj)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values) – returns an array of values.
-   [Object.entries(obj)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries) – returns an array of `[key, value]` pairs.

Please note the distinctions (compared to map for example):

Map

Object

Call syntax

`map.keys()`

`Object.keys(obj)`, but not `obj.keys()`

Returns

iterable

“real” Array

The first difference is that we have to call `Object.keys(obj)`, and not `obj.keys()`.

Why so? The main reason is flexibility. Remember, objects are a base of all complex structures in JavaScript. So we may have an object of our own like `data` that implements its own `data.values()` method. And we still can call `Object.values(data)` on it.

The second difference is that `Object.*` methods return “real” array objects, not just an iterable. That’s mainly for historical reasons.

For instance:

```javascript
let user = {
  name: "John",
  age: 30
};
```

-   `Object.keys(user) = ["name", "age"]`
-   `Object.values(user) = ["John", 30]`
-   `Object.entries(user) = [ ["name","John"], ["age",30] ]`

Here’s an example of using `Object.values` to loop over property values:

[](https://javascript.info/keys-values-entries# "run")

[](https://javascript.info/keys-values-entries# "open in sandbox")

```javascript
let user = {
  name: "John",
  age: 30
};

// loop over values
for (let value of Object.values(user)) {
  alert(value); // John, then 30
}
```

Object.keys/values/entries ignore symbolic properties

Just like a `for..in` loop, these methods ignore properties that use `Symbol(...)` as keys.

Usually that’s convenient. But if we want symbolic keys too, then there’s a separate method [Object.getOwnPropertySymbols](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertySymbols) that returns an array of only symbolic keys. Also, there exist a method [Reflect.ownKeys(obj)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Reflect/ownKeys) that returns _all_ keys.
### Transforming objects

Objects lack many methods that exist for arrays, e.g. `map`, `filter` and others.

If we’d like to apply them, then we can use `Object.entries` followed by `Object.fromEntries`:

1.  Use `Object.entries(obj)` to get an array of key/value pairs from `obj`.
2.  Use array methods on that array, e.g. `map`, to transform these key/value pairs.
3.  Use `Object.fromEntries(array)` on the resulting array to turn it back into an object.

For example, we have an object with prices, and would like to double them:

```javascript
let prices = {
  banana: 1,
  orange: 2,
  meat: 4,
};

let doublePrices = Object.fromEntries(
  // convert prices to array, map each key/value pair into another pair
  // and then fromEntries gives back the object
  Object.entries(prices).map(entry => [entry[0], entry[1] * 2])
);

alert(doublePrices.meat); // 8
```

It may look difficult at first sight, but becomes easy to understand after you use it once or twice. We can make powerful chains of transforms this way.

### [Property flags and descriptors](https://javascript.info/property-descriptors)
### [Property getters and setters](https://javascript.info/property-accessors)
## [Destructuring assignment](https://javascript.info/destructuring-assignment)
## this
### Context in function
- For a typical function, the value of `this` is the object that the function is accessed on. In other words, if the function call is in the form `obj.f()`, then `this` refers to `obj`. For example:
```javascript
function getThis() {
  return this;
}

const obj1 = { name: "obj1" };
const obj2 = { name: "obj2" };

obj1.getThis = getThis;
obj2.getThis = getThis;

console.log(obj1.getThis()); // { name: 'obj1', getThis: [Function: getThis] }
console.log(obj2.getThis()); // { name: 'obj2', getThis: [Function: getThis] }

```
- If the value that the method is accessed on is a primitive, `this` will be a primitive value as well — but only if the function is in strict mode.
-   If a function is called with `this` set to `undefined` or `null`, `this` gets substituted with [`globalThis`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/globalThis) without `strict` mode and throws error with `strict`.
-   If the function is called with `this` set to a primitive value, `this` gets substituted with the primitive value's wrapper object.
### Context in callbacks
- Callbacks are _typically_ called with a `this` value of `undefined` (calling it directly without attaching it to any object), which means if the function is non–strict, the value of `this` is the global object ([`globalThis`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/globalThis)). This is the case for [iterative array methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods), the [`Promise()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/Promise) constructor, [`setTimeout()`](https://developer.mozilla.org/en-US/docs/Web/API/setTimeout), etc.
### Context in arrow functions
- when evaluating an arrow function's body, the language does not create a new `this` binding.
- In global code, `this` is always `globalThis` regardless of strictness, because of the [global context](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this#global_context) binding
```javascript
const globalObject = this;
const foo = () => this;
console.log(foo() === globalObject); // true

```
### Context in constructors
- When a function is used as a constructor (with the [`new`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new) keyword), its `this` is bound to the new object being constructed, no matter which object the constructor function is accessed on. The value of `this` becomes the value of the `new` expression unless the constructor returns another non–primitive value.
```javascript
function C() {
  this.a = 37;
}

let o = new C();
console.log(o.a); // 37

function C2() {
  this.a = 37;
  return { a: 38 };
}

o = new C2();
console.log(o.a); // 38
```
### Context in Class
- *Instance context* - constructors, methods, instance field initializers; the `this` value is the object that the method was accessed on. If the method is not transferred to another object, `this` is generally an instance of the class.
- *static context* - static methods, field initializers, static initialization blocks; `this` is the value of the class
- *derived class constructor* -  derived constructors have no initial `this` binding. Calling [`super()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super)creates a `this` binding within the constructor and essentially has the effect of evaluating the following line of code, where `Base` is the base class
### Context in global
- At the top level of a script, `this` refers to [`globalThis`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/globalThis) whether in strict mode or not. This is generally the same as the global object — for example, if the source is put inside an HTML [`<script>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script) element and executed as a script, `this === window`.
## Arrays (See [[Data Types in JS#^bec712]])
- Objects with `0 indexed keys` and are not associative.
- [Array indices](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#array_indices) are, in fact, properties with string keys that contain integers.
- Only be accessed using `bracket notation.`
- `Length` can be `increased or decreased`, `empty` spaces return `undefined.`
- Has a bunch of inbuilt copying, modifying and iterative methods, refer [[Syntax-JS#^e7a286]]
```javascript
const arrayLike = {
  0: "a",
  1: "b",
  length: 2,
};
```
- Above is the generic array like object

## Functions
A function declaration looks like this:

```javascript
function name(parameters, delimited, by, comma) {
  /* code */
}
```
-   `Values `passed to a function `as parameters are copied to its local variables.`
-   A `function may access outer variables`. But it works only from inside out. The c`ode outside of the function doesn’t see its local variables.`
-   A function can return a value. If it doesn’t, then its result is `undefined`.
**NOTE: To make the code clean and easy to understand, it’s recommended to use mainly local variables and parameters in the function, not outer variables.**

- Functions are values. They can be `assigned, copied or declared in any place of the code.`
-  ` If `the function is `declared as a separate statement `in the main code flow, that’s called a `“Function Declaration”.`
-   `If` the function is `created as a part of an expression`, it’s called a `“Function Expression”.`[[#^2ebdf6]]
-   `Function Declarations are processed before the code block is executed. They are visible everywhere in the block.`
-  ` Function Expressions are created when the execution flow reaches them.`

## Functional Expressions

^2ebdf6

- a `map` function that should receive a function as first argument and an array as second argument:
```javascript
function map(f, a) {
  const result = new Array(a.length);
  for (let i = 0; i < a.length; i++) {
    result[i] = f(a[i]);
  }
  return result;
}

const f = function (x) {
  return x * x * x;
}

const numbers = [0, 1, 2, 5, 10];
const cube = map(f, numbers);
console.log(cube);
```
- Function Hoisting - The below code works, only works with function _declarations_
```javascript
console.log(square(5)); // 25

function square(n) {
  return n * n;
}
```

## Callback Functions
Refer [[Asynchronous JS#^f152c1]]

## Arrow Functions
- Its a type of functional experssion
- It’s called “arrow functions”, because it looks like this:

```javascript
let func = (arg1, arg2, ..., argN) => expression;
```
- It’s in the very spirit of JavaScript to `create a function and pass it somewhere.` And in such functions `we usually don’t want to leave the current context`. That’s where arrow functions come in handy.
-  [Arrow functions have no “this”](https://javascript.info/arrow-functions#arrow-functions-have-no-this) If `this` is accessed, it is taken from the outside.
```js
let group = { 
	title: "Our Group", 
	students: ["John", "Pete", "Alice"], 
	showList() { 
		this.students.forEach( 
			student => alert(this.title + ': ' + student) 
		); 
	} 
}; 
group.showList();
```
- Arrow functions can’t run with `new`(whic means it can be used as a constructor)
- #### `Arrow functions VS bind
	- There’s a subtle difference between an arrow function `=>` and a regular function called with `.bind(this)`:
		-   `.bind(this)` creates a “bound version” of the function.
		-   The arrow `=>` doesn’t create any binding. The function simply doesn’t have `this`. The lookup of `this` is made exactly the same way as a regular variable search: in the outer lexical environment.
- [Arrows have no “arguments”](https://javascript.info/arrow-functions#arrows-have-no-arguments)
```js
function defer(f, ms) { 
	return function() { 
		setTimeout(() => f.apply(this, arguments), ms); 
	}; 
} 
function sayHi(who) { 
	alert('Hello, ' + who); 
} 
let sayHiDeferred = defer(sayHi, 2000); 
sayHiDeferred("John"); // Hello, John after 2 seconds

//Without arrow function
function defer(f, ms) { 
	return function(...args) { 
		let ctx = this; 
		setTimeout(function() { 
			return f.apply(ctx, args); 
		}, ms); 
	}; 
}
```

## Function Prototype Methods

### Function.prototype.apply(thisArg, arr)
- The **`apply()`** method calls the specified function with a given `this` value, and `arguments` provided as an array (or an [array-like object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Indexed_collections#working_with_array-like_objects)).
- Uses
-  [Using apply() to append an array to another](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply#using_apply_to_append_an_array_to_another)

```js
const array = ["a", "b"];
const elements = [0, 1, 2];
array.push.apply(array, elements);
console.info(array); // ["a", "b", 0, 1, 2]

// Same effect as spread arg
const array = ["a", "b"];
const elements = [0, 1, 2];
array.push(...elements);
console.info(array); // ["a", "b", 0, 1, 2]
```
- [Using apply() and built-in functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply#using_apply_and_built-in_functions)
```js
// min/max number in an array
const numbers = [5, 6, 2, 3, 7];

// using Math.min/Math.max apply
let max = Math.max.apply(null, numbers);
// This about equal to Math.max(numbers[0], …)
// or Math.max(5, 6, …)

let min = Math.min.apply(null, numbers);
```

### Function.prototype.bind(thisArg, optional...)
- The **`bind()`** method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.
- 
## [Function object, NFE](https://javascript.info/function-object)

## Closures
- A closure is an expression (most commonly, a function) that can have free variables together with an environment that binds those variables (that "closes" the expression).
- Inner can access outer, but not vice versa
```javascript
function addSquares(a, b) {
  function square(x) {
    return x * x;
  }
  return square(a) + square(b);
}
const a = addSquares(2, 3); // returns 13
const b = addSquares(3, 4); // returns 25
const c = addSquares(4, 5); // returns 41

function outside(x) {
  function inside(y) {
    return x + y;
  }
  return inside;
}
const fnInside = outside(3); // Think of it like: give me a function that adds 3 to whatever you give it
const result = fnInside(5); // returns 8
const result1 = outside(3)(5); // returns 8
```
- in Essence `addSquares, outside` are function factories. All const variables form closures. They share the same function body definition, but store different `lexical environments`.
- Name Conflicts - When two arguments or variables in the scopes of a closure have the same name, there is a _name conflict_. More nested scopes take precedence. So, `the innermost scope takes the highest precedence, while the outermost scope takes the lowest`. This is the scope chain.
- If an enclosed function defines a variable with the same name as a variable in the outer scope, then there is no way to refer to the variable in the outer scope again. (The inner scope variable "overrides" the outer one, until the program exits the inner scope.
```javascript
function outside() {
  const x = 5;
  function inside(x) {
    return x * 2;
  }
  return inside;
}

outside()(10); // returns 20 instead of 10
```
- An object containing methods for manipulating the inner variables of the outer function can be returned.
```javascript
const createPet = function (name) {
  let sex;

  const pet = {
    // setName(newName) is equivalent to setName: function (newName)
    // in this context
    setName(newName) {
      name = newName;
    },

    getName() {
      return name;
    },

    getSex() {
      return sex;
    },

    setSex(newSex) {
      if (typeof newSex === 'string' &&
        (newSex.toLowerCase() === 'male' || newSex.toLowerCase() === 'female')) {
        sex = newSex;
      }
    }
  };

  return pet;
}

const pet = createPet('Vivie');
pet.getName();                  // Vivie

pet.setName('Oliver');
pet.setSex('male');
pet.getSex();                   // male
pet.getName();                  // Oliver
```
- you can use a `closure` anywhere that you might normally use an object with only a single method. Refer MDN Closure example
## Emulating private methods with Closures
```js
const counter = (function () {
  let privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }

  return {
    increment() {
      changeBy(1);
    },

    decrement() {
      changeBy(-1);
    },

    value() {
      return privateCounter;
    },
  };
})();

console.log(counter.value()); // 0.

counter.increment();
counter.increment();
console.log(counter.value()); // 2.

counter.decrement();
console.log(counter.value()); // 1.

```
- In the above example, there is a single lexical environment that is shared by the three functions: `counter.increment`, `counter.decrement`, and `counter.value`.
- The shared lexical environment is created in the body of an anonymous function, _which is executed as soon as it has been defined_ (also known as an [IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)). The lexical environment contains two private items: a variable called `privateCounter`, and a function called `changeBy`. You can't access either of these private members from outside the anonymous function. Instead, you can access them using the three public functions that are returned from the anonymous wrapper.
- Change the above, to normal function variable and make lexical environments according to one's usecases
## Creating closures in a loop
```js
function showHelp(help) {
  document.getElementById('help').textContent = help;
}

function setupHelp() {
  var helpText = [
    { id: 'email', help: 'Your email address' },
    { id: 'name', help: 'Your full name' },
    { id: 'age', help: 'Your age (you must be over 16)' },
  ];

  for (var i = 0; i < helpText.length; i++) {
    // Culprit is the use of `var` on this line
    var item = helpText[i];
    document.getElementById(item.id).onfocus = function () {
      showHelp(item.help);
    };
  }
}

setupHelp();
```
- If you try this code out, you'll see that it doesn't work as expected. No matter what field you focus on, the message about your age will be displayed.

- The reason for this is that the functions assigned to `onfocus` form closures; they consist of the function definition and the captured environment from the `setupHelp` function's scope. Three closures have been created by the loop, but each one shares the same single lexical environment, which has a variable with changing values (`item`). This is because the variable `item` is declared with `var` and thus has function scope due to hoisting. The value of `item.help` is determined when the `onfocus` callbacks are executed. Because the loop has already run its course by that time, the `item`variable object (shared by all three closures) has been left pointing to the last entry in the `helpText`list.
- 1ST SOLUTION (SEPERATE FUNTIONS)
```js
function showHelp(help) {
  document.getElementById('help').textContent = help;
}

function makeHelpCallback(help) {
  return function () {
    showHelp(help);
  };
}

function setupHelp() {
  var helpText = [
    { id: 'email', help: 'Your email address' },
    { id: 'name', help: 'Your full name' },
    { id: 'age', help: 'Your age (you must be over 16)' },
  ];

  for (var i = 0; i < helpText.length; i++) {
    var item = helpText[i];
    document.getElementById(item.id).onfocus = makeHelpCallback(item.help);
  }
}

setupHelp();
```
- 2ND SOLUTION (ANONYMOUS CLOSURES)
```js
function showHelp(help) {
  document.getElementById('help').textContent = help;
}

function setupHelp() {
  var helpText = [
    { id: 'email', help: 'Your email address' },
    { id: 'name', help: 'Your full name' },
    { id: 'age', help: 'Your age (you must be over 16)' },
  ];

  for (var i = 0; i < helpText.length; i++) {
    (function () {
      var item = helpText[i];
      document.getElementById(item.id).onfocus = function () {
        showHelp(item.help);
      };
    })(); // Immediate event listener attachment with the current value of item (preserved until iteration).
  }
}

setupHelp();

```
- 3RD SOLUTION (USE CONST & LET)
```js
function showHelp(help) {
  document.getElementById('help').textContent = help;
}

function setupHelp() {
  const helpText = [
    { id: 'email', help: 'Your email address' },
    { id: 'name', help: 'Your full name' },
    { id: 'age', help: 'Your age (you must be over 16)' },
  ];

  for (let i = 0; i < helpText.length; i++) {
    const item = helpText[i];
    document.getElementById(item.id).onfocus = () => {
      showHelp(item.help);
    };
  }
}

setupHelp();
```
## Using *arguments* object
- The arguments of a function are maintained in an array-like object.
- `arguments[i]`
- The total number of arguments is indicated by `arguments.length`.
```javascript
function myConcat(separator) {
  let result = ''; // initialize list
  // iterate through arguments
  for (let i = 1; i < arguments.length; i++) {
    result += arguments[i] + separator;
  }
  return result;
}

// returns "red, orange, blue, "
myConcat(', ', 'red', 'orange', 'blue');

// returns "elephant; giraffe; lion; cheetah; "
myConcat('; ', 'elephant', 'giraffe', 'lion', 'cheetah');

// returns "sage. basil. oregano. pepper. parsley. "
myConcat('. ', 'sage', 'basil', 'oregano', 'pepper', 'parsley');

```
## Function Parameters
- Default parameter =  `undefined` unless defined and set as `function(a, b=1)`
- Rest parameter = `function(a, ...b)`

## IIFE
- Use cases:
	- Avoid polluting the global namespace
	```js
	(() => {
	  // some initiation code
	  let firstVariable;
	  let secondVariable;
	})();

	// firstVariable and secondVariable will be discarded after the function is executed.

	```
	- Execute an async function
	```js
	const getFileStream = async (url) => {
	  // implementation
	};

	(async () => {
		  const stream = await getFileStream("https://domain.name/path/file.ext");
	  for await (const chunk of stream) {
	    console.log({ chunk });
	  }
	})();
	```
	- THe module pattern
	```js
	const makeWithdraw = (balance) =>
  ((copyBalance) => {
    let balance = copyBalance; // This variable is private
    const doBadThings = () => {
      console.log("I will do bad things with your money");
    };
    doBadThings();
    return {
      withdraw(amount) {
        if (balance >= amount) {
          balance -= amount;
          return balance;
        }
        return "Insufficient money";
      },
    };
  })(balance);

const firstAccount = makeWithdraw(100); // "I will do bad things with your money"
console.log(firstAccount.balance); // undefined
console.log(firstAccount.withdraw(20)); // 80
console.log(firstAccount.withdraw(30)); // 50
console.log(firstAccount.doBadThings); // undefined; this method is private
const secondAccount = makeWithdraw(20); // "I will do bad things with your money"
console.log(secondAccount.withdraw(30)); // "Insufficient money"
console.log(secondAccount.withdraw(20)); // 0
	```
## Template literals 
- backtick could hold expressions using `${}` 

## `strict` mode
To fully enable all features of modern JavaScript, we should start scripts with `"use strict"`.

```javascript
'use strict';

...
```
- Ensure that “use strict” is at the top
- There’s no way to cancel `use strict`
Modern JavaScript supports “classes” and “modules” – advanced language structures (we’ll surely get to them), that enable `use strict` automatically. So we don’t need to add the `"use strict"` directive, if we use them.

**So, for now `"use strict";` is a welcome guest at the top of your scripts. Later, when your code is all in classes and modules, you may omit it.**

## Asynchronous Javascript
### Web Workers
- Javascript has introduced a new concept to prevent the limitation we are facing, that is, `Web Workers. `Web Workers (threads in js) are mainly used `to perform CPU-intensiveJavascript tasks`. They `can perform long-running tasks without affecting or blocking the main execution thread.`

Using a Constructor, we can create a worker object, which will run a js file. This js file includes code to run the worker thread; these workers run in some other global context that is different from the current window.\

However, Node.js built-in asynchronous I/O operations are more efficient than Workers can be. Web workers are not of much help with I/O-intensive work.

See [[Asynchronous JS]]
for events, promise, setTimeout

## Personal Notes

-   Block has global scope
-   Labeled loops like java
-   Return condition must be in the same line
-   Functions are first class objects
-   Closures are functions inside function which can run even if outer
    function run is over
-   Objects can contain functions.
-   Functions attached to an object can access object variables using
    **[this]{.underline}** keyword
-   Functions can also be attached to objects afterwards and access
    object properties using **[this]{.underline}** keyword
-   **[Call]{.underline}** and **[apply]{.underline}** keywords can also
    be used to execute a function attaching an object temporarily
-   Use **[bind]{.underline}** partially or fully bind functions to an
    object
-   **[new]{.underline}** keyword with function call can be used for
    creating constructors which creates new objects and made available
    using **[this]{.underline}** keyword
-   Javascript instance + inheritence = prototype
-   **[\_\_proto\_\_]{.underline}** keyword is used to attach prototypes
    with objects. Changes to prototypes are visible to everyone. The
    ***[for/in]{.underline}*** **** statement allows iterations over
    properties of an object. hasOwnProperty function can be used to
    exclude prototype properties from objects.
-   The first is Object.create, which is a recent addition to Js and not
    available in all implementations yet. ***var my0bj = Object.create
    (myPrototype);***\
-   The second way, which works anywhere, has to do with constructors.
    Constructors have a property called prototype. This is \*not\* the
    prototype of the constructor function itself; instead, it\'s the
    prototype that new objects are given when they\'re created with that
    constructor and the new keyword. ***MyConstructor.prototype = {
    myNumber: 5, getMyNumber: function(){ return this.myNumber; } }; var
    myNewObj2 = new MyConstructor(); myNewObj2.getMyNumber(); //=5
    myNewObj2.myNumber = 6; myNewobj2.getMyNumber(); //=6***

## Transpilers and polyfills
### Transpilers
- A [transpiler](https://en.wikipedia.org/wiki/Source-to-source_compiler) is a special piece of software that translates source code to another source code. It can parse (“read and understand”) modern code and rewrite it using older syntax constructs, so that it’ll also work in outdated engines.
E.g. JavaScript before year 2020 didn’t have the “nullish coalescing operator” `??`. So, if a visitor uses an outdated browser, it may fail to understand the code like `height = height ?? 100`.

A transpiler would analyze our code and rewrite `height ?? 100` into `(height !== undefined && height !== null) ? height : 100`.
Speaking of names, [Babel](https://babeljs.io/) is one of the most prominent transpilers out there.

Modern project build systems, such as [webpack](https://webpack.js.org/), provide a means to run a transpiler automatically on every code change, so it’s very easy to integrate into the development process.

### Polyfills
New language features may include not only syntax constructs and operators, but also built-in functions.

For example, `Math.trunc(n)` is a function that “cuts off” the decimal part of a number, e.g `Math.trunc(1.23)` returns `1`.

In some (very outdated) JavaScript engines, there’s no `Math.trunc`, so such code will fail.

As we’re talking about new functions, not syntax changes, there’s no need to transpile anything here. We just need to declare the missing function.

A script that updates/adds new functions is called “polyfill”. It “fills in” the gap and adds missing implementations.

Two interesting polyfill libraries are:

-   [core js](https://github.com/zloirock/core-js) that supports a lot, allows to include only needed features.
-   [polyfill.io](https://polyfill.io/) service that provides a script with polyfills, depending on the features and user’s browser.

---
References:
- 
