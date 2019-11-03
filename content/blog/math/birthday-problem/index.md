---
title: Birthday problem
date: 2019-08-03 08:00:00 +0800
description: "Using the Greatest Common Divisor (GCD) to compute results."
---

> Organise a birthday party with **48** toys and **42** sweets.
You have to give away all the toys and sweets to the guests at the party.

What is the highest number of guests that can be invited such that each guest gets the **same amount** of **sweets and toys**?

#### Greatest Common Divisor

The Greatest Common Divisor (GCD) of two or more integers, which are not all zero, is the largest positive integer that divides each of the integers (ref. [Wikipedia](https://en.wikipedia.org/wiki/Greatest_common_divisor))

1. Divide the larger number by the small one. In this case we divide 48 by 42 to get a quotient of 1 and remainder of 6.
2. Next we divide the smaller number (i.e. 42) by the remainder from the last division (i.e. 6). So 42 divide by 6, we get a quotient of 7 and remainder of 0.
3. Since we already get a remainder of zero, the last number that we used to divide is the GCD, i.e 6.

#### Algorithm

```mermaid
graph TB
    Start(-Start-) --> id1[Divide the larger number by the smaller number]
    id1 --> id2{Is A or B equal to 0?}
    id2 -- Yes --> End(-End-)
    id2 -- No --> id1
```

#### Code

```js
const gcd = (a, b) => {
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
  
  return gcd(a, b); // recurse
}

gcd(48, 42); // 6
```

```python
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

print(gcd(48, 42)); # 6
```


