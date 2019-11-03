---
title:  "Converting RGB to hexadecimal values."
date:   2019-03-03 08:00:00 +0800
description: Converting RGB to hex values
---


Hexadecimal numbers are numbers in base 16 ($$ x_{16} $$ where x is an integer).

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

#### Code

```js
const rgbToHex = (val) => {
  if (val >= 255) {
    return 'FF';
  }

  if (val <= 0) {
    return '00';
  }

  let hex = Number(val).toString(16);

  if (hex.length < 2) {
    hex = "0" + hex;
  }

  return hex;
};

const rgb = (r, g, b) => {
  return `${rgbToHex(r)}${rgbToHex(g)}${rgbToHex(b)}`.toUpperCase();
};
```