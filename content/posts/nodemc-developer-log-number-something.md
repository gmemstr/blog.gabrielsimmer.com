---
title: NodeMC Developer Log Number Something
date: 2016-02-10
---

#### A more developery post

NodeMC has changed a lot from what I envisioned in the
beginning. When I first began development, nearly three months ago now
(and about 52 git commits), I had envisioned a single product,
everything packaged into one executable and probably wouldn't be used by
anyone but me and one or two of my friends. However, I quickly found
myself leaning towards something very... different.

It started when I started looking for ways to package NodeMC. My plan
was to develop a full dashboard then open the source up and provide a
few binaries. I had a silly idea it would be a quick project. I started
in December, my first git commit dated the 17th (although I think I
started on the 16th). I thought about it as a complete thing, dashboard
and whatnot all packed into one executable. The first thing that moved
my direction to the one I'm going in now was the fact that I could not
figure out how to package other files into my executable made with
[EncloseJS](http://enclosejs.com/). I
made the decision to instead allow people to make their own dashboards
and apps around the application.

![Three months of git commits on NodeMC](https://cdn-images-1.medium.com/max/800/1*v3jOiqGff74xqOOa6UQslg.png)

When looking for investors, it came down to the Minecraft hosts I'd used
before and knew they used the old Multicraft dashboard. I have nothing
against Multicraft -- I think it's a pretty good dashboard, and the
recent UI refresh makes it look much better. However I knew for a fact
several hosts didn't upgrade, so I asked them first. I wanted to sell
NodeMC to a host and develop it for them exclusively. My first target
was ImChimp, whose owner [Alex](https://twitter.com/AlexHH25)
has given me support in the past (and helped run the infamous
server-that-shall-not-be-named). Unfortunately, he wasn't interested,
and who can blame him, because at the time I had a very rudimentary
demo.

https://www.youtube.com/watch?v=25ZVtFHwiCE

I did a bit more work and eventually was able to show off a much more
refined version to James from [GGServers](https://ggservers.net).
He was interested, and invested some money into the project to pay for a
VPS to use for testing and hosting the [nodemc.space](https://nodemc.space)
website, and a domain that was on sale (and would lead to my decision
for major release names). I can confidently say that without his
investment NodeMC would have probably been left as abandonware on
GitHub.

Also thanks to James, I was given a list of things that are essential
for Minecraft server dashboards, especially if you want to have
multi-server hosts using it. This included custom jar files, file
manipulation, logins with authentication, and more. Taking this list, I
worked hard to implement the features I needed. Below is the playlist
for all my dev logs.

https://www.youtube.com/watch?v=V-K8A6zQam0

It's been an interesting few months. I've learned many things about
developing things in Node.js, from methods to the limits of the
JavaScript language.

Since the beginning of this month, I've been making a huge effort to
make MultiNodeMC work, building it out with logins, setup pages, server
management, and everything else a server host admin needs. A very
interested aspect that I've never given much thought is login and
authentication, storing passwords, and keeping it all *secure*. A huge
shoutout to [Oliver](https://www.oliverdunk.com/) for giving pointers on how to cut down on security
vulnerabilities. He encouraged me to implement the API key feature for
NodeMC to prevent unauthorized access of files.

Recently, and what made me rethink my methods of distributing the
binaries, was my EncloseJS license key recently ran out. I have been
looking at [nexe](https://github.com/jaredallard/nexe) as an alternative, which while it works (and seems to
be slightly better at binary compression) isn't great because when I
deployed it onto the VPS, it produced an error saying that glibc wasn't
the correct version. This made me pause and wonder what on Earth I'm
getting into. To clarify, with EncloseJS, you literally just need to
send out the binary (and any files not packed into it), not worrying too
much about dependencies because there are pretty much... none. That
said, I believe nexe may be the way forward for me, and I'll be working
on compiling it for all the distributions that I need to.

A question I've been asked quite a bit is **will you open-source this**?
The answer is... no, not yet. I'll be opening up CORE (the basic
application) around the time version 1.4.0 of NodeMC is released. I have
no plans on open-sourcing MultiNodeMC at this time, however if I ever
abandon the project I promise to release the full sourcecode to the
public.
