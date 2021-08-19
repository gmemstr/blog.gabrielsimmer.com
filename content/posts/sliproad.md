---
title: Sliproad
date: 2021-07-10
---

### Another case of "just do it yourself"

The want for quickly sharing files across devices and having an easy interface for uploading and downloading them is a relatively common want among people, both for those in the technology sphere or otherwise. Most may opt for services like Dropbox or Google Drive, which offer good clients for desktop and mobile, but I wanted to take it a step further and self host a solution. While options like ownCloud/Nextcloud and the like exist, I wasn't happy with the platforms for a variety of reasons (mostly with regard to their feature set being relatively large and ill-suited to my usual workflow). I also wanted to be able to bring in other file storage providers into one interface, since I store backups and whatnot on external providers (this came into play later, but we'll get to that).

Thus was born the concept of _sliproad_, originally just "pi nas" (changed for obvious reasons), was born. The initial commit was February 24th, 2019, [and really isn't much to look at](https://github.com/gmemstr/sliproad/commit/7b091438d43d77300c4be8afb64e2735dd423d71) - just reading a configuration defining a "cold" and "hot" storage location. The idea behind this stemmed from my use of two drives attached to my server at the time (a small Thinkcenter PC), one being an external hard drive and the other a much faster USB 3 SSD. For simplicity, I leveraged server-side rendered templates for file listings, and the API wasn't really of importance at this point.

![My old "server" setup](/images/old-server-setup.png)

For a long while, this sufficed. It was more or less a file explorer for a remote fileysystem with two degrees of performance. But I wanted to expand on the frontend, specifically looking for more dynamic features. I began to work on decoupling functionality into an API rather than server-side templates in March of 2019, and that evolved to the implementation of "providers". I'm not entirely sure what sparked this idea, besides beginning to use Backblaze around the time of the rewrite. Previously, I ran a simple bash script to rsync my desktop's important files to the Thinkcenter's cold storage, but understood I needed offsite backups. Offloading this to Backblaze's B2 service was an option (and very worth the price) but I sacrificed ease of use when looking through backed up files. Bringing the various file providers under one roof allowed me to keep using the same interface and gave me the option of expanding the methods of interfacing with the filesystems provided. Around this time I was looking to rebrand, and taking a queue from highways chose the name "sliproad" to signify the merging of filesystems into one "road" (or API).

Coming back around to my want for a more robust frontend - while rewriting and decoupling the frontend rendering, I originally opted to rewrite the interface using React. This was off the heels of a relatively good experience rewriting my server monitor's interface ([Platypus](#)) using it, but it was quickly abandoned as I grew frustrated with the process of running both the React development server and the sliproad server in parallel to develop them in tandem. Eventually I opted to delete it and instead moved to a much more simplified form factor, with plain HTML, CSS and JavaScript. This ended up being a great move when Go's bundling of files into executables came to the stable branch, which meant I could deploy a single executable to my Raspberry Pi or wherever I need to run the project (I regularly run it on my desktop or work laptop to quickly nab files between them, rather than uploading them to the Pi as a go between).

And this is where Sliproad is currently. I've been tweaking the internals a bit to hopefully make future "providers" easier to add (spurred on by AWS S3 support) and working on figuring out how to handle authentication in the future, but the application itself works well for my use case. It's entirely possible it will work well for someone else, but that's pretty secondary. For the time being, I'm happy keeping the repository and code base "as is" and consider the project largely finished.

_Side note: I'm intentionally omitting the brief period I tried to rewrite the application in Rust. My intention was to rewrite with speed in mind, but ultimately it wasn't something I found myself wanting to keep up, given the level of functionality of the application in the current language, Go._
