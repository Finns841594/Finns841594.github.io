---
layout: post
title: 'Generate UUID without 3rd library'
date: 2024-01-11 13:30:00 +0200
---

### Using crypto.randomUUID()

(ES2021 and newer): This method provides a more robust way of generating unique IDs using the built-in crypto module available in modern JavaScript environments. The randomUUID() method generates a Universally Unique Identifier (UUID), which has a very low probability of duplication.

```
const  generateUniqueID = () => {
  return crypto.randomUUID();
}
```

### Using Math.random() and Date.now()

This is a simple method where you combine a random number with the current timestamp to generate a unique ID. However, it's important to note that this method does not guarantee absolute uniqueness, but it's generally sufficient for many use cases.

```
const  generateUniqueID = () => {
  return 'id-' + Math.random().toString(36).substr(2, 9) + '-' + Date.now();
}
```
