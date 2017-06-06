---
title:  "CSS Style Guide"
categories: css
---

#### Syntax

- Use soft tabs with two spaces - this is the only way to ensure code renders the same in all environments
- When grouping selectors, keep individual selectors to a single line
- Include on space before the opening brace of declaration blocks for legibility 
- Place closing brackets of declaration blocks on a new line
- Include one space after `:` for each declaration
- Each declaration should appear on its own line for more accurate error reporting
- End all declarations with a semi-colon. The last declaration's is optional, but code is more error prone without it
- Comma-separated property values should include a space after each comma (e.g. `box-shadow`)
- Don't include spaces after commas within `rgb()`, `rgba()`, `hsl()`, `hsla()`, or `rect()` values. This helps to differentiate multiple colour values (comma, no space) from multiple property values (comma with space)
- Don't prefix property values or colour parameters with a leading zero (e.g. `.5` instead of `0.5` and `-.5px` instead of `-0.5px`)
- Lowercase all hex values, e.g. `#fff`. Lowercase letters are much easier to discern when scanning a document as they tend to have more unique shapes
- Use shorthand hex values where available e.g. `#fff` instead of `#ffffff`
- Quote attribute values in selectors e.g. `input[type="text"]. They're only optional in some cases, and it's good practice for consistency 
- Avoid specifying units for zero values e.g `margin: 0;` instead of `margin: 0px;`


```css
/* Not very good CSS */
.selector, .selector-secondary, .selector[type="text"] {
  padding:15px;
  margin:0px 0px 25px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

/* Very good CSS */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}

```

#### Declaration order

Related property declarations should be grouped together in the following order: 

1. **Positioning** comes first because it can remove an element from the normal flow of the document and override box model related styles 
2. **Box model** Comes next as it dictates a component's dimensions and placement
3. **Typographic** takes place inside the component and doesn't impact 1. or 2. so comes last
4. **Visual** same as typographic

```css
.declaration-order{
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;
  
  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #d5d5d5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

#### Media query placement

Place media queries as close as possible to their relevant rule sets. Don't bundle them all in a separate stylesheet or at the end of the document. Doing so only makes it easier for people to miss them in the future.

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
  .element { ... }
  .element-avatar { ... }
  .element-selected { ... }
}
```

#### Prefixed properties

When using vendor prefixed properties, indent each property so that the declaration's value lines up vertically for easy multi-line editing. 

{How to do this in VSC}

```css
/* Prefixed properties */
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
          box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
```

#### Single declarations

In instances where a rule set includes only one declaration, consider removing line breaks for readability and faster editing. Any rule set with multiple declarations should be split to separate lines.

The key factor here is error detection - e.g. a CSS validator stating you have a syntax error on line 183. with a single declaration, there's no missing it. With multiple declarations, separate lines is a must for your sanity.

```css
/* Single declarations on one line */
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 200px; }

/* Multiple declarations, one per line */
.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/logo.png);
}

```

#### Shorthand notation
Strive to limit use of shorthand declarations to instances where you must explicitly set all the available values. Common overused shorthand properties include: 
- `padding`
- `margin`
- `font`
- `background`
- `border`
- `border`
- `border-radius`

At times we don't need to set all the values a shorthand property represents. For example, HTML headings only set top and bottom margins, so when necessary, only override those two values. Excessive use of shorthand properties often leads to sloppier code with unnecessary overrides and unintended side effects. 

```css
/* Bad example */
.element {
  margin: 0 0 10px;
  background: red;
  background: url("icon.png");
  border-radius: 3px 3px 0 0;
}

/* Good example */
.element {
  margin-bottom: 10px;
  background-color: red;
  background-image: url("icon.png");
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
```

#### Nesting in Sass

Avoid unnecessary nesting. Just because you can nest, doesn't mean you always should. Consider nesting only if you must scope styles to a parent and if there are multiple elements to be nested. 

```scss
// Without nesting
.table > thead > tr > th { color: #fff; }
.table > thead > tr > th { color: #fff; }

// With nesting
.table > thead > tr {
  > th { color: #fff; }
  > td { color: #fff; }
}

```

#### Operators in Sass

To improve readability, wrap all maths operations in parentheses with a single space between values, variables and operators.

```scss
// Bad example
.element {
  margin: 10px 0 @variable*2 10px;
}

// Good example
.element {
  margin: 10px 0 (@variable * 2) 10px;
}

```

#### Comments

Code is written and maintained by people. Ensure your code is descriptive, well commented and approachable by others. Great code comments convey context or purpose. Do not simply reiterate a component or class name.

Be sure to write in complete sentences for larger comments and succinct phrases in general notes.

```scss
// Use two slashes for comments in sass files

/* Use asterix and a slash for comments in css files */
```

```css
/* Bad example */
/* Modal header */
.modal-header {
  ...
}

/* Good example */
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

#### Class names

- Keep classes lowercase and use dashes (not camelCase). Dashes serve as natural breaks in related class (e.g. `.btn` and `.btn-danger`)
- Avoid excessive and arbitrary shorthand notation. `.btn` is useful for *button*, but `.s` doesn't mean anything
- Keep classes as short and succinct as possible
- Use meaningful names; use structural or purposeful names over presentational 
- Prefix classes based on the closest parent or base class 
- Use `.js-*` classes to denote behaviour (as opposed to style), but keep these classes out of your CSS

It's also useful to apply many of these same rules when creating Sass variable names.

Useful reading: [The BEM Methodology](https://en.bem.info/methodology/quick-start/)

#### Selectors

- Use classes over generic element tag for optimum rendering performance
- Avoid using several attribute selectors (e.g. `[class^="..."]`) on commonly occurring components. Browser performance is known to be impacted by these
- Keep selectors short and strive to limit the number of elements in each selector to three
- Scope classes to the closest parent only when necessary e.g. when not using prefixed classes

```css
/* Bad example */
span { color: #fff; }
.page-container #stream #stream-item .tweet .tweet-header .username { color: #fff; }
.avatar { color: #fff; }

/* Good example */
.avatar { color: #fff; }
.tweet-header .username { ... }
.tweet .avatar { ... }

```

#### Organisation

- Organise sections of code by component
- Develop a consistent white space to your advantage when separating sections or code for scanning larger documents
- When using multiple CSS/Sass files, break them down by component instead of page. Pages can be rearranged and components moved.  

```css
/* 
* Component section heading
*/

.element { color: #fff; }

/*
* Component section heading
*
* Sometimes you need to include some optional context for the entire component. Do that up here if it's important enough
*/

.element { color: #fff; }

/* Contextual sub-component or modifier */
.element-heading { color: #fff; }
```

#### Editor preferences

Set your editor to the following settings to avoid common code inconsistencies and dirty diffs:
- Use soft tabs set to two spaces
- Trim trailing white space on save
- Add new line at end of files
