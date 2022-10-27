---
layout: post
title:  "Notes for Free Code Camp Course JavaScript"
date:   2022-10-24 14:21:14 +0200
categories: JavaScript
---

# 0 About this post
I am learning Javascript on Free Code Camp: https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/, leave notes here for the future review.

# 1 Basic JavaScript

## 1 Meanning of common characters

|  Code  | Output |
|  ----  |  ----  |
| \'	| single quote |
| \"	| double quote |
| \\	| backslash |
| \n	| newline |
| \t	| tab |
| \r	| carriage return |
| \b	| word boundary |
| \f	| form feed |

## 2 Index

Javascript的string不能直接用[-1]的方法来取得最后一个字符
```javascript
name = “Feng”
❌ var lastCharacter = name[-1] 
✅ var lastCharacter = name[name.length -1]
```

## 3 Notes based on Python

1. append in Python is push in JavaScript. Similar methods are pop, shift, unshift.
2. Define a function in JS is function
3. A variable defined out side a function has global scope.
4. `int("110")` in Python is `parseInt("110")` in JS. You can use `parseInt` to parse a binary string into a Int by adding a second parameterr: `parseInt("0110", 2)`.

## 4 Notes about data type comparison with Python

1. An array in JS is similar to a list in Python.
2. An object in JS is similar to a dict in Python.

## 5 To get a value from an object

```js
const collection = {
  2548: {
    albumTitle: 'Slippery When Wet',
    artist: 'Bon Jovi',
    tracks: ['Let It Rock', 'You Give Love a Bad Name']
  },
  2468: {
    albumTitle: '1999',
    artist: 'Prince',
    tracks: ['1999', 'Little Red Corvette']
  }
};

console.log(recordCollection[2548]); // Can get the value
console.log(recordCollection.2548);  // Can NOT get the value

console.log(recordCollection[2548].artist);  // Can get the value
console.log(recordCollection[2548]['artist']);  // Can get the value
```

## 6 Detecting undefined in a object

```js
if (aCollection[aindex][aproperty] === undefined){
  console.log("yes, it is undefined");
};
```
`null` and `undefined` are different. And unlike Python, there is no such a thing like `None`.

## 7 Multiple conditional operators: 'if' 'else' in one line

A format syntax like `a ? b :c` in JS means if `a` is `true` then `b` else `c`. For example:

```js
function checkEqual(a, b) {
  return (a == b) ? "Equal" : "Not Equal"
}
```
or several else if :
```js
function checkSign(num) {
  return (num == 0) ? "zero" : (num > 0) ? "positive" : "negative";
}
```

# 2 ECMAScript 6

## 1 Variables definetion

1. `var` is gobal and `let` is local. So when use `for` loop, use `let`:
```js
for (let i=0;i<10;i++){
  console.log(i);
}
```

2.  Use `let` only when you know the variable will be re-assign. Use `const` for define a variable for most cases, it is mutable:
```js
const s = [5, 6, 7];
s = [1, 2, 3];
s[2] = 45;
console.log(s);
```
code above will display `[5, 6, 45]`.

## 2 Arrow Function, like lambda in Python
```js
// Arrow function with one input parameter;
const doubler = item => item * 2;
doubler(4);
// Arrow function with more than one parameter;
const multiplier = (item, multi) => item * multi;
multiplier(2,4);
// Arrow function with parameter has its default value;
const greeting = (name = "Anonymous") => "Hello " + name;
console.log(greeting("John"));
console.log(greeting());
```

## 3 Spread Operator
```js
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr); 
```
Use `...arr` because `Math.max(input)` the `input` can not be an array, it must be comma separated arguments.
To copy a list in this way:
```js
let list1 = [1,2,3];
let list2 = [...list1];
```

## 4 Destructing assignment
1. To get the value from an object
```js
const user = { name: 'John Doe', age: 34 };

```
In ES5:
```js
const name = user.name;
const age = user.age;
```
Now in ES6:
```js
const { name, age } = user;
```
2. Notice that the name of new assigned variable must be consist with the key name, thus `name` and `age`. If one wants to assign to a different variable name, use the method below:
```js
const { name: newName, age: newAge } = user;
```
3. And here is how you get and assign the value which stored in nested objects:
```js
const user = {
  johnDoe: { 
    age: 34,
    email: 'johnDoe@freeCodeCamp.com'
  }
};

const { johnDoe: { age: userAge, email: userEmail }} = user;
```
4. Assign Variables from an array:
Use `,` to skip unwished values.
```js
const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b);
// output: 1, 2

const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c);
// output: 1, 2, 5
```
5. A interested way to switch values for two variables:
```js
let a = 1, b = 2;
// switching:
[b, a] = [a, b];
```
6. Get the values from an array by de-selecting way:
```js
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b);
// output: 1,2
console.log(arr);
// output: 2,3,4,5,7
```
7. Applying destructuring assignment in arrow function:
```js
const stats = {
  max: 56.78,
  standard_deviation: 4.34,
  median: 34.54,
  mode: 23.87,
  min: -0.75,
  average: 35.85
};

// ES6 Magic below
const half = ({max, min}) => (max + min) / 2.0; 
```
## 5 Template literal to create a string
1. Python has it... Just notice the syntax differences between `` ` `` and `"` for the string, and `${}` for place holder:
```js
const person = {
  name: "Zodiac Hasbro",
  age: 56
};

const greeting = `Hello, my name is ${person.name}!
I am ${person.age} years old.`;

console.log(greeting);
```
2. Easy defining? Don't get it very well:
```js
// In ES5
const getMousePosition = (x, y) => ({
  x: x,
  y: y
});
// In ES6:
const getMousePosition = (x, y) => ({ x, y });
```

3. Declaretive Functions:
Don't get it well neither:
In ES5:
```js
const person = {
  name: "Taylor",
  sayHello: function() {
    return `Hello! My name is ${this.name}.`;
  }
};
```
In ES6 you can remove the function:
```js
const person = {
  name: "Taylor",
  sayHello() {
    return `Hello! My name is ${this.name}.`;
  }
};
```

## 6 Class
I don't understand very well about this, but here is an example about classes:
```js
// Create a class:
class Vegetable {
  constructor(input){
    this.name = input;
  }
}

// initializing an object with a class:
const carrot = new Vegetable('carrot');

// Call this object:
console.log(carrot.name);
```

## 7 Promise
I don't know why have it. It is basically a if...else function:
```js
const makeServerRequest = new Promise((resolve, reject) => {
  // responseFromServer represents a response from a server
  let responseFromServer;
    
  if(responseFromServer) {
    resolve("We got the data")
  } else {  
    reject("Data not received")
  }
});
```

It says one way to use it is followed a `then` method:
```js
const makeServerRequest = new Promise((resolve, reject) => {
  // responseFromServer is set to true to represent a successful response from a server
  let responseFromServer = true;
    
  if(responseFromServer) {
    resolve("We got the data");
  } else {  
    reject("Data not received");
  }
});

makeServerRequest.then(result => {
  console.log(result);
});
```
In this way, if `responseFromServer` is `true`, print out the result. (Still, I think it is a simple if...else function)
Or, if fell, you use `catch` method:
```js
makeServerRequest.catch(error => {
  console.log(error);
})
```