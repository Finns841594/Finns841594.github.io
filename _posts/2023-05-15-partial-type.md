---
layout: post
title: "Partial types in TypeScript"
date: 2023-05-15 10:00:00 +0200
---

## You can give a type as partial of defined type in TypeScript

```typescript
const updatePuppyInfo = async (id: number, puppyInfo: Partial<Puppy>): Promise<Puppy> => {
  const puppy = await getPuppy(id);
  return { ...puppy, ...puppyInfo };
}
```

