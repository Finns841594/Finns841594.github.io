---
layout: post
title: "JEST in TypeScript project for beginners (like me)"
date: 2023-05-10 16:00:00 +0200
---

## 1. What is JEST?
JEST is a JavaScript testing framework. I started my programming practice with Mocha, so JEST is relativly less familier to me.

Besides, my previous experience with TDD is basically manual testing due to the lack of time learning and writing testing files. But this time I spend some time to learn JEST and do really TDD, I found it acutally saving more time than manual testing. I don't need to shift windows to click Postman everytime I modeifed something.

## 2. How to setup JEST for TypeScript project?
Sometimes it is with initial setup with Express.js project. But I leave a command here for furture me.
`npm i -D jest @types/jest ts-jest typescript`

## 3. How to write a test case?
I will use a simple example to show the main structure and syntax of JEST test case.

```typescript
import request from 'supertest';
import app from './app'; // which is the express app

describe('/api/puppies get methond', () => {
  it('it should return a list of puppies', async () => {
    const res = await request(app).get('/api/puppies');
    expect(res.statusCode).toEqual(200);
    expect(res.body.length).toBeGreaterThan(1); // at least have 2 puppies
  })
});
```

more methods other than `toEqual` and `toBeGreaterThan` can be found in [JEST document](https://jestjs.io/docs/expect).

## 4. JEST in package.json
```json
"scripts": {
  "test": "jest --watch --silent"
}
```
`--watchAll` means JEST will watch all the files and run the test cases when there is any change. 
`--verbose` means JEST will show more details in the terminal.
`--silent` means JEST will not show the details in the terminal. So remeber to remove it when you want to see the details like console.log in the terminal.
