---
title: Enjoying my time with Node.js
date: 2015-12-19
---

#### Alternatively, I found a project to properly learn it

A bit of background -- I've been using primarily PHP for any backend
that I've needed to do, which while works most certainly doesn't seem
quite right. I have nothing against PHP, however it feels a bit dirty,
almost like I'm cheating when using it. I didn't know any other way,
though, so I stuck with it.

Well I recently found a project I could use to learn Node.js -- a
Minecraft server control panel -- and I've actually been enjoying it,
much more than I have PHP. Here's a demo of my project:

https://www.youtube.com/embed/c0IGKEmHyOM?feature=oembed

It's all served (very quickly) by a Node.js backend, that wraps around
the Minecraft server and uses multiple POST and GET routes for various
functions, such as saving files. The best part about it is how fast it
is (obviously), but the second greatest thing is the efficiency. For
example, in PHP, for me to implement some new thing, I'd most likely
need to create a new file, fill in my variables and methods, and point
my JavaScript (or AJAX) towards it. And I have no real good way of
debugging it. However with Node.js, it's three lines of code (no
seriously) to implement a new route with Express that will perform a
function. Not only that, but it's *so easy to debug.* Because of how
it's run, instead of just producing a 500 error page, it can actually
log the error before shutting off the program, which is so much more
useful then then old 'cat /var/log/apache2/error.log'.

My advice to anyone looking to get into web development is *learn
Node.js.* Not only is it a new web technology that is only increasing in
size, but it's powerful, open with about a billion extensions, and can
help you learn more JavaScript, a big part of dynamic content on HTML5
websites.
