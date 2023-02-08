---
layout: post
title:  "Jekyll tag errors"
date:   2023-01-08 17:00:00 +0200
categories: Note
---

# 0. github-pages Error:  Liquid syntax error Unknown tag 'example'

If any markdown post has {% raw %}{{example}}{% endraw %} inside, jekyll will have problem to render it.
I found the solution here:
https://github.com/orgs/community/discussions/23170

Basically you need to add {% raw %}`{% raw %}` and `{% endraw %}`{% raw %} at the beginning and ending of the potentially trouble-making code blocks in your .md file.

More problem could happen later, I leave this posts here for future:

https://www.tomordonez.com/curly-braces-markdown-jekyll/
