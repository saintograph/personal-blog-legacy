---
layout: post
title:  "Shorter syntax for await"
date:   2019-08-01 08:00:00 +0800
categories: [javascript]
---


Credits: [link](https://www.linkedin.com/feed/update/urn:li:activity:6558758287632883712), Sifat Haque on LinkedIn

```javascript
// usual
const jsonData = fetch('url')
                  .then(res => res.json())
                  .then(json => console.log(json))
                  .catch(error => console.error(error));

// await
const jsonData = await fetch('url').then(res => res.json());

// simple syntax
const jsonData = await (await fetch('url')).json();
```