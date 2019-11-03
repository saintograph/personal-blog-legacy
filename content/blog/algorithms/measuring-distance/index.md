---
layout: post
title:  "Measuring distance on a spherical plane."
date:   2019-07-03 08:00:00 +0800
description: Measuring physical distance on a globe with the Haversine formula.
---

When you're on a stopover and have little to do - try calculating your distance to your destination.


### Haversine formula.

Central angle = $$ 2 \arcsin \sqrt{\sin^2(\frac{\gamma_2 - \gamma_1}{2}) + \cos \gamma_1 \times \cos \gamma_2 \sin^2(\frac{\lambda_2 - \lambda_1}{2})}$$

Reference:

* [https://www.intmath.com/vectors/3d-earth-geometry.php](https://www.intmath.com/vectors/3d-earth-geometry.php)

Credits: 

* [https://www.movable-type.co.uk/scripts/latlong.html](https://www.movable-type.co.uk/scripts/latlong.html).
* [https://www.w3schools.com/html/html5_geolocation.asp](https://www.w3schools.com/html/html5_geolocation.asp)


```js
Number.prototype.toRadians = function() {
  return this * Math.PI / 180;
}

const lat1 = position.coords.latitude;
const lon1 = position.coords.longitude;

// Your distance from Rome
const lat2 = 41.9028;
const lon2 = 12.4964;

const R = 6371e3;
const gamma1 = lat1.toRadians();
const gamma2 = lat2.toRadians();
const deltaGamma = (lat2 - lat1).toRadians();
const deltaLambda = (lon2 - lon1).toRadians();

const a = Math.sin(deltaGamma / 2) * Math.sin(deltaGamma / 2) + Math.cos(gamma1) * Math.cos(gamma2) * Math.sin(deltaLambda / 2) * Math.sin(deltaLambda / 2);
const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
const d = R * c;
```



```html
<!DOCTYPE html>
<html class="no-js">

<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <title></title>
  <meta name="description" content="">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="">
</head>

<body>
  <h1>Haversine</h1>
  <button onclick="getLocation()">How far am I from Rome?</button>
  <p id="demo"></p>
  <script src="./js/main.js" async defer></script>
</body>

</html>
```

```js
const x = document.getElementById("demo");

Number.prototype.toRadians = function() {
  return this * Math.PI / 180;
}

function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
  } else {
    x.innerHTML = "Geolocation is not supported by this browser.";
  }
}

function showPosition(position) {
  const lat1 = position.coords.latitude;
  const lon1 = position.coords.longitude;

  // Your distance from Rome
  const lat2 = 41.9028;
  const lon2 = 12.4964;

  const R = 6371e3;
  const gamma1 = lat1.toRadians();
  const gamma2 = lat2.toRadians();
  const deltaGamma = (lat2 - lat1).toRadians();
  const deltaLambda = (lon2 - lon1).toRadians();

  const a = Math.sin(deltaGamma / 2) * Math.sin(deltaGamma / 2) + Math.cos(gamma1) * Math.cos(gamma2) * Math.sin(deltaLambda / 2) * Math.sin(deltaLambda / 2);
  const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
  const d = R * c;

  x.innerHTML = `Latitude:  ${position.coords.latitude} <br>Longitude: ${position.coords.longitude}<br> Distance is: ${Math.round(d / 1000)} km.`;
}
```