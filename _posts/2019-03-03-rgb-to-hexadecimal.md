---
layout: post
title:  "Converting RGB to hexadecimal values."
date:   2019-03-03 08:00:00 +0800
categories: [math, javascript]
---


Hexadecimal numbers are numbers with base 16, $$ x_{16} $$ where x is an integer

|Decimal|Hex|
|---|---|
|1|1|
|2|2|
|3|3|
|4|4|
|5|5|
|6|6|
|7|7|
|8|8|
|9|9|
|10|**A**|
|11|**B**|
|12|**C**|
|13|**D**|
|14|**E**|
|15|**F**|

#### Hexadecimal values refresher

```javascript
const rgbToHex = (rgb) => {
  if(rgb >= 255) {
    return 'FF'
  }
  if(rgb <= 0) {
    return '00'
  }
  let hex = Number(rgb).toString(16);
  if (hex.length < 2) {
    hex = "0" + hex;
  }
  return hex;
};

const rgb = (r, g, b) =>{
  const red = rgbToHex(r);
  const green = rgbToHex(g);
  const blue = rgbToHex(b);
  return `${red}${green}${blue}`.toUpperCase();
}
```