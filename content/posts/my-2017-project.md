---
title: My 2017 Project
date: 2016-12-22
---

#### This one... this one will be fun

As some of you may know, or not know, I am a developer
at heart, writing and playing with code to my hearts content. However
there are some other areas of technology I really, *really* want to play
with. These last few months I've been toying with the idea of building
my own homelab, teaching myself the basics of enterprise and small-scale
networks (and then breaking them, of course). I've also wanted to look
into server farms and whatnot, but that seems a bit too much considering
my budget and space, among other things.

#### The Plan

First, I want to start with a really solid second hand network switch.
The primary function of this is to allow me to extend my ethernet
capabilities -- right now I'm essentially limited to one physical
ethernet jack and have to rely on WiFi for everything else. This will
allow me to have a permanent home for my Pi, laptop station, and
whatever else I add to the network. Plus I think network switches look
really cool.

Next, once I can afford it, I want to either build or buy a good
rackmount NAS, along with an actual rack to mount it on (and add the
switch to said rack). Ideally I'd want to have around 8TB of storage to
play with initially, a few 2TB drives most likely with unRaid. I'd want
a rack mount case that can support a fair few drives so later down the
line I can add more and larger disks. Specs wise, I have no clue what a
NAS would need, but I would assume nothing too high-end. If all else
fails, I'd end up buying a second hand one off eBay and going from
there. This will then connect to the switch -- whether I allow it to
communicate with the outside world I can't say for sure yet (this is
after all a rambly brainstorm kind of blog post). This NAS would be a
"hot" server, one that is frequently read from, modified, written to,
and so forth.

The second NAS box would be a highly-redundant backup system, limited to
just the internal network and comprised of many tried-and-tested drives.
This server would be upgraded and read from far less than the "hot" NAS,
but needs to make up for lack of read speed in sheer bytes of data it
can hold and keep intact even in cases like drive failure. This box
would most likely be bought second hand, depending on the situation.
Capacity I do not have concretely in my head, however I want to aim for
about 30TB of raw storage (5x6TB drives, 10x3TB drives if the server is
big enough).

The final system, the pièce de résistance if you will, is a high-end
dedicated computation-heavy server. In my head (and heart) this would be
equipped with two Intel Xeon cores, one or two GPUs (one gaming, one
dedicated to crunching numbers like a Quadro), and a couple SSDs to keep
it happy in terms of storage. This box would be the server that handles
media encoding, 3D rendering (most likely renting it out later), serving
up websites, and whatever the heck else I can get the power-hungry thing
to do. Overkill, most likely, and probably end up selling some computing
space in the form of VPSs and whatnot, but it would be a damn cool thing
to have around (my power bill would never be happy).

Anywho, time to get cracking.
