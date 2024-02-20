---
layout: post
author: "Katherine Reid"
title:  "CSS is pretty (cool)"
date:   2023-09-02 00:27:52 -0500
categories: "340"
---
Okay, HTML isn't that fun, but CSS is _awesome_. I can take a bunch of invisible `div`s and color, expand, border, transform(!), stack, and animate them! This is probably a bit further than the intended scope for this lab assignment, but I got curious about the CSS [`transform`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) property this morning and made a little browser extension that tilts all my webpages thusly:
```css
body { transform: rotate(5deg); }
```

Which produced a hilarious effect:
![Oops, I dropped my webpage.]({{site.baseurl}}/assets/images/tilted_webpage.png)

So when I found out that 3D transformations were possible, I immediately began working on the prototypical 3D graphics demo. It's no Blender monkey head or Idaho Teapot, but I was quite proud of this cube (Which might still be hosted at [/blog/cube]({{site.baseurl}}/cube) - check there for the animated version).
![Banana peels and super mushrooms not included.]({{site.baseurl}}/assets/images/rotating_cube.png)

I had seen "pure CSS" art and demos before now, but it still astonishes me how much is possible ~~[without a real programming language](https://jsfiddle.net/Camilo/eQyBa/)~~, and it now astonishes me that it's so easy. It reminds me of doodling in the Desmos graphing calculator, except that in CSS, making aesthetically pleasing visuals is the intended use case. I'm really excited to see how it can synergize with JavaScript when we add it to our mix next week.
