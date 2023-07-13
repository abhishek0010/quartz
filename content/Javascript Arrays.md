---
title: Javascript Arrays
tags: 
- javascript
---
-----------------
Date Created : `25-01-2023`

Tags: #javascript, #publish 


----------------------------
# `Javascript Arrays`.

NOTE: Summarize [Arrays](https://javascript.info/array)

In JavaScript, arrays aren't [primitives](https://developer.mozilla.org/en-US/docs/Glossary/Primitive) but are instead `Array` objects with the following core characteristics:

-   **JavaScript arrays are resizable** and **can contain a mix of different [data types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)**. (When those characteristics are undesirable, use [typed arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Typed_arrays) instead.)
-   **JavaScript arrays are not associative arrays** and so, array elements cannot be accessed using arbitrary strings as indexes, but must be accessed using nonnegative integers (or their respective string form) as indexes.
-   **JavaScript arrays are [zero-indexed](https://en.wikipedia.org/wiki/Zero-based_numbering)**: the first element of an array is at index `0`, the second is at index `1`, and so on — and the last element is at the value of the array's [`length`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/length) property minus `1`.
-   **JavaScript [array-copy operations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#copy_an_array) create [shallow copies](https://developer.mozilla.org/en-US/docs/Glossary/Shallow_copy)**. (All standard built-in copy operations with _any_ JavaScript objects create shallow copies, rather than [deep copies](https://developer.mozilla.org/en-US/docs/Glossary/Deep_copy)).

- A JavaScript array's [`length`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/length) property and numerical properties are connected.

## Copying Methods and mutuaing methods
The following methods create new arrays with `@@species`:

-   [`concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)
-   [`filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
-   [`flat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)
-   [`flatMap()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap)
-   [`map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
-   [`slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
-   [`splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) (to construct the array of removed elements that's returned)


The following methods mutate the original array:

-   [`copyWithin()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)
-   [`fill()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)
-   [`pop()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)
-   [`push()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)
-   [`reverse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)
-   [`shift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)
-   [`sort()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
-   [`splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
-   [`unshift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)


## Iterative Methods
- Many array methods take a callback function as an argument.
- They all share the same signature:

```javascript
method(callbackFn, thisArg)
```
Where `callbackFn` takes three arguments:

`element`

The current element being processed in the array.

`index`

The index of the current element being processed in the array.

`array`

The array that the method was called upon.

The `thisArg` argument (defaults to `undefined`) will be used as the `this` value when calling `callbackFn`. The `this` value ultimately observable by `callbackFn` is determined according to [the usual rules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this): if `callbackFn` is [non-strict](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode#no_this_substitution), primitive `this` values are wrapped into objects, and `undefined`/`null` is substituted with [`globalThis`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/globalThis). The `thisArg` argument is irrelevant for any `callbackFn` defined with an [arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions), as arrow functions don't have their own `this` binding.

The following methods are iterative:

-   [`every()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)
-   [`filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
-   [`find()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
-   [`findIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)
-   [`findLast()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLast)
-   [`findLastIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLastIndex)
-   [`flatMap()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap)
-   [`forEach()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
-   [`group()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/group)
-   [`groupToMap()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/groupToMap)
-   [`map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
-   [`some()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)

## Generic Array Methods
- Always generic
- They only access the array elements through the `length` property and the indexed elements.
```javascript
const arrayLike = {
  0: "a",
  1: "b",
  length: 2,
};
console.log(Array.prototype.join.call(arrayLike, "+")); // 'a+b'
```

## Constructor
- `Array()`
## Static Methods
- `Array.from()` - Creates new array from array-like objects and iterable object
- `Array.isArray()` - check if array
- `Array.of()` - Creates a new `Array` instance with a variable number of arguments, regardless of number or type of the arguments.
- 
## Instance Properties
- `Array.prototype.length` 
- [`Array.prototype[@@unscopables]`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/@@unscopables)

Contains property names that were not included in the ECMAScript standard prior to the ES2015 version and that are ignored for [`with`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/with) statement-binding purposes.

## Instance Methods
[`Array.prototype.at()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/at)

Returns the array item at the given index. Accepts negative integers, which count back from the last item.

[`Array.prototype.concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

Returns a new array that is the calling array joined with other array(s) and/or value(s).

[`Array.prototype.copyWithin()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)

Copies a sequence of array elements within an array.

[`Array.prototype.entries()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/entries)

Returns a new [_array iterator_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators) object that contains the key/value pairs for each index in an array.

[`Array.prototype.every()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)

Returns `true` if every element in the calling array satisfies the testing function.

[`Array.prototype.fill()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)

Fills all the elements of an array from a start index to an end index with a static value.

[`Array.prototype.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

Returns a new array containing all elements of the calling array for which the provided filtering function returns `true`.

[`Array.prototype.find()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

Returns the value of the first element in the array that satisfies the provided testing function, or `undefined` if no appropriate element is found.

```js
const found = array1.find(element => element > 10);
```

[`Array.prototype.findIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

Returns the index of the first element in the array that satisfies the provided testing function, or `-1` if no appropriate element was found.

[`Array.prototype.findLast()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLast)

Returns the value of the last element in the array that satisfies the provided testing function, or `undefined` if no appropriate element is found.

[`Array.prototype.findLastIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLastIndex)

Returns the index of the last element in the array that satisfies the provided testing function, or `-1`if no appropriate element was found.

[`Array.prototype.flat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)

Returns a new array with all sub-array elements concatenated into it recursively up to the specified depth.

[`Array.prototype.flatMap()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap)

Returns a new array formed by applying a given callback function to each element of the calling array, and then flattening the result by one level.

[`Array.prototype.forEach()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

Calls a function for each element in the calling array.

[`Array.prototype.includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

Determines whether the calling array contains a value, returning `true` or `false` as appropriate.

[`Array.prototype.indexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)

Returns the first (least) index at which a given element can be found in the calling array.

[`Array.prototype.join()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

Joins all elements of an array into a string.

[`Array.prototype.keys()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/keys)

Returns a new [_array iterator_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators) that contains the keys for each index in the calling array.

[`Array.prototype.lastIndexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf)

Returns the last (greatest) index at which a given element can be found in the calling array, or `-1`if none is found.

[`Array.prototype.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

Returns a new array containing the results of invoking a function on every element in the calling array.

[`Array.prototype.pop()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)

Removes the last element from an array and returns that element.

[`Array.prototype.push()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

Adds one or more elements to the end of an array, and returns the new `length` of the array.

[`Array.prototype.reduce()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)

Executes a user-supplied "reducer" callback function on each element of the array (from left to right), to reduce it to a single value.

[`Array.prototype.reduceRight()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight)

Executes a user-supplied "reducer" callback function on each element of the array (from right to left), to reduce it to a single value.

[`Array.prototype.reverse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)

Reverses the order of the elements of an array _in place_. (First becomes the last, last becomes first.)

[`Array.prototype.shift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)

Removes the first element from an array and returns that element.

[`Array.prototype.slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

Extracts a section of the calling array and returns a new array.

[`Array.prototype.some()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)

Returns `true` if at least one element in the calling array satisfies the provided testing function.

[`Array.prototype.sort()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

Sorts the elements of an array in place and returns the array.

[`Array.prototype.splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

Adds and/or removes elements from an array.

[`Array.prototype.toLocaleString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toLocaleString)

Returns a localized string representing the calling array and its elements. Overrides the [`Object.prototype.toLocaleString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toLocaleString) method.

[`Array.prototype.toString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)

Returns a string representing the calling array and its elements. Overrides the [`Object.prototype.toString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString) method.

[`Array.prototype.unshift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)

Adds one or more elements to the front of an array, and returns the new `length` of the array.

[`Array.prototype.values()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/values)

Returns a new [_array iterator_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators) object that contains the values for each index in the array.

[`Array.prototype[@@iterator]()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/@@iterator)

An alias for the [`values()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/values) method by default.

## Examples
```javascript
//Creation
const fruits = ["Apple", "Banana"];
const fruits2 = new Array("Apple", "Banana");
const fruits3 = "Apple, Banana".split(", ");

// String creation
const fruitsString = fruits.join(", ");

//Element access
fruits[0]; // Apple
fruits[1]; // Banana
fruits[fruits.length - 1]; // Banana
fruits[99]; // undefined

//Find Index
console.log(fruits.indexOf("Banana"));// 1

// Check if element exist
fruits.includes("Banana"); // true
fruits.includes("Cherry"); // false

// If indexOf() doesn't return -1, the array contains the given item.
fruits.indexOf("Banana") !== -1; // true
fruits.indexOf("Cherry") !== -1; // false

//Append at back
const newLength = fruits.push("Orange");

//Remove from back
const removedItem = fruits.pop();

// Remove multiple items
const fruits = ["Apple", "Banana", "Strawberry", "Mango", "Cherry"];
const start = -3;
const removedItems = fruits.splice(start);
console.log(fruits);// ["Apple", "Banana"]
console.log(removedItems);// ["Strawberry", "Mango", "Cherry"]

const fruits = ["Apple", "Banana", "Strawberry", "Mango", "Cherry"];
const start = 2;
const removedItems = fruits.splice(start);
console.log(fruits);// ["Apple", "Banana"]
console.log(removedItems);// ["Strawberry", "Mango", "Cherry"]

const fruits = ["Apple", "Strawberry", "Cherry", "Banana", "Mango"];
const start = 0;
const deleteCount = 3;
const removedItems = fruits.splice(start, deleteCount);
console.log(fruits);// ["Banana", "Mango"]
console.log(removedItems);// ["Apple", "Strawberry", "Cherry"]
//splice can also be used to replace elements
const removedItems = fruits.splice(start, deleteCount, "Mango", "Cherry");

//Append at front
const newLength = fruits.unshift("Strawberry");

// Remove from front
const removedItem = fruits.shift();

//iterate over
const fruits = ["Apple", "Mango", "Cherry"];
for (const fruit of fruits) {
  console.log(fruit);
}

const fruits = ["Apple", "Mango", "Cherry"];
fruits.forEach((item, index, array) => {
  console.log(item, index);
});

// Merging two arrays
const fruits = ["Apple", "Banana", "Strawberry"];
const moreFruits = ["Mango", "Cherry"];
const combinedFruits = fruits.concat(moreFruits);

// Copy array
const fruits = ["Strawberry", "Mango"];

const fruitsCopy = [...fruits];// ["Strawberry", "Mango"]

const fruitsCopy2 = Array.from(fruits);// ["Strawberry", "Mango"]

const fruitsCopy3 = fruits.slice();// ["Strawberry", "Mango"]

//


```
### Splice(The swiss army knife)
The [arr.splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) method is a swiss army knife for arrays. It can do everything: insert, remove and replace elements.

The syntax is:

```javascript
arr.splice(start[, deleteCount, elem1, ..., elemN])
```

It modifies `arr` starting from the index `start`: removes `deleteCount` elements and then inserts `elem1, ..., elemN` at their place. Returns the array of removed elements.

This method is easy to grasp by examples.

Let’s start with the deletion:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = ["I", "study", "JavaScript"];

arr.splice(1, 1); // from index 1 remove 1 element

alert( arr ); // ["I", "JavaScript"]
```

Easy, right? Starting from the index `1` it removed `1` element.

In the next example we remove 3 elements and replace them with the other two:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = ["I", "study", "JavaScript", "right", "now"];

// remove 3 first elements and replace them with another
arr.splice(0, 3, "Let's", "dance");

alert( arr ) // now ["Let's", "dance", "right", "now"]
```

Here we can see that `splice` returns the array of removed elements:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = ["I", "study", "JavaScript", "right", "now"];

// remove 2 first elements
let removed = arr.splice(0, 2);

alert( removed ); // "I", "study" <-- array of removed elements
```

The `splice` method is also able to insert the elements without any removals. For that we need to set `deleteCount` to `0`:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = ["I", "study", "JavaScript"];

// from index 2
// delete 0
// then insert "complex" and "language"
arr.splice(2, 0, "complex", "language");

alert( arr ); // "I", "study", "complex", "language", "JavaScript"
```

### [slice](https://javascript.info/array-methods#slice)

The method [arr.slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) is much simpler than similar-looking `arr.splice`.

The syntax is:

```javascript
arr.slice([start], [end])
```

It returns a new array copying to it all items from index `start` to `end` (not including `end`). Both `start`and `end` can be negative, in that case position from array end is assumed.

It’s similar to a string method `str.slice`, but instead of substrings it makes subarrays.

For instance:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = ["t", "e", "s", "t"];

alert( arr.slice(1, 3) ); // e,s (copy from 1 to 3)

alert( arr.slice(-2) ); // s,t (copy from -2 till the end)
```

We can also call it without arguments: `arr.slice()` creates a copy of `arr`. That’s often used to obtain a copy for further transformations that should not affect the original array.

### [concat](https://javascript.info/array-methods#concat)

The method [arr.concat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat) creates a new array that includes values from other arrays and additional items.

The syntax is:

```javascript
arr.concat(arg1, arg2...)
```

It accepts any number of arguments – either arrays or values.

The result is a new array containing items from `arr`, then `arg1`, `arg2` etc.

If an argument `argN` is an array, then all its elements are copied. Otherwise, the argument itself is copied.

For instance:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [1, 2];

// create an array from: arr and [3,4]
alert( arr.concat([3, 4]) ); // 1,2,3,4

// create an array from: arr and [3,4] and [5,6]
alert( arr.concat([3, 4], [5, 6]) ); // 1,2,3,4,5,6

// create an array from: arr and [3,4], then add values 5 and 6
alert( arr.concat([3, 4], 5, 6) ); // 1,2,3,4,5,6
```

Normally, it only copies elements from arrays. Other objects, even if they look like arrays, are added as a whole:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [1, 2];

let arrayLike = {
  0: "something",
  length: 1
};

alert( arr.concat(arrayLike) ); // 1,2,[object Object]
```

…But if an array-like object has a special `Symbol.isConcatSpreadable` property, then it’s treated as an array by `concat`: its elements are added instead:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [1, 2];

let arrayLike = {
  0: "something",
  1: "else",
  [Symbol.isConcatSpreadable]: true,
  length: 2
};

alert( arr.concat(arrayLike) ); // 1,2,something,else
```

## [Searching in array](https://javascript.info/array-methods#searching-in-array)

Now let’s cover methods that search in an array.

### [indexOf/lastIndexOf and includes](https://javascript.info/array-methods#indexof-lastindexof-and-includes)

The methods [arr.indexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) and [arr.includes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) have the similar syntax and do essentially the same as their string counterparts, but operate on items instead of characters:

-   `arr.indexOf(item, from)` – looks for `item` starting from index `from`, and returns the index where it was found, otherwise `-1`.
-   `arr.includes(item, from)` – looks for `item` starting from index `from`, returns `true` if found.

Usually these methods are used with only one argument: the `item` to search. By default, the search is from the beginning.

For instance:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [1, 0, false];

alert( arr.indexOf(0) ); // 1
alert( arr.indexOf(false) ); // 2
alert( arr.indexOf(null) ); // -1

alert( arr.includes(1) ); // true
```

Please note that `indexOf` uses the strict equality `===` for comparison. So, if we look for `false`, it finds exactly `false` and not the zero.

If we want to check if `item` exists in the array, and don’t need the index, then `arr.includes` is preferred.

The method [arr.lastIndexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf) is the same as `indexOf`, but looks for from right to left.

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let fruits = ['Apple', 'Orange', 'Apple']

alert( fruits.indexOf('Apple') ); // 0 (first Apple)
alert( fruits.lastIndexOf('Apple') ); // 2 (last Apple)
```

The `includes` method handles `NaN` correctly

A minor, but noteworthy feature of `includes` is that it correctly handles `NaN`, unlike `indexOf`:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
const arr = [NaN];
alert( arr.indexOf(NaN) ); // -1 (wrong, should be 0)
alert( arr.includes(NaN) );// true (correct)
```

That’s because `includes` was added to JavaScript much later and uses the more up to date comparison algorithm internally.

### [find and findIndex/findLastIndex](https://javascript.info/array-methods#find-and-findindex-findlastindex)

Imagine we have an array of objects. How do we find an object with the specific condition?

Here the [arr.find(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find) method comes in handy.

The syntax is:

```javascript
let result = arr.find(function(item, index, array) {
  // if true is returned, item is returned and iteration is stopped
  // for falsy scenario returns undefined
});
```

The function is called for elements of the array, one after another:

-   `item` is the element.
-   `index` is its index.
-   `array` is the array itself.

If it returns `true`, the search is stopped, the `item` is returned. If nothing found, `undefined` is returned.

For example, we have an array of users, each with the fields `id` and `name`. Let’s find the one with `id == 1`:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let users = [
  {id: 1, name: "John"},
  {id: 2, name: "Pete"},
  {id: 3, name: "Mary"}
];

let user = users.find(item => item.id == 1);

alert(user.name); // John
```

In real life arrays of objects is a common thing, so the `find` method is very useful.

Note that in the example we provide to `find` the function `item => item.id == 1` with one argument. That’s typical, other arguments of this function are rarely used.

The [arr.findIndex](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex) method has the same syntax, but returns the index where the element was found instead of the element itself. The value of `-1` is returned if nothing is found.

The [arr.findLastIndex](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLastIndex) method is like `findIndex`, but searches from right to left, similar to `lastIndexOf`.

Here’s an example:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let users = [
  {id: 1, name: "John"},
  {id: 2, name: "Pete"},
  {id: 3, name: "Mary"},
  {id: 4, name: "John"}
];

// Find the index of the first John
alert(users.findIndex(user => user.name == 'John')); // 0

// Find the index of the last John
alert(users.findLastIndex(user => user.name == 'John')); // 3
```

### [filter](https://javascript.info/array-methods#filter)

The `find` method looks for a single (first) element that makes the function return `true`.

If there may be many, we can use [arr.filter(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter).

The syntax is similar to `find`, but `filter` returns an array of all matching elements:

```javascript
let results = arr.filter(function(item, index, array) {
  // if true item is pushed to results and the iteration continues
  // returns empty array if nothing found
});
```

For instance:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let users = [
  {id: 1, name: "John"},
  {id: 2, name: "Pete"},
  {id: 3, name: "Mary"}
];

// returns array of the first two users
let someUsers = users.filter(item => item.id < 3);

alert(someUsers.length); // 2
```

## [Transform an array](https://javascript.info/array-methods#transform-an-array)

Let’s move on to methods that transform and reorder an array.

### [map](https://javascript.info/array-methods#map)

The [arr.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) method is one of the most useful and often used.

It calls the function for each element of the array and returns the array of results.

The syntax is:

```javascript
let result = arr.map(function(item, index, array) {
  // returns the new value instead of item
});
```

For instance, here we transform each element into its length:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let lengths = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);
alert(lengths); // 5,7,6
```

### [sort(fn)](https://javascript.info/array-methods#sort-fn)

The call to [arr.sort()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) sorts the array _in place_, changing its element order.

It also returns the sorted array, but the returned value is usually ignored, as `arr` itself is modified.

For instance:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [ 1, 2, 15 ];

// the method reorders the content of arr
arr.sort();

alert( arr );  // 1, 15, 2
```

Did you notice anything strange in the outcome?

The order became `1, 15, 2`. Incorrect. But why?

**The items are sorted as strings by default.**

Literally, all elements are converted to strings for comparisons. For strings, lexicographic ordering is applied and indeed `"2" > "15"`.

To use our own sorting order, we need to supply a function as the argument of `arr.sort()`.

The function should compare two arbitrary values and return:

```javascript
function compare(a, b) {
  if (a > b) return 1; // if the first value is greater than the second
  if (a == b) return 0; // if values are equal
  if (a < b) return -1; // if the first value is less than the second
}
```

For instance, to sort as numbers:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
function compareNumeric(a, b) {
  if (a > b) return 1;
  if (a == b) return 0;
  if (a < b) return -1;
}

let arr = [ 1, 2, 15 ];

arr.sort(compareNumeric);

alert(arr);  // 1, 2, 15
```

Now it works as intended.

Let’s step aside and think what’s happening. The `arr` can be array of anything, right? It may contain numbers or strings or objects or whatever. We have a set of _some items_. To sort it, we need an _ordering function_ that knows how to compare its elements. The default is a string order.

The `arr.sort(fn)` method implements a generic sorting algorithm. We don’t need to care how it internally works (an optimized [quicksort](https://en.wikipedia.org/wiki/Quicksort) or [Timsort](https://en.wikipedia.org/wiki/Timsort) most of the time). It will walk the array, compare its elements using the provided function and reorder them, all we need is to provide the `fn` which does the comparison.

By the way, if we ever want to know which elements are compared – nothing prevents from alerting them:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
[1, -2, 15, 2, 0, 8].sort(function(a, b) {
  alert( a + " <> " + b );
  return a - b;
});
```

The algorithm may compare an element with multiple others in the process, but it tries to make as few comparisons as possible.

A comparison function may return any number

Actually, a comparison function is only required to return a positive number to say “greater” and a negative number to say “less”.

That allows to write shorter functions:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [ 1, 2, 15 ];

arr.sort(function(a, b) { return a - b; });

alert(arr);  // 1, 2, 15
```

Arrow functions for the best

Remember [arrow functions](https://javascript.info/arrow-functions-basics)? We can use them here for neater sorting:

```javascript
arr.sort( (a, b) => a - b );
```

This works exactly the same as the longer version above

### [reverse](https://javascript.info/array-methods#reverse)

The method [arr.reverse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) reverses the order of elements in `arr`.

For instance:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [1, 2, 3, 4, 5];
arr.reverse();

alert( arr ); // 5,4,3,2,1
```

It also returns the array `arr` after the reversal.

### [split and join](https://javascript.info/array-methods#split-and-join)

Here’s the situation from real life. We are writing a messaging app, and the person enters the comma-delimited list of receivers: `John, Pete, Mary`. But for us an array of names would be much more comfortable than a single string. How to get it?

The [str.split(delim)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split) method does exactly that. It splits the string into an array by the given delimiter `delim`.

In the example below, we split by a comma followed by space:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let names = 'Bilbo, Gandalf, Nazgul';

let arr = names.split(', ');

for (let name of arr) {
  alert( `A message to ${name}.` ); // A message to Bilbo  (and other names)
}
```

The `split` method has an optional second numeric argument – a limit on the array length. If it is provided, then the extra elements are ignored. In practice it is rarely used though:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = 'Bilbo, Gandalf, Nazgul, Saruman'.split(', ', 2);

alert(arr); // Bilbo, Gandalf
```

Split into letters

The call to `split(s)` with an empty `s` would split the string into an array of letters:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let str = "test";

alert( str.split('') ); // t,e,s,t
```

The call [arr.join(glue)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) does the reverse to `split`. It creates a string of `arr` items joined by `glue` between them.

For instance:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = ['Bilbo', 'Gandalf', 'Nazgul'];

let str = arr.join(';'); // glue the array into a string using ;

alert( str ); // Bilbo;Gandalf;Nazgul
```

### [reduce/reduceRight](https://javascript.info/array-methods#reduce-reduceright)

When we need to iterate over an array – we can use `forEach`, `for` or `for..of`.

When we need to iterate and return the data for each element – we can use `map`.

The methods [arr.reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce) and [arr.reduceRight](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight) also belong to that breed, but are a little bit more intricate. They are used to calculate a single value based on the array.

The syntax is:

```javascript
let value = arr.reduce(function(accumulator, item, index, array) {
  // ...
}, [initial]);
```

The function is applied to all array elements one after another and “carries on” its result to the next call.

Arguments:

-   `accumulator` – is the result of the previous function call, equals `initial` the first time (if `initial` is provided).
-   `item` – is the current array item.
-   `index` – is its position.
-   `array` – is the array.

As function is applied, the result of the previous function call is passed to the next one as the first argument.

So, the first argument is essentially the accumulator that stores the combined result of all previous executions. And at the end it becomes the result of `reduce`.

Sounds complicated?

The easiest way to grasp that is by example.

Here we get a sum of an array in one line:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [1, 2, 3, 4, 5];

let result = arr.reduce((sum, current) => sum + current, 0);

alert(result); // 15
```

The function passed to `reduce` uses only 2 arguments, that’s typically enough.

Let’s see the details of what’s going on.

1.  On the first run, `sum` is the `initial` value (the last argument of `reduce`), equals `0`, and `current` is the first array element, equals `1`. So the function result is `1`.
2.  On the second run, `sum = 1`, we add the second array element (`2`) to it and return.
3.  On the 3rd run, `sum = 3` and we add one more element to it, and so on…

The calculation flow:

Or in the form of a table, where each row represents a function call on the next array element:

`sum`

`current`

result

the first call

`0`

`1`

`1`

the second call

`1`

`2`

`3`

the third call

`3`

`3`

`6`

the fourth call

`6`

`4`

`10`

the fifth call

`10`

`5`

`15`

Here we can clearly see how the result of the previous call becomes the first argument of the next one.

We also can omit the initial value:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [1, 2, 3, 4, 5];

// removed initial value from reduce (no 0)
let result = arr.reduce((sum, current) => sum + current);

alert( result ); // 15
```

The result is the same. That’s because if there’s no initial, then `reduce` takes the first element of the array as the initial value and starts the iteration from the 2nd element.

The calculation table is the same as above, minus the first row.

But such use requires an extreme care. If the array is empty, then `reduce` call without initial value gives an error.

Here’s an example:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let arr = [];

// Error: Reduce of empty array with no initial value
// if the initial value existed, reduce would return it for the empty arr.
arr.reduce((sum, current) => sum + current);
```

So it’s advised to always specify the initial value.

The method [arr.reduceRight](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight) does the same, but goes from right to left.

## [Array.isArray](https://javascript.info/array-methods#array-isarray)

Arrays do not form a separate language type. They are based on objects.

So `typeof` does not help to distinguish a plain object from an array:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
alert(typeof {}); // object
alert(typeof []); // object (same)
```

…But arrays are used so often that there’s a special method for that: [Array.isArray(value)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray). It returns `true` if the `value` is an array, and `false` otherwise.

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
alert(Array.isArray({})); // false

alert(Array.isArray([])); // true
```

## [Most methods support “thisArg”](https://javascript.info/array-methods#most-methods-support-thisarg)

Almost all array methods that call functions – like `find`, `filter`, `map`, with a notable exception of `sort`, accept an optional additional parameter `thisArg`.

That parameter is not explained in the sections above, because it’s rarely used. But for completeness we have to cover it.

Here’s the full syntax of these methods:

```javascript
arr.find(func, thisArg);
arr.filter(func, thisArg);
arr.map(func, thisArg);
// ...
// thisArg is the optional last argument
```

The value of `thisArg` parameter becomes `this` for `func`.

For example, here we use a method of `army` object as a filter, and `thisArg` passes the context:

[](https://javascript.info/array-methods# "run")

[](https://javascript.info/array-methods# "open in sandbox")

```javascript
let army = {
  minAge: 18,
  maxAge: 27,
  canJoin(user) {
    return user.age >= this.minAge && user.age < this.maxAge;
  }
};

let users = [
  {age: 16},
  {age: 20},
  {age: 23},
  {age: 30}
];

// find users, for who army.canJoin returns true
let soldiers = users.filter(army.canJoin, army);

alert(soldiers.length); // 2
alert(soldiers[0].age); // 20
alert(soldiers[1].age); // 23
```

If in the example above we used `users.filter(army.canJoin)`, then `army.canJoin` would be called as a standalone function, with `this=undefined`, thus leading to an instant error.

A call to `users.filter(army.canJoin, army)` can be replaced with `users.filter(user => army.canJoin(user))`, that does the same. The latter is used more often, as it’s a bit easier to understand for most people.

## [Summary](https://javascript.info/array-methods#summary)

A cheat sheet of array methods:

-   To add/remove elements:
    
    -   `push(...items)` – adds items to the end,
    -   `pop()` – extracts an item from the end,
    -   `shift()` – extracts an item from the beginning,
    -   `unshift(...items)` – adds items to the beginning.
    -   `splice(pos, deleteCount, ...items)` – at index `pos` deletes `deleteCount` elements and inserts `items`.
    -   `slice(start, end)` – creates a new array, copies elements from index `start` till `end` (not inclusive) into it.
    -   `concat(...items)` – returns a new array: copies all members of the current one and adds `items`to it. If any of `items` is an array, then its elements are taken.
-   To search among elements:
    
    -   `indexOf/lastIndexOf(item, pos)` – look for `item` starting from position `pos`, return the index or `-1` if not found.
    -   `includes(value)` – returns `true` if the array has `value`, otherwise `false`.
    -   `find/filter(func)` – filter elements through the function, return first/all values that make it return `true`.
    -   `findIndex` is like `find`, but returns the index instead of a value.
-   To iterate over elements:
    
    -   `forEach(func)` – calls `func` for every element, does not return anything.
-   To transform the array:
    
    -   `map(func)` – creates a new array from results of calling `func` for every element.
    -   `sort(func)` – sorts the array in-place, then returns it.
    -   `reverse()` – reverses the array in-place, then returns it.
    -   `split/join` – convert a string to array and back.
    -   `reduce/reduceRight(func, initial)` – calculate a single value over the array by calling `func`for each element and passing an intermediate result between the calls.
-   Additionally:
    
    -   `Array.isArray(value)` checks `value` for being an array, if so returns `true`, otherwise `false`.

Please note that methods `sort`, `reverse` and `splice` modify the array itself.

These methods are the most used ones, they cover 99% of use cases. But there are few others:

-   [arr.some(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)/[arr.every(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) check the array.
    
    The function `fn` is called on each element of the array similar to `map`. If any/all results are `true`, returns `true`, otherwise `false`.
    
    These methods behave sort of like `||` and `&&` operators: if `fn` returns a truthy value, `arr.some()`immediately returns `true` and stops iterating over the rest of items; if `fn` returns a falsy value, `arr.every()` immediately returns `false` and stops iterating over the rest of items as well.
    
    We can use `every` to compare arrays:
    
    [](https://javascript.info/array-methods# "run")
    
    [](https://javascript.info/array-methods# "open in sandbox")
    
    ```javascript
    function arraysEqual(arr1, arr2) {
      return arr1.length === arr2.length && arr1.every((value, index) => value === arr2[index]);
    }
    
    alert( arraysEqual([1, 2], [1, 2])); // true
    ```
    
-   [arr.fill(value, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill) – fills the array with repeating `value` from index `start` to `end`.
    
-   [arr.copyWithin(target, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin) – copies its elements from position `start` till position `end` into _itself_, at position `target` (overwrites existing).
    
-   [arr.flat(depth)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)/[arr.flatMap(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap) create a new flat array from a multidimensional array.
    

For the full list, see the [manual](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

From the first sight it may seem that there are so many methods, quite difficult to remember. But actually that’s much easier.

Look through the cheat sheet just to be aware of them. Then solve the tasks of this chapter to practice, so that you have experience with array methods.

Afterwards whenever you need to do something with an array, and you don’t know how – come here, look at the cheat sheet and find the right method. Examples will help you to write it correctly. Soon you’ll automatically remember the methods, without specific efforts from your side.

---
References:
- 