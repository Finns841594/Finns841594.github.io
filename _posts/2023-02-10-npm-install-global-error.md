---
layout: post
title: "Problem in solution in global installation by npm"
date: 2023-02-10 16:00:00 +0200
---

# Offical solutions

[Resolving EACCES permissions errors when installing packages globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally)

# The missing information

In the solution "Manually change npm's default directory", it temporaly tell the system where to find the newly installed package by creating a file `~/.profile`, and then call it by bash command `source ~/.profile`.

So this is limited in the current terminal only. If you open a new terminal, you need to `source ~/.profile` again.

