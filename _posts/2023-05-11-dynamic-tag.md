---
layout: post
title: "Dynamic tag in React projects"
date: 2023-05-11 16:00:00 +0200
---

## Dynamic tag in React projects

```typescript
function MyComponent({ tag, children }) {
  const Tag = tag as keyof JSX.IntrinsicElements;

  return <Tag>{children}</Tag>;
}
```
So `Tag` is reserved for JSX. as long as tag is a valid string, such as `h1` or `p`, this works.

