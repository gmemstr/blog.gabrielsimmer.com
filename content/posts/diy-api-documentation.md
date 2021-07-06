---
title: DIY API Documentation
date: 2016-02-24
---

#### How difficult can writing my own API doc pages be?

I needed a good documentation solution for
[NodeMC](https://nodemc.space)'s
RESTful API. But alas, I could find no solutions that really met my
particular need. Most API documentation services I could find were
either aimed more towards web APIs, like Facebook's or the various API's
from Microsoft, very, very slow, or just far too expensive for what I
wanted to do (I'm looking at you,
[readme.io](http://readme.io)). So,
as I usually do, I decided to tackle this issue myself.

![The current docs!](https://cdn-images-1.medium.com/max/800/1*-ojv-n3P9P3Tn_49VO0Iug.png)

I knew I wanted to use Markdown for writing the docs, so the first step
was to find a Markdown-to-HTML converter that I could easily automate
for a smoother workflow. After a bit of research, I came along
[Pandoc](http://pandoc.org/), a
converter that does pretty much everything I need, including adding in
CSS resources to the exported file. Excellent. There is also quite a few
integrations for several Markdown (or text) editors, but none for vsCode
so I didn't need to worry about those, choosing instead to use the \*nix
watch command to run my 'makefile' every second to build to HTML.

The next decision I had to make was what to use for CSS. I was very
tempted to use Bootstrap, which I have always used for pretty much all
of my projects that I needed a grid system for. However, instead, I
decided on the much more lightweight
[Skeleton](http://getskeleton.com/)
framework, which does pretty much everything I need to in a much smaller
package. Admittedly it's not as feature-packed as Bootstrap, but it does
the job for something that is designed to be mostly text for developers
who want to get around quickly. Plus, it's not too bad looking.

So the final piece of the puzzle was "how can I present the information
attractively?", which took a little bit more time to figure out. I
wanted to do something like what most traditional companies will do,
with a sidebar table of contents, headers, etc. The easiest way to do
this was a bit of custom HTML and a handy bit of Pandoc parameters, and
off to the races.

Now at this point you're probably wondering why I'm not just using
Jekyll, and the answer to that is... well, I just didn't. Honestly I
wanted to try to roll my own Jekyll-esque tool, which while slightly
less efficient still gets the job done.

So where can you see these docs in action? Well, you can view the
finished result over at
[docs.nodemc.space](http://docs.nodemc.space), and the source code for the docs (where you can make
suggestions as pull requests) is available on [my
GitHub](https://github.com/gmemstr/NodeMC-Docs), which I hope can be used by other people to build
their own cool docs.
