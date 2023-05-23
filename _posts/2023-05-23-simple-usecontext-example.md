---
layout: post
title: "Simple useContext example" 
date: 2023-05-23 09:30:00 +0200
---

## Simple useContext example


### 1. Create a context

Create a file called `SomethingContext.tsx`, I will use `PostsContext` as an example for a blogging website:

```typescript
import { Dispatch, SetStateAction, createContext } from "react";
import { Post } from "./types";

interface PostsInfoContextProp {
  posts: Post[];
  setPosts: Dispatch<SetStateAction<Post[]>>;
}

export const PostsContext = createContext<PostsInfoContextProp>({
  posts: [],
  setPosts: () => {},
});
```

### 2. Wrap the context provider around the components

In a Next.js app, you can wrap the context provider around the `src/app/pages.tsx`:

```typescript
'use client'

import { PostsContext } from './PostsContext'
import { useEffect, useState } from 'react'
import { Post } from './types'
import { getPosts } from './components/functions/async'

export default function Home() {
  const [posts, setPosts] = useState<Post[]>([])

  // To set initial state
  useEffect(() => {
    getPosts().then((posts) => {
      setPosts(posts)
    } ).catch((err) => {
      console.log('err', err)
      })
  }, [])
  
  return (
    // Wrap the context HERE
    <PostsContext.Provider value={{ posts, setPosts }}>
      <main className="main">
        ...
        <OtherComponents />
        ...
      </main>
    // And HERE
    </ PostsContext.Provider>
  )
}
```

### 3. Use the context in other components

```typescript
import { useContext } from 'react'

  ...
  const { posts } = useContext(PostsContext)
  ...
```

