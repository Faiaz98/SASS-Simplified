# SASS-Simplified

Sass is a preprocessor scripting language that is interpreted or compiled into CSS.

## 1. Introduction to SASS

**What is SASS?**

Sass is a preprocessor scripting language that is interpreted or compiled into CSS. SassScript is the scripting language itself. Sass helps make writing CSS easier and more efficient.

**Why Use Sass?**

- Variable: Store values you want to reuse throughout your stylesheet.
- Nesting: Nest CSS selectors in a way that follows the same visual hierarchy of your HTML.
- Partials and Import: Split your CSS into smaller, reusable pieces.
- Mixins: Create reusable chunks of code.
- Inheritance: Share a set of CSS properties from one selector to another.
- Operators: Perform calculations to set CSS property values.


## 2. Setting Up Sass

**Installation**

- Via Node.js and npm:

```bash
npm install -g sass
```
- Via Ruby and gem:

```bash
gem install sass
```

## 3. Basic Concepts

**Variables**

Variables in Sass start with a dollar sign(`$`). They allow you to store information that you reuse throughout your stylesheets.

```scss
$primary-color: #333;
$font-stack: Helvetica, sans-serif;

body {
  color: $primary-color;
  font-family: $font-stack;
```

