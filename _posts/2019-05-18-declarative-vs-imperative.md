---
layout: post
title:  "Declarative vs. imperative code"
date:   2019-05-18 08:00:00 +0800
categories: [javascript]
---

#### Declarative programming is a layer on top of low-level constructs, providing logical patterns to work with and readable code.

Most software stacks are a mix of both. UI layers (React/Vue/Angular) are often written with declarative code to reduce the layers of complexity often associated with writing backend logic. The complexity is 'hidden away' from the developer, which has benefits and drawbacks.

Declarative code increases developer efficiency ( i.e. speed ), which partly explains the popularity of scripting languages such as Ruby, Python and Javascript for developing server-side code when speed in bringing a product to users matter.

Imperative code is written for optimization. A lot more consideration and time goes into writing imperative code such as an algorithm which is measured against metrics such as memory and runtime complexity ( i.e. Big-O notation ).

For example, `Array.prototype.sort()` is declarative but slow when sorting larger arrays ( Chrome's implementation of `Array.sort()` is different from Firefox's). That's when the developer has to roll-up his sleeves and write imperative code, a custom sorting algorithm which performs consistently on every browser for the task at hand. ( [resource](https://khan4019.github.io/front-end-Interview-Questions/sort.html) )

Declarative and imperative programming is best associated with **complexity**.