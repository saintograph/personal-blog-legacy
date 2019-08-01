---
layout: post
title:  "let, const and var"
date:   2019-07-30 08:00:00 +0800
categories: [javascript]
---

#### When should `let`, `const` and `var` be used?

The ES2015 ( and later ) spec is used when writing Javascript for the production environment. In almost all cases, we declare intent ( i.e. should the variable be reassigned within the scope of a function? ) with `let` and `const`.

`let` and `const` are block-scoped and not available outside the scope, compared to `var`.

Global variables are generally 'frowned-upon'. It's classified as bad practice because in a large code-base with thousand of lines, similarly named variables can be difficult to find _and_ debug.

Use `const` wherever possible, as we try to be explicit with our code and intent.

Here's an example:

```javascript
// add() and multiply() are global functions

function add(a, b) {
  return a + b;
}

function multiply(a, b) {
  return a * b;
}

// Style A - the most verbose
let foo = 0; 
const bar = add(1, 2); // 3
foo = multiply(bar, 2); // 6

// Style B - much simpler, but still not explicit
const bar = add(1, 2); // 3
const foo = multiply(bar, 2); // 6

// Style C - simple and explicit. Declare foo and immediately assign a value with an IIFE
const foo = (function() {
  return multiply(add(1, 2), 2);
})(); // 6

// Style C - ES2015
const foo = (() => multiply(add(1, 2), 2))(); // 6
```


**Caveat**: The `var` keyword is still valid, `let` shouldn't be construed as an invitation to sprinkle variables all over a file's scope and `const` doesn't mean a variable is immutable, unlike C++ along with a hundred other peculiarities.


### Garbage collecting

One other thing to note is Javascript's **garbage collection** feature. Global variables sit in memory ( i.e. RAM ) indefinitely and use up resources.

Scoped variables are 'garbage-collected', which means if a variable is scoped within a terminated function it is removed from memory. This feature isn't obvious on modern systems with oodles of RAM, but can cause hiccups if there's a memory leak or a improperly written Raspberry Pi iOT setup ( e.g. [Johnny-Five](http://johnny-five.io) )

Read about it [here](https://javascript.info/garbage-collection).