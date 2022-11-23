---
layout: post
title:  "Django Notes for CS50 Web"
date:   2022-11-02 14:00:00 +0200
categories: django
---

# 0 Intro
Notes when were working with "problem set 1: wiki" for course CS50 Web Programming.


# 1 How to render a string into a markdown format text
The function is not builtin, need to install it by `pip3 install markdown2`.
code in views.py:
```python
# Need to install it first.
import markdown2

# The funciton for render the page of each entry
def entries(request, titlefromurl):
    # Get the string by title 
    entry = util.get_entry(titlefromurl)
    if entry:
        # WATCH HERE, render first, and then pass in to html page
        entry = markdown2.markdown(f"{entry}")
        return render(request, "encyclopedia/entry.html", {
            "entry": entry, "title": titlefromurl
        })
    else:
        message = f"'{titlefromurl}' has not been created yet"
        return render(request, "encyclopedia/error.html", {
            "message": message
        })
```

then code in html page:

```html
{% block body %}
    <!-- need to add a "safe" filter so it can display correctly -->
    {{ entry|safe }}
{% endblock %}
```


# 2 How to compile a parameter in `{% url %}`
example is below:

```html
<ul>
    {% for entry in entries %}
        <li><a href="{% url 'entries' titlefromurl=entry %}">{{ entry }}</a></li>
    {% endfor %}
</ul>
```

Code above builds a list of links, every link shows the name of each `entry` in list `entries`, and every link has a url based ono parameter `entry` as well.
Inspired from the article here: https://cloud.tencent.com/developer/article/1736241.


# 3 Syntax to get the data from <form>
get method by `if request.method == "POST"`
get value by `request.GET['q']` when by `get` method from a label which name is `q`.


# 4 Input
`<input type="text">` is not friendly for multiline text, one should use `<textarea></textarea>`
