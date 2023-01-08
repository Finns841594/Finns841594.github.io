---
layout: post
title:  "Notes: Start A Project In TypeScript From Scratch"
date:   2023-01-08 11:00:00 +0200
categories: Note
---

# 0 How to start a project in Typescript from Scratch?



# 1 Install the necessary environment


## 1 Learn to use terminal

###  Terminal commands:
[10 bash commands every developer should know](https://appliedtechnology.github.io/protips/terminal-start)
[The SALT pro-tip blog on the terminal](https://dev.to/coderamrin/10-terminal-commands-every-developer-should-know-5ge4)

###  Custmise:
[Getting started with Oh My Zsh](https://dienbui.medium.com/using-oh-my-zsh-f65be6460d3f)


## 2 Use Git through terminal

Git is pre-installed by the operating system, so no need to install.

### Git commands:
`git init` (or git clone) to create/copy a new repository
`git status` to check the current status of the staging area, committed files, and branch.
`git add to` add files to the staging area (git rm to remove)
`git commit` to save files to the git repository
`git pull to` get changes from a remote repository
`git push to` send changes to a remote repository

Above are commands to use Git in terminal. But actually when we develop a project, we use Visual Studio Code, which has integreted Git in user interface of it.


## 3 Install Visual Studio Code

Install from their website. Then logged in with Github account, so the setting will be synchronized automatically.

The key is to find all useful and powerful extensions for the better efficiency in development. Extensions suggested by Salt:

Material Icon Theme
Prettier - Code formatting

Different themes:

[Top VSCode Themes to Try in 2022](https://www.tabnine.com/blog/top-vscode-themes/)
(Darker themes might better for eyes, afterall we watched screen the whole day...)

Extra Links by Salt:

[Getting started with Visual Studio Code](https://code.visualstudio.com/docs/introvideos/basics)
[10 vs code extension every web developer should have](https://dev.to/javascriptacademy/top-10-vscode-extensions-for-web-developers-19jg)
[Extensions for JavaScript developers](https://livecodestream.dev/post/best-vscode-extensions-for-javascript/)


## 4 Install JavaScript

One don't really need to install JavaScript, because it is a language among browers. Its the node which makes JavaScript runable on the os.

So, instead of installing JavaScript, here we install nvm, Node Version Manager, by the following command in terminal:
`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash`

More information check here:
https://github.com/nvm-sh/nvm#installing-and-updating

The idea is, after one write a program in `program.js`, one execute it by `npm start` in terminal, nmp will looking for the configuration in `package.json` at current path, and then execute the script, which will execute the `program.js` in node.



# 2 Start a project


## 1 Creat a folder for the project


## 2 Initialize Node application

`npm init --yes`


## 3 Installing dependencies

There are two types of dependencies: (normal) dependencies and development dependencies, the formers are for the program, the laters are for development process and not necessary for program running in "real" situation. They are installed in different ways in Node:

For the "dependencies": `npm install <package-name> [--save-prod]`

For the "devDependencies": `npm install <package-name> --save-dev`

Check [here](https://docs.npmjs.com/specifying-dependencies-and-devdependencies-in-a-package-json-file) for more.

To use typescript, we need to install it here as a dependency.
Abd when install dependencies for development, install the package in this syntax: `npm install @types/<package-name> --save-dev`.


## 4 Create a folder called `src` for .ts files


## 5 Create a `tsconfig.json` file in root path of the project with the following contents:

```js
{
  "extends": "@tsconfig/node16/tsconfig.json",
  "compilerOptions": {
    "outDir": "dist"
  },
  "include": ["src"],
  "exclude": ["node_modules"],
}
```

One can also generate this file by `npx tsc --init --rootdir src --outdir dist`.


## 6 confige `script` part in `package.json`

Check [here](https://docs.npmjs.com/cli/v9/using-npm/scripts) for more.

For example:
```js
"scripts": {
  "build": "tsc",
  "dev": "ts-node src/index.ts",
  "test": "mocha -r ts-node/register src/**/*.test.ts"
},
```
When run `npm test`, `npm` will execute `mocha` to test the file called `test.ts` in path `src`.



# 3 Main files for a project

All contents below are well explained here:
https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web


## 1 ts file template

The "template" here is only for developing a web project with `Express` server
```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello fellow developer!');
});

const port = 3000
app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}/`);
});
```

One can import a function from another js file by 
```js
const someApp = require('./functions.js');
```
And in `functions.js`:
```js
export function sayHi(user) {
  alert(`Hello, ${user}!`);
}
```


## 2 html file template

### 0 It's better to have all static files in one folder in the project, `static`.

### 1 template.html and index.html
But its always good to inherete structure from a template.html, which written in this way:
{% raw %}
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- Extending syntax here -->
    <title>{% block title %}My amazing site{% endblock %}</title>
</head>
<body>
    <!-- Extending syntax here -->
    {% block content %}{% endblock %}
</body>
</html>
```
{% endraw %}

other html files can just inherite it by:
{% raw %}
```html
{% extends "template.html" %}

{% block title %}{{ section.title }}{% endblock %}

{% block content %}
<h1>{{ section.title }}</h1>

{% for story in story_list %}
<h2>
  <a href="{{ story.get_absolute_url }}">
    {{ story.headline|upper }}
  </a>
</h2>
<p>{{ story.tease|truncatewords:"100" }}</p>
{% endfor %}
{% endblock %}
```
{% endraw %}

Above are from [here](https://docs.djangoproject.com/en/4.1/ref/templates/language/)

### 2 Emmet
Type `!` and then `tab` to have a basic structure of a html file.

Here we are using [Emmet](https://code.visualstudio.com/docs/editor/emmet). One can have a quick html structure with lorem content by this way: `main>article.story*3>h2.story-heading>lorem8`

### 3 reference a css, or Cascading Style Sheet, file
In `<head>`, add a `<link href="style.css" rel="stylesheet">`

### 4 reference a Javascript file
`<script src="myscripts.js"></script>`



# 4 Coding

I think the content above has covered nicely how to start a web project from scratch. Programming part will involve other knowledge about coding, which are the contents for other posts. Lets end this one here. 

Happy Coding!









