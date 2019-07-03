---
layout: post
title:  "Writing code for navigational software."
date:   2019-07-03 08:00:00 +0800
categories: [c++]
---

When you're on a long-haul flight and have little to do - try calculating the distance the plane has to fly to get you to your destination.


### Haversine formula.

Central angle = $$ 2 \arcsin \sqrt{\sin^2(\frac{\gamma_2 - \gamma_1}{2}) + \cos \gamma_1 \times \cos \gamma_2 \sin^2(\frac{\lambda_2 - \lambda_1}{2})}$$