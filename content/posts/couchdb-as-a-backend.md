---
title: Using CouchDB as a Website Backend
date: 2016-01-07
---

**She's a Coucher!**

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/m1eooqIyjbM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Not too long ago, I was shown [CouchDB](https://couchdb.apache.org/), a wonderous database promising to let me relax. It was presented
as a database that would be able to effectively act as a standalone app backend, without any need for a custom backend for simple applications.
At the time, I didn't think I had any use for a document store (or "NoSQL database"), nor did I want to remove any of my existing custom
backends - I spent so long writing them! Deploying them! But then, as I started to think about what would need to go into adding a new
type of commission my girlfriend wanted to accept to her website, including uploading files, managing the schema etc. I realised that actually,
her website is pretty well served by a document database.

Allow me to justify; the content [on their website](https://artbybecki.com) is completely standalone - there's no need for relations, and I want
to allow flexibility to add whatever content or commission types that she wants without me needing to update a bunch of Go code and deploy it
(as much as I may love Fly.io at the moment), while also performing any migrations to the PostgreSQL database. 
So with that in mind, I started to write a proof of concept, moving the database of the existing
Go backend to use CouchDB instead. This was surprisingly easy - CouchDB communicates over HTTP, returning JSON, so I just needed to use the stdlib
HTTP client Go provides. But I found that the more I wrote, the more I was just layering a thin proxy over CouchDB that didn't need to exist!
Granted, this thin proxy did do several nice things, like conveniently shortcutting views, or providing a simple token-based authentication for
editing entries. But at the end of the day, I was just passing CouchDB JSON directly through the API, and realised I could probably scrap it
all together. Not only is it one less API to maintain and update, but I get to play around with a new concept - directly querying and modifying
a database from the frontend of the website! Something typically labelled as unwanted, but given CouchDB's method of communication I was willing
to give it a shot.

Thus, I `rm -rf backend/`'d and got to work, getting a handle of how CouchDB works. The transition was really easy - the data I wanted was still
being returned in a format I could easily handle, and after writing some simple views I got a prototype put together.


_views are just JS!_
![Screenshot of Fauxton interface showing view code snippet](https://i.imgur.com/JaZr8qU.png)


(this does still mean there's a bit of manual legwork I have to do when she wants to add a new type, but I'd have to tweak the frontend anyways)

The tricky part came when it was time to move the admin interface to use the CouchDB API. I wanted to use CouchDB's native auth, of course, and
ideally the cookies that it provides on one of its authentication endpoints. The best I could come up with, for the moment, is storing the username
and password as a base64 encoded string and sending it along as basic HTTP authentication, for the time being. These are only stored in-memory, so while
I do feel a shred of guilt storing the username and password in essentially plaintext, it's at least difficult to get to - and the application is only
used by me and my partner, so the radius is relatively small.

One minor note, on this topic, on permissions. CouchDB doesn't have a granular permission system, and is sort of an all-or-nothing thing - either your
database is open for everyone to read and write, or just one group/user. Thankfully, you can use a design document with a validation function to restrict
the modification of the database to users or groups, but it's a little annoying that it's not technically native, but it does seem to be working just fine
so until something breaks it seems like the best approach.

There was also the question of where to store images - the custom API I wrote uploaded
images to Backblaze B2, which is proxied through Cloudflare and processed with Cloudinary's free offering for optimising images. Thankfully, the answer
is "just shove it into CouchDB!". CouchDB natively understands attachments for documents, so I don't have to do any funky base64 encoding into the
document itself. It's hooked up to Cloudinary as a data source, so images are cached and processed on their CDN - the B2/Cloudflare approach was
okay, if a little slow, but using CouchDB for this was _really_ slow, so this caching is pretty much mandatory. Also on the caching front, I opted
to put an AWS Cloudfront distribution in front of the database itself to cache the view data. While this slows down updates, it also lessens the
load on the database (currently running on a small Hetzner VPS) and speeds up fetching the data.

_side note: Given CouchDB's replication features, and my want to have a mostly globally distributed CDN for the data, I'm considering looking into
using CouchDB on Fly.io and replicating the database(s) between regions! Follow me on [Twitter](https://twitter.com/gmem_) or [Mastodon](https://tech.lgbt/@arch)
for updates._

Migration from the previous API and the development environment was a breeze as well - I wrote a simple Python script that just pulls the API
and inserts the objects in the response into their own documents, then uploading the images associated with the object to the database itself.
The entire process is pretty quick, and only has to be done once more when I finally merge the frontend changes point to the database's API.

Using a database directly as an API for a CRUD interface is a very odd feeling, and even more odd exposing it directly to end users of a website.
But all things considered, it works really well and I'm excited to keep exploring what CouchDB can offer. I don't know if I have enough of an
understanding of the database to recommend it as a backend replacement for simple applications, but I _do_ recommend considering it for simple
APIs, and shipping with a web GUI for management (Fauxton)is incredibly helpful for experimenting. My stance on "SQL all the things!" has shifted 
substantially and I recognise that 1) traditional SQL databases are actually a _really_ clunky way of handling webapp data and 2) it's fine to not 
have relational data.

I'm going to be exploring the database much more, with CouchDB and PouchDB, [SurrealDB](https://surrealdb.com/), and continuing keep an eye on
SQLite thanks to [LiteFS](https://github.com/superfly/litefs) and [Litestream](https://litestream.io/) piquing my, and the rest of the internet's,
interest. I also want to invest a little bit of time into time series databases like Prometheus, InfluxDB or QuestDB, although those are a little
lower on my priority list.
