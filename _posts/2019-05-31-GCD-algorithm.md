---
layout: post
title:  "Finding the greatest common divisor(GCD)."
date:   2019-05-31 08:00:00 +0800
categories: [math, algorithm]
---

### Greatest common divisor and the Euclidean algorithm

If _a_ and _b_ are any two positive integers, the _greatest common divisor_ or **GCD** of _a_ and _b_ is the largest integer which is a divisor of both numbers.

Two numbers with greatest common divisor of 1 are called _coprime_ or _relatively prime_.

i.e.
```javascript
function checkCoPrime(a, b) {
  if (gcd(a,b) === 1) {
    return 'coprime';
  }
}
```

The steps of for finding the _greatest common divisor_ with the Euclidean Algorithm is as follows:

1. If A = 0 then GCD(A,B)=B, since the GCD(0,B)=B, and we can stop.
2. If B = 0 then GCD(A,B)=A, since the GCD(A,0)=A, and we can stop.
3. Write A in quotient remainder form (A = B⋅Q + R)
4. Find GCD(B,R) using the Euclidean Algorithm since GCD(A,B) = GCD(B,R)

reference: [link - Khan Academy](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/the-euclidean-algorithm)

Here's the recursive algorithm with **Javascript**.

```javascript
// greatest common divisor for two numbers
function gcd(a, b) {
  if (arguments.length > 2) {
    return;
  }
  if (a === 0 || b === 0) {
    if (b > a) {
      return b;
    }
    return a;
  }
  if (b > a) {
    const c = a;
    a = b;
    b = c;
  }
  const result = a % b;
  a = b;
  b = result;
  return gcd(a, b);
}

gcd(864, 291); // 3
```