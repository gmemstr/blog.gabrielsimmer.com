---
title: HoverZoom.js
date: 2015-11-05
---

#### A quick script

I'm working on a new, super secret project, and as such I'm going to
post bits and pieces of code that are generic enough but could be
useful.

This particular one will zoom in when you hover over an image, and only
requires jQuery to work. Enjoy!

```javascript
/*
HoverZoom.js by Gabriel Simmer

Provides zoom-in on hover over element,
requires jQuery :)

Obviously you can change "img" to whatever
you'd like, e.g ".image" or "#image"
*/
var imgHeight=720;
var imgWidth=1280; // Naturally you should replace these with your own values

$( document ).on({
  mouseenter:function() {
  $("img").animate({
    "height": imgHeight,
    "width": imgWidth
  });
},
  mouseleave:function(){
    $("img").animate({
      "height": "100%",
      "width": "100%"
    })
}}, "img");

```

Of course, be sure to include the following at the bottom of your *body*
element:

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js></script>
<! -- HoverZoom JS -->
<script src="js/hoverzoom.js"></script>
```