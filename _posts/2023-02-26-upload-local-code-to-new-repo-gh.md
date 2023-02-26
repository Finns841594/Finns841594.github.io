---
layout: post
title: "How to upload local working repo to a new repo"
date: 2023-02-26 15:00:00 +0200
---

### 1. Create a new repo by github CLI
Run following command and then follow promts
```bash
git repo create
```

### 2. Set the url of current working repo to url of the new repo

For example:
```bash
git remote set-url origin git@github.com:Finns841594/weekendtest-shoppingWishList.git
```

### 3. add commit and push, done

reference [link](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories)