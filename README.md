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

**Nesting**

Sass allows you to nest your CSS selectors in a way that follows the same visual hierarchy of your HTML.

```scss
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { 
    display: inline-block; 
  }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}  
```

**Partials and Imports**

You can create partial Sass files that contain little snippets of CSS. These partials are then imported into a main stylesheet.

- Create a partial:

```scss
// _colors.scss
$primary-color: #333;
$secondary-color: #555;
```

- Import the partial:

```scss
// main.scss
@import 'colors';

body {
  color: $primary-color;
}
```


**Mixins**

Mixins allow you to create reusable chunks of code.

```scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
    -moz-border-radius: $radius;
     -ms-border-radius: $radius;
         border-radius: $radius;
}

.box {
  @include border-radius(10px);
}
```

**Inheritance**

Inheritance in Sass allows you to share a set of CSS properties from one selector to another.

```scss
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #3333;
}

.message {
  @extend %message-shared;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}
```

**Operators**

Sass has a handful of standard math operators like +, -, *, and / for doing math.

```scss
.container {
  width: 100% / 3;
}

.sidebar {
  width: 300px - 50px;
}
```

## 4. Advanced Concepts

**Functions**

Sass functions allow you to define complex operations you can use throughout your stylesheets.

```scss
@function prx-to-rem($px, $base-font-size: 16) {
  @return $px / $base-font-size * 1rem;
}

body {
  font-size: px-to-rem(16);
}
```
