---
title: Binet's Formula
date: 2019-07-08 08:00:00 +0800
description: Computing n in the Fibonacci Sequence
---

#### Binet's formula for calculating <span style="text-transform: lowercase">$$n$$</span> in a Fibonacci sequence

Binet's formula can be used to calculate the $$n$$th term of the Fibonacci sequence without resorting to _recursion_.

If $$F_n$$ is the $$n$$th Fibonacci number, 

$$F_n = \frac{1}{\sqrt5}((\frac{1+\sqrt5}{2})^n - (\frac{1-\sqrt5}{2})^n )$$


#### Code

```python
import math

def binetFormula(n):
  return (1 / math.sqrt(5)) * (math.pow((1 + math.sqrt(5)) / 2, n) - math.pow((1 - math.sqrt(5)) / 2, n))

print(math.floor(binetFormula(60))) # 1548008755920
```

```js
function binetFormula(n) {
  return (1 / Math.sqrt(5)) * (Math.pow(((1 + Math.sqrt(5)) / 2), n) - Math.pow(((1 - Math.sqrt(5)) / 2), n));
}

Math.round(binetFormula(60)); // 1548008755920
```
