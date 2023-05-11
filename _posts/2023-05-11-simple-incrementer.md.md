---
layout: post
title: "a simple incrementer to generate simple numeric id"
date: 2023-05-10 16:00:00 +0200
---

## Shut up and look at the code

It will generate a new id based on the highest id in the database.

```typescript
interface Puppy {
    id: number;
    name: string;
    age: number;
    breed: string;
}

export const idIncrementer = (db:Puppy[]) => {
    //find the highest id in the db
    const highestId = db.reduce((acc:number, curr:Puppy) => {
        if (curr.id > acc) {
            return curr.id;
        }
        else {
            return acc;
        }
    }
    , 0);
    //increment the highest id by 1
    const newId = highestId + 1;
    return newId;
};
```

One line version for javascript:

```javascript
const idIncrementer = (db) => db.reduce((acc, curr) => curr.id > acc ? curr.id : acc, 0) + 1;
```
