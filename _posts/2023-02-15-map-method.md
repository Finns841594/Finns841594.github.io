---
layout: post
title: "Amazing way of using .map method"
date: 2023-02-15 22:32:00 +0200
---

[here](https://www.codewars.com/kata/54b42f9314d9229fd6000d9c/solutions/typescript)
Found this amazing solution from codewars.com:
```js
export function duplicateEncode(word: string){
    // ...
    return word
    .toLowerCase()
    .split('')
    .map((a, i, w) => {
      return w.indexOf(a) == w.lastIndexOf(a) ? '(' : ')'
    })
    .join('')
}
```
solved the problem which I used code below:
```js
export function duplicateEncode(word: string){
    let lowerWord = word.toLowerCase()
    let repeatedChar: string[] = []
    for (let i = 0; i < lowerWord.length - 1; i++) {
      if (lowerWord.slice(i+1).includes(lowerWord[i])) {
        repeatedChar.push(lowerWord[i])
      }
    }
    
    let result = ''
    let wordArray = lowerWord.split('')
    wordArray.map(char => {
      if (repeatedChar.includes(char)) {
        result += ')'
      } else {
        result += '('
      }
    })
  
    return result
}
```

its cool to check if repeatition exits in an array by .map
```js
exampleArray.map((currentItem, currentItemIndex, fullArray) => {
      return fullArray.indexOf(currentItem) == fullArray.lastIndexOf(currentItem) ? true : false
    })
```