---
layout: post
title: "Manage Date"
date: 2023-06-13 15:30:00 +0200
---

## About time and date in Javascript

### Get current date

```js
const today = new Date();
```

The `today` object is a `Date` object, which is a built-in object in Javascript. 
You can convert it into string by using `toString()` method.

```js
const today = new Date();
console.log(today.toISOString());
// OUTPUT: 2023-06-13T13:56:25.031Z
console.log(today.toDateString());
// OUTPUT: Tue Jun 13 2023
```

### Set a date

#### Set a date by string

```js
const tomorrow = new Date('2023-06-14');
console.log(tomorrow.toDateString());
// OUTPUT: Wed Jun 14 2023
const wrongYesterday = new Date(23, 5, 12);
console.log(wrongYesterday.toDateString());
// It will be 1923-06-12, not 2023-05-12, months are 0-based, years are 1900-based
// OUTPUT: Fri Jun 12 1923
const yesterday = new Date(2023, 5, 12);
console.log(yesterday.toDateString());
// OUTPUT: Fri Jun 12 2023
```

##### One can also pass in time to the `Date` constructor.

1. by string
```js
const tomorrow = new Date('2023-06-14T00:00:00');
console.log(tomorrow.toDateString());
// OUTPUT: Wed Jun 14 2023
```
2. by milliseconds number
```js
const aDay = new Date(1666342680472);
console.log(aDay);
// OUTPUT: 2022-10-21T08:58:00.472Z
```
Note: this number is the milliseconds since 1970-01-01 00:00:00 UTC.
Its called Unix Epoch.


#### Date calculation

```js
const today = new Date();
const tomorrow = new Date(today);
tomorrow.setDate(today.getDate() + 1);
console.log(tomorrow.toDateString());
// OUTPUT: Wed Jun 14 2023
```

#### Date and Time comparison

##### Compare two dates

```js
const today = new Date();
const tomorrow = new Date(today);
tomorrow.setDate(today.getDate() + 1);
console.log(today < tomorrow);
// OUTPUT: true
```

##### Compare two times

```js
const today = new Date();
const aDay = new Date(1666342680472);
aDay.setDate(today.getDate() + 1);
console.log(today.getTime() < aDay.getTime());
// OUTPUT: flase
```

