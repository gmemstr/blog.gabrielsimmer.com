---
title: Porting Websites to Jekyll
date: 2016-01-07
---

#### Why on Earth use SSI...

Jekyll, to the uninitiated, is a static site generator for websites. Instead of using PHP include statements or SSI, it generates all the pages into plain-jane HTML. It uses a fairly straightforward file structure, making most projects very clean and nice to work with. I've personally used it for the [NodeMC](http://nodemc.space) website and the new [floorchan.org](https://floorchan.org) site, and have absolutely loved it. So how can you convert your website to use Jekyll?

I'll be using Strata from HTML5Up.net ([link](http://html5up.net/strata))
to build a very simple and quick static page blog. This shouldn't take
long. (I'm also assuming you have Jekyll installed, if not here's a
[quick start guide](https://jekyllrb.com/docs/quickstart/).

First, extract the files from the zip. We'll need to create a few files
for Jekyll to work. We need the following:

```
_includes/
_layouts/
_config.yml
```

Inside the \_config.yml file, we'll need a few things just to make sure
Jekyll understands us, and maybe for future use. A simple setup would
look like this:

```yaml
name: Strata
description: A template ported to Jekyll
```

Let's now focus on the \_layouts/ directory. In here is where your
templates will go for dictating how a page will look. You'll need to
take your header and any static components you want to share across all
pages and place them in here, like navbars, footers, etc. Where you want
the content to go, you add {{content}}, which will pull the content from
the file and place it there on the generated page. It is recommended you
name this 'default.html' for easier referencing to it. Now you can go
into your index.html in the root of your project and put in your
content. You need to declare a title (more on this in a second) and a
layout to use. Enclose the lines between three dashes. Here's an
example.

```markdown
---
title: Strata
layout: default
---

    lorem ipsum

```

And voila! You have ported your website over to Jekyll. You can run
'jekyll serve' to run a server on port :4000 to preview your website,
and 'jekyll build' to build the website to a static format to a \_site/
directory.
:::

![It works!](https://cdn-images-1.medium.com/max/1200/1*WHbyFDZGHl_6eYlJc436Uw.png)

There is of course quite a bit more you can do with Jekyll, like
creating blogs and such, but maybe I'll cover that later -- or maybe
not at all, because it seems pretty well documented online.

The advantage of using Jekyll should be fairly obvious -- because it
generates HTML pages, it requires less processing overhead than PHP or
SSI. It also means that there are no entry points for SQL injections or
any of those nasty things. And one of the biggest advantages in my mind
is the layout system, so you can quickly change something across all
pages.

\~gabriel
