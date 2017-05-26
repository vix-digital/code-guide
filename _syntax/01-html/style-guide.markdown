---
title:  "HTML Style Guide"
categories: html
---

#### Syntax

- Use soft tabs with four spaces, it makes sure that code renders the same in any environment 
- Nested elements should be indented once (four spaces)
- Always use double quotes, never single quotes, on attributes
- Don’t include a trailing slash in self-closing elements like `<img>` as the HTML5 spec says they’re optional
- Don’t omit optional closing tags on elements like `</li>` and `</body>`

```html
<!DOCTYPE html>
<html>
  <head>
    <title>A fantastic page title</title>
  </head>
  <body>
    <img src="logo.png" alt="VIX Digital logo">
    <h1 class="page-title">Welcome to VIX Digital!</h1>
  </body>
</html>
```

#### HTML5 doctype

Enforce standards mode and more consistent rendering in every browser possible with this simple doctype at the beginning of every HTML page.

```html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
```

#### Language attribute 

Taken from the HTML5 spec:

>”Authors are encouraged to specify a lang attribute on the root html element, giving the document’s language. 
This aids speech synthesis tools to determine what pronunciations to use, translation tools to determine what rules to use and so forth.”

```html
<html lang="en-us">
  <!-- … -->
</html>
```

#### Character encoding

To ensure proper rendering of content, declare an explicit character encoding. When doing so, you can avoid using character entities in your HTML, as long as their encoding matches that of the document. This is usually UTF-8. 

```html
<head>
  <meta charset="UTF-8">
</head>
```

#### CSS and JavaScript includes

According to HTML5 spec, there is no need to specify a `type` when including CSS and JavaScript files as `text/css` and `text/javascript` are their respective defaults. 

This applies to: 
- Using link
- Using style
- Using script

```html
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- In-document CSS -->
<style>
  /* … */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>

```

#### Reducing markup: practicality over purity

We should always try to maintain HTML standards and semantics, but without neglecting practicality. Use the lease amount of markup with the fewest intricacies whenever possible.

Try to avoid using superfluous parent elements when writing HTML. As this can often lead to iteration and refactoring to produce less HTML. 

Example:

```html
<!-- Not so good -->
<span class="profile-picture">
  <img src="…">
</span>

<!-- Much better -->
<img class="profile-picture" src="…">
```

#### Attribute order
HTML attributes should come in this particular order for easier reading of code
 
- `class`
- `id`, `name`
- `data-*`
- `src`, `for`, `type`, `href`, `value`
- `title`, `alt`
- `role`, `aria-*`

Classes are great for reusable components so they should always come first.
IDs are more specific and should be used more sparingly e.g. for in-page bookmarks, so they come second 

```html
<a class="…" id="…" data-toggle="tooltip" href="#">
  A link
</a>

<input class="form-control" type="text">

<img src="…" alt="…">
```

#### JavaScript generated markup

Writing markup in JavaScript files makes content much harder to find, harder to edit and less performant. Wherever possible HTML should always be written in `.html` files.
