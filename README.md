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

## Additional Topics

**1. Advanced Functions**

Function in Sass can be quite powerful and extend beyond simple arithmetic. Cover how to create more complex functions and use built-in functions.

```scss
@function calculate-grid-width($columns, $gutter-width) {
  @return ($columns * 100% / 12) - ($gutter-width * (12 - 1) / 12);
}

.grid-item {
  width: calculate-grid-width(4, 20px);
}
```

## 2. Color Functions

Sass provides several built-in functions to manipulate colors. These include functions for adjusting lightness, saturation, and more.

```scss
$base-color: #036;

.button {
  background-color: lighten($base-color, 20%);
  border-color: darken($base-color, 20%);
}
```

## 3. Control Directive & Expressions

Use control directives like `@if`, `@for`, `@each`, and `@while` to add logic to your stylesheets.

```scss
@for $i from 1 through 3 {
  .col-#{$i} {
    width: 100% / 3 * $i;
  }
}

$themes: (light, dark, colorful);

@each @theme in @themes {
  .theme-#{$theme} {
    @if $theme == light {
      background: white;
    } @else if @theme == dark {
      background: black;
    } @else {
      background: blue;
    }
  }
}
```

## 4. @error, @warm, and @debug Directives

These directives are useful for debugging and validating your Sass code.

```scss
@mixin validate-color($color) {
  @if not (type-of($color) == 'color') {
    @error "#{$color) is not a valid color value.";
  }
}

@include validate-color(#333); // Valid
@include validate-color("333"); // Error
```

## 5. Placeholder Selectors

Placeholder selectors(denoted by `%`) are used for inheritance but do not output CSS directly unless extended.

```scss
%buttn-styles {
  padding: 10px 20px;
  border-radius: 5px;
}

.button {
  @extend %button-styles;
  background-color: blue;
  color: white;
}

.alert {
  @extend %button-styles;
  background-color: red;
  color: white;
}
```

## 6. @use and @forward Rules

The `@use` rule is a newer way to include Sass files and is more powerful `@import`. It helps avoid issues with global scope.

- @use:

```scss
// _buttons.scss
$button-padding: 10px;
@mixin button {
  padding: $button-padding;
}

// main.scss
@use 'buttons';

.btn {
  @include buttons.button;
}
```

- @forward:

```scss
// _colors.scss
$primary-color: #333;
$secondary-color: #555;

@forward *;

// _index.scss
@use 'colors';

body {
  color: colors.$primary-color;
}
```
