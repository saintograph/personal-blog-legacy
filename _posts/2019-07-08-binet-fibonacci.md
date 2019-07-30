---
layout: post
title:  "Binet's Formula."
date:   2019-07-08 08:00:00 +0800
categories: [math]
comments: true
---

#### Binet's formula for calculating n in a Fibonacci sequence

Binet's formula can be used to calculate the $$n$$th term of the Fibonacci sequence.

If $$F_n$$ is the $$n$$th Fibonacci number, 

$$F_n = \frac{1}{\sqrt5}((\frac{1+\sqrt5}{2})^n - (\frac{1-\sqrt5}{2})^n )$$


Implementation:

**Python:**

```python
import math

def binetFormula(n):
  return (1 / math.sqrt(5)) * (math.pow((1 + math.sqrt(5)) / 2, n) - math.pow((1 - math.sqrt(5)) / 2, n))

print(math.floor(binetFormula(60))) # 1548008755920
```

**Javascript:**

```javascript
function binetFormula(n) {
  return (1 / Math.sqrt(5)) * (Math.pow(((1 + Math.sqrt(5)) / 2), n) - Math.pow(((1 - Math.sqrt(5)) / 2), n));
}

Math.round(binetFormula(60)); // 1548008755920
```