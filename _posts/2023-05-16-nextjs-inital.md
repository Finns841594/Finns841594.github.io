---
layout: post
title: "Notes about Next.js"
date: 2023-05-16 15:00:00 +0200
---

## 0. To create a new Next.js app

```bash
npx create-next-app@latest
```

## 1. api routes is different from route handlers

check [this](https://nextjs.org/docs/app/building-your-application/routing/router-handlers) out.

In short, Route Handlers are only available inside the app directory. They are the equivalent of API Routes inside the pages directory meaning you do not need to use API Routes and Route Handlers together.

## 2. installing Jest

```bash
npm i -D jest @types/jest ts-jest typescript
```
still working on writing test cases for Next.js app.
