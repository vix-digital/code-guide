---
title:  "CSS Linting"
categories: css
---

#### Sass Linting Setup
 
A Sass linter that keeps all of our .scss files neat and tidy.

Based on this article - [Making lint great again!](https://medium.com/@okonetchnikov/make-linting-great-again-f3890e1ad6b8)

#### Background Reading
The package.json relies on these dependencies, you can read more about them in the links below
- [pre-commit](https://www.npmjs.com/package/pre-commit)
- [lint-staged](https://github.com/okonet/lint-staged)
- [stlyelint](https://github.com/okonet/lint-staged)

#### Method
**Step 1** 

Add this code snippet to your `package.json` file in your project repository.

If your project doesn't have a `package.json` file you will need to create one.

When adding the linter to a monolithic repository make sure you add this file to the base folder.

```

{
  "name": "lint",
  "version": "0.1.0",
  "scripts": {
    "lint-staged": "lint-staged"
  },
  "lint-staged": {
    "*.scss": "stylelint --syntax scss"
  },
  "pre-commit": "lint-staged",
  "devDependencies": {
    "pre-commit": "~1.2.2",
    "lint-staged": "~3.4.0",
    "stylelint": "~7.10.1"
  }

```

**Step 2** 

In your repository, create a new file called `.stylelintrc` file, this is where you will configure your lint settings.

When adding the linter to a monolithic repo make sure you add this 
file to the base folder.

A list of all available settings can be found [here](https://stylelint.io/user-guide/rules/)

Once configured the file should start to look a bit like this.. 

```
{
  "rules": {
    "at-rule-empty-line-before": "always",
    "at-rule-name-case": "lower",
    "at-rule-semicolon-space-before": "never",
    "block-closing-brace-empty-line-before": "never",
    "block-closing-brace-newline-after": "always",
    "block-closing-brace-newline-before": "always-multi-line",
    "block-closing-brace-space-before": "always-single-line",
    "block-no-empty": true
  }
}
```

We store our settings file as a [snippet](https://gitlab.com/vix/deepvix/snippets/1660626) in a GitLab Repository, making it easy to keep up to date and accessible to the whole team.

**Step 3**

Run `npm install`

This will install all the dependencies, listed above in the "Ingredients" section, to your git repo in a folder called `node_modules`

We don't want to commit the `node_modules` to our repository when we push a change, so make sure that you add it to the `.gitignore` file

```
## Ignore Node Modules
node_modules
```

#### Result
When you make a change to a `.scss` file it will be checked for errors before you can commit the change. 

If everything is setup correctly and you have written lovely neat code you will see something like this when you commit a change:

![sass_success]({{ site.url }}/assets/images/sass_success.png)

If the sass formatting isn't quite right you will something like this when you try to commit the change:

![sass_mistake]({{ site.url }}/assets/images/sass_mistake.png)
