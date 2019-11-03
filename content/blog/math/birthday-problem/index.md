---
title: Birthday problem
date: 2019-08-03 08:00:00 +0800
---

> You have to organise a birthday party for your younger sibling and you've been given $$48$$ toys and $$42$$ sweets.
You have to give away all the toys and sweets to the guests at the party.

So the question is, what is the highest number of guests that can be invited such that each guest gets the same amount of sweets and toys?


Divide the larger number by the small one. In this case we divide 60 by 24 to get a quotient of 2 and remainder of 12.
Next we divide the smaller number (i.e. 24) by the remainder from the last division (i.e. 12). So 24 divide by 12, we get a quotient of 2 and remainder of 0.
Since we already get a remainder of zero, the last number that we used to divide is the GCD, i.e 12.

```flowchart
st=>start: Start
e=>end: End
op1=>operation: Divide the larger number 
by the smaller number
cond=>condition: Is A or B equal to 0?

st->op1->cond
cond(yes)->e
cond(no)->op1
```

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
```

</br>

Running `gcd(48, 42)` gives us $$6$$.

