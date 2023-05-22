---
layout: post
title: "Simple Next.js api with TypeScript" 
date: 2023-05-22 17:00:00 +0200
---

## Simple Next.js api with TypeScript

It is annoying that I can't find a simple example of Next.js api with TypeScript. Here is a simple example I wrote:

```typescript
// src/app/api/posts/route.tsx
import {blogPosts} from './data';
import { NextResponse } from 'next/server';
 
// example: http://localhost:3000/api/posts will retun all posts
// example: http://localhost:3000/api/posts?tag=tag1 will retun all posts with tag1
export async function GET(request: Request) {
  const {searchParams} = new URL(request.url);
  const tag = searchParams.get('tag')
  if (tag) {
    const filteredPosts = blogPosts.posts.filter(post => post.tags.includes(tag));
    return NextResponse.json(filteredPosts);
  } else {
    return NextResponse.json(blogPosts);
  }
}
```

In the example above, I didn't write the code which communicate to a real database, instead, I just import a static data from a file called `data.ts` at the same directory.


