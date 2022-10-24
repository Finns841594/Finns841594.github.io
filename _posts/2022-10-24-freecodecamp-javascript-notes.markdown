---
layout: post
title:  "Notes for Free Code Camp Course JavaScript"
date:   2022-10-24 14:21:14 +0200
categories: JavaScript
---

#0 
Self learning Javascript on Free Code Camp: https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/, leave notes here for the future review.

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

#2 ECMAScript 6
