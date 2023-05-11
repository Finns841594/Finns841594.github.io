---
layout: post
title: "Setting up debugger in VSCode for testing"
date: 2023-05-10 16:00:00 +0200
---

## Following bash code can be used to set up debugger in VSCode for testing

```bash
mkdir .vscode
echo "{
  \"version\": \"0.2.0\",
  \"configurations\": [
    {
      \"name\": \"Run Tests\",
      \"request\": \"launch\",
      \"runtimeArgs\": [
        \"run\",
        \"test\"
      ],
      \"runtimeExecutable\": \"npm\",
      \"skipFiles\": [
        \"<node_internals>/**\"
      ],
      \"type\": \"node\"
    }
  ]
}
" > .vscode/launch.json
```