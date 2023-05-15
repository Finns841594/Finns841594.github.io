---
layout: post
title: "A function can have dynamic key in TypeScript"
date: 2023-05-15 10:00:00 +0200
---

## When writing a dynamic conponent, you can use a function with dynamic key in TypeScript

```typescript
 function getValueFromObjectByKey<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const person = {
  name: 'John',
  age: 30,
};

const name = getValueFromObjectByKey(person, 'name'); // returns 'John'
const age = getValueFromObjectByKey(person, 'age'); // returns 30
```

In this function, T is a generic that represents any possible type of the object, and K is another generic that is constrained to be a key of T (keyof T). The function returns a value of type T[K], which is the type of the value that the key points to in the obj.
