---
title: Where NodeMC is headed.
date: 2016-06-02
---

#### aka the "SE Daily Follow-up Post"

I talked about where I wanted to take NodeMC on the
Software Engineering Daily podcast last month. I also discussed a few
things about the future of Minecraft, it becoming less of a game and
more of a tool, and how NodeMC will help fulfil a need for quick and
easy-to-deploy Minecraft servers.

Before we get into the future, let's talk about what's happening for
NodeMC v6 (6.0.0). First and foremost, we've rewritten pretty much every
aspect of NodeMC using the ES6 specifications, transforming the
monolithic single-file-of-code into an agile and easy to scale platform
of microservices. Not only does it mean I have to learn ES6, it also
means it's much easier to add new features and API routes. We're adding
an auto-updater (which you will be able to turn on or off hopefully),
switching to using semver for versioning, and overhauling the plugin
system with permissions and a better API to interface with the core.

We're also changing several of the routes to make more sense. Every
route that has been implemented in version 5.0.0 or below is labelled
'/v1/'. New routes introduced in v6.0.0 are '/v2/'. Routes that
interface with the server are directed to '/server/', and so forth. Each
of these routes are generated with Express and some fancy magic (Jared
goes into it a bit more
[here](https://medium.com/@jaredallard/why-i-moved-from-monolithic-backends-to-microservices-d9955b9464b2#.bexdzdpzw)) so that we can keep all the code clean.

So, back to the main topic of this post.

#### Where is NodeMC going?

The direction NodeMC is headed is being a software-as-a-service. I want
to accommodate for the rapid change in direction of Minecraft, it
becoming less of a game and more of a platform for creative works. We've
seen it used as more than just a game before, with things like [the UN
using Minecraft to re-develop neighbourhoods](http://www.polygon.com/2014/4/22/5641044/minecraft-block-by-block-united-nations-project) or it being [used for
teaching](http://education.minecraft.net/minecraftedu/), and it makes me feel we're heading more in the
direction of this sandbox game becoming a tool for both creative,
educational and professional work.

NodeMC as a SaaS basically means this: Companies who want to quickly
deploy and manage Minecraft servers will be able to quickly spin up
Minecraft servers either through a user interface or their own UI. A
typical example of this may be something like so.

Company A wants to design a new housing complex really quickly to show
to some clients, and they feel Minecraft is the best way of doing that.
They would visit the NodeMC website and hit the "New Server" button,
picking the flat world preset with one or two plugins like WorldEdit.
Once the designers are done their job, they run a command to zip the
world file, save the zip to the cloud, and shut off the server. Company
A can then spin up "viewing servers" that allow clients to log in and
explore the project freely. Everything is stored in the cloud, and if
Company A wants they can download the zip file or run the world through
a processor first to export it to a 3D design program.

> TL;DR: Starts server for building at click of a button \> Builds
> mockup \> Saves world to the cloud \> Viewing server deployed for
> clients automatically.

Obviously this is not a small task, and required a *ton* more work on
NodeMC. Right now v6 is focused on the ES6 rewrite, dashboard written in
React, and the plugin system. I'm already drawing up v7 plans, which are
going to help drive NodeMC in the direction I want to take it. And who
knows, maybe this will go other unexpected directions.
