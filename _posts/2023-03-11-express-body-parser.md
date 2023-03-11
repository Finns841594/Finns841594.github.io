---
layout: post
title: "Note: Express body-parser"
date: 2023-03-11 21:40:00 +0200
---

### client send a post request but req.body is undefined in the express backend?

body-parser is a necessary middle ware to handle POST requests. To handle a POST request with a JSON-formatted request body:

```js
const express = require('express');
const bodyParser = require('body-parser');
const app = express();

app.use(bodyParser.json());

app.post('/users', (req, res) => {
  // the name and age below will be undefined if the middle ware is missing  
  const {name,age} = req.body;
  res.send('successful info')
})

app.listen(3000, ()=>{
  console.log('Server started on port 3000')
})

```

Similar when the backend need to deal with urlencoded-formatted request body:
`app.use(bodyParser.urlencoded({ extended: true}))`
remember to set `extended` to `true` to support parsing request bodies containing nested objects.

PS: a simple example of urlencoded body: `127.0.0.1:3000/users/name=Adam&age=29&city=New+York`