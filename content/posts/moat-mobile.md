---
title: Moat Mobile
date: 2015-11-11
---

## Or "The evolution of my web skills"

![](https://cdn-images-1.medium.com/max/1200/1*mJn71fHwI6K3pfZlY5MN8Q.png)

Moat, for the uninitiated (so, most of you), is my original project to
learn how to use APIs. The API I chose was for [Voat.co](http://voat.co), a reddit competit- sorry, news aggregator that looks an awful lot like another
website.

It started off pretty rough -- in fact, you can go preview it [here (dead link)](http://gabrielsimmer.com/moat/)

![Using pretty much just pure PHP](https://cdn-images-1.medium.com/max/800/1*0kycKbtMpPuQPSduytG2gg.png)

It... worked, but the UI wasn't really where I wanted it. I was also
using the Voat alpha API, which was really slow. I looked ahead, and
started working on a version that utilized JavaScript and AJAX, so I
could display some sort of loading animation. I also used Bootstrap for
it, so that I could scale it better on mobile.

![Looks nicer. But functions about the same.](https://cdn-images-1.medium.com/max/800/1*r8Z-FLErTE4ldh9F8EZ-_g.png)

The logical next step was to upgrade the interface, since so far it has
been terrible. Again, I wanted to use Bootstrap, and I wanted to make it
as mobile friendly as possible. And what's the best way of doing that?
By using a [material design bootstrap
theme](http://fezvrasta.github.io/bootstrap-material-design/). I also used [Material Floating Buttons](http://nobitagit.github.io/material-floating-button/)to give it navigation that made sense. I also made JavaScript do all the formatting work, using the .get() function in jQuery, and using my own server as an API middleman because of AJAX's lack of trust when getting info from other sites (for understandable reasons, but [here is how you can bypass it](https://ghostbin.com/paste/kf3pf)). And here is the final product.

![Not too bad.](https://cdn-images-1.medium.com/max/800/1*dPZW7uPaJRClAs-SRhtbPg.png)

The FAB requires a bit of tweaking, and I have a bit of functionality to
add, but this is the product so far. I doubt I'll touch the styling for
quite a while, unless it's to make the UI more material design like.

You can fork the project on the [GitHub
page](https://github.com/gmemstr/moat-mobile) if you so please, and be sure to read the FAQ if you want to know what you can help out with.
