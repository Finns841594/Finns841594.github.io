---
layout: post
title: "Get current domain in Next.js"
date: 2023-05-25 14:30:00 +0200
---

## Simple example of getting current domain and port in Next.js

```ts
// get current host name
const host = window.location.hostname
const port = window.location.port

// function that get posts from api
export const getPosts = async () => {
  const res = await fetch(`http://${host}:${port}/api/posts`)
  const posts = await res.json()
  return posts.posts
}
```