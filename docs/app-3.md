---
title: Advanced Programming with Python
author: Pepe García
email: jgarciah@faculty.ie.edu
date: 2020-04-20
lang: en
---

# Plan for today

- Review homework
- Sending files from folder
- working with HTML

# Homework

# Serving static files

Being able to serve static files is vital for websites.  They can be
images, videos, CSS templates, or anything you imagine.

# Serving static files

In flask we can serve static files using the **send_from_directory**
function.

from flask import send_from_directory

```python
@app.route("/images/<image>.png")
def serve_image(image):
    return send_from_directory(
        "images/",
        filename="{}.png".format(image))
```

# Serving static files

Do you see something that can go wrong in the previous route?  Try to
search for an image that's not there.

# Practice

## https://github.com/app-2020/app-sync-4

See example-1

# Serving HTML

HTML files, as files of any other type can be served using the
**send_from_directory** function.

# Serving HTML

```python
@app.route("/")
def index():
    return send_from_directory("html", filename="index.html")
```

# HTML

**HTML** stands for **Hypertext Markup Language**.  It's a language
that describes how the information\
should be presented in webpages

# HTML

HTML documents are defined by tags, which look as follows:

```html
<tag>content</tag>
```

# HTML

Let's see a real world example

```html
<p>this is a paragraph</p>
```

the **`<p>`** tag is used to represent paragraphs!

# HTML structure

In HTML, all the visible structure of the document must go inside the
**`<body>`** tag

```html
<body>
  <p>the 'p' tag represents a paragraph</p>
</body>
```

# HTML structure

On the other hand, all the HTML tags that are not meant to be rendered
go inside the **`<head>`** tag.

For example, the title tag is one of these tags:

```html
<head>
  <title>this is the title</title>
</head>
<body>
  <p>the 'p' tag represents a paragraph</p>
</body>
```

# HTML structure

Finally, for an HTML document to be well formed, it needs to be wrapped
in the HTML tag

```html
<html>
  <head>
    <title>this is the title</title>
  </head>
  <body>
    <p>the 'p' tag represents a paragraph</p>
  </body>
</html>
```

# HTML structure

Let's create our first web page!

# Some HTML tags

Now let's see some HTML tags

# Paragraphs

text paragraphs in HTML are represented with the **`<p>`** tag

```html
<p>
this is the first paragraph of my text.  As you can see it
also contains <strong>other tags</strong>
</p>
<p>
In the second paragraph, I wanted to write this other thing
but I'm running out of ideas for what to write
</p>
<p>
In the last paragraph of my text I want to <strong>finish</strong>
it
</p>
```

# Headings

Headings are used in html in the same way a word doc, or in a newspaper,
to capture reader's attention.


What's the most important heading in the image? and the second one?

# Headings

HTML provides us with 6 different tags to represent 6 different levels
of headings.

```html
<h1>this is the h1</h1>
<h2>this is the h2</h2>
<h3>this is the h3</h3>
<h4>this is the h4</h4>
<h5>this is the h5</h5>
<h6>this is the h6</h6>
```

# Hyperlinks

Hyperlinks are the most vital part of HTML.  They allow us to go to
other documents when clicking them.

# Hyperlinks

We create links in HTML using the **`<a>`** tag. `a`, in this case, stands for _anchor_.

```html
<a>this is a link, but doesn't have an address to go to...</a>
```

In order to give an address to the link, we need to use the **href
attribute**:

```html
<a href="https://google.com">this takes you to Google!</a>
```

# Images

We use the **`img`** tag with the **`src`** attribute in order to embed
images in our HTML documents.

The `src` attribue can be either a route to a local file, or a url to
a file in the Internet.

```python
<img src="/home/pepe/Desktop/image.jpg">
```

# Homework

Create the HTML for what it could be your Wikipedia entry.

- different parts of your life
- links to your presence in the web

# Resources

Codecademy course to learn HTML: **<https://www.codecademy.com/courses/learn-html>**

Mozilla development network docs: **<https://developer.mozilla.org/en-US/docs/Web/HTML>**
