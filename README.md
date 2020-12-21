# SNUG — `S`uper `N`eat `U`tility `G`enerator
SCSS toolkit to create utility classes with ease.


## Requirements
For now you need to use [dart sass](https://sass-lang.com/dart-sass) to compile your styles.


## Installation
```bash
npm install @snug/core
```


## Basic Usage
```scss
@use 'snug' with (
  $breakpoints: (
    's': 640px,
    'm': 768px,
    'l': 1024px,
  )
);

// Basic responsive variants
.banana {
  @include snug.variants('responsive') {
    color: gold;
  }
}

// Adding additional variants
.banana {
  @include snug.variants('responsive' 'hover' 'group-hover') {
    color: gold;
  }
}
```


## Advanced Usage
When using modifiers that change the same or a more specific css property these should be grouped by breakpoint.
A more specific property would be something like `padding-top` to `padding`.

```scss
// Wrap your code like this to have your modifiers grouped by breakpoint
@include snug.variants('responsive') using ($props...) {
  .p-1 {
    @include snug.variants($props...) {
      padding: 0.25rem;
    }
  }

  .pt-1 {
    @include snug.variants($props...) {
      padding-top: 0.25rem;
    }
  }
}
```
