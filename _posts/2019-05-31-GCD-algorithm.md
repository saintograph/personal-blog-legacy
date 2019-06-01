---
layout: post
title:  "Finding the greatest common divisor(GCD)."
date:   2019-05-31 08:00:00 +0800
categories: [math, algorithm]
---

### Greatest common divisor and the Euclidean algorithm

If $$a$$ and $$b$$ are any two positive integers, the _greatest common divisor_ or **GCD** of $$a$$ and $$b$$ is the largest integer which is a divisor of both numbers.

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

1. If $$A = 0$$ then $$GCD(A,B)=B$$, since $$GCD(0,B)=B$$ we can stop.
2. If $$B = 0$$ then $$GCD(A,B)=A$$, since $$GCD(A,0)=A$$ we can stop.
3. Write $$A$$ in quotient remainder form $$(A = B⋅Q + R)$$
4. Find $$GCD(B,R)$$ using the Euclidean Algorithm since $$GCD(A,B) = GCD(B,R)$$

reference: [link - Khan Academy](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/the-euclidean-algorithm)

**Example:**

1. Find the **GCD** of $$(864, 291)$$.
  * $$A = 864$$, $$B = 291$$
  * check $$A \neq 0$$
  * check $$B \neq 0$$
  * $$864 \div 291 = 2$$ remainder $$282$$
  * find $$GCD(291, 282)$$ since $$GCD(864, 291) = GCD(291, 282)$$
2. Find the **GCD** of $$(291, 282)$$.
  * $$A = 291$$, $$B = 282$$
  * check $$A \neq 0$$
  * check $$B \neq 0$$
  * $$864 \div 291 = 1$$ remainder $$9$$
  * find $$GCD(282, 9)$$ since $$GCD(291, 282) = GCD(282, 9)$$
3. Find the **GCD** of $$(282, 9)$$.
  * $$A = 282$$, $$B = 9$$
  * check $$A \neq 0$$
  * check $$B \neq 0$$
  * $$282 \div 9 = 31$$ remainder $$3$$
  * find $$GCD(9, 3)$$ since $$GCD(282, 9) = GCD(9, 3)$$
4. Find the **GCD** of $$(9, 3)$$.
  * $$A = 9$$, $$B = 3$$
  * check $$A \neq 0$$
  * check $$B \neq 0$$
  * $$9 \div 3 = 3$$ remainder $$0$$
  * find $$GCD(3, 0)$$ since $$GCD(9, 3) = GCD(3, 0)$$
5. Find the **GCD** of $$(3, 0)$$.
  * $$A = 9$$, $$B = 3$$
  * check $$A \neq 0$$
  * check $$B = 0$$
  * Since $$B = 0$$, $$GCD(3, 0) = 3$$
6. Answer = $$3$$


Here's the recursive algorithm with **C++**.

```c++
#include <iostream>

int gcd(int a, int b) {
  if (a == 0 || b == 0) {
    if (b > a) {
      return b;
    }
    return a;
  }
  if (b > a) {
    int c = a;
    a = b;
    b = c;
  }
  int result = a % b;
  a = b;
  b = result;
  return gcd(a, b);
}

int main() {
  std::cout << gcd(864, 291) << std::endl;
}
```
GCD algorithm with **Javascript**.

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

GCD algorithm with **Python**.

```python
# greatest common divisor for two numbers
def gcd(a, b):
  if len(locals().keys()) > 2:
    return
  if a == 0 or b == 0 :
    if b > a:
      return b
    return a
  if b > a:
    c = as
    a = b
    b = c
  result = a % b
  a = b
  b = result
  return gcd(a, b)

print(gcd(864, 291))
```