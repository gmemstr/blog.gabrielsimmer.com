---
title: State of the Union
date: 2017-10-26
---

#### Where are the projects at?

I have a lot of projects on my plate right now. While
also a full-time student, I am also working on expanding my portfolio
and knowledge for the real world, which means a lot of projects.

My current project I'm focusing on is the podcast hosting app written in
Go, named [**Pogo**](https://pogoapp.net). It's a straightforward CMS for managing podcast
episodes, and automatically generates an RSS feed. It is more than
stable in the current release, and I'd personally feel confident using
it in production (your mileage may vary). Pogo currently features
multiple user support, a flat directory structure for storing episodes
alongside their respective shownotes, *mostly* correct RSS (few bugs to
iron out, but all readers I have tested manage it fine), and a rich
admin interface built out in Vue.js, which includes custom CSS and
episode management.

I am currently working on the user management aspect of Pogo,
implementing a much more sane method of storing and modifying user
accounts, and looking into permissions for restricting certain
functions. Previously, users were stored in a JSON file, became
notoriously difficult to manage in Golang (not impossible however).
Thus, I have moved to the much more portable SQLite3 -- I do have plans
to explore the possibility of picking SQLite3 or MySQL (or MariaDB
etc.), however I plan to focus most of my efforts on ensuring SQLite3
compatibility. With this will come an admin interface for adding and
managing users, which in the current release requires you to manually
add them into the JSON file (and manually generate a bcrypt hash...).
Once the users branch has been merged into the master branch, work will
be done to rework the frontend to use Vue.js instead of plain
JavaScript. I've also been really happy with the current traffic and
outside contributions thanks to my efforts to promote it "organically"
and Hacktoberfest, from which some contributors have found the project.

Another project I've been looking at again is
[**Platypus**](https://getplatypus.io). The simple real time server usage monitor I wrote
back at GGServers has been lying dormant for a long time, and I can't
remember where I left off. It was ready to be deployed, but was not the
focus of the company at the time and I ended up moving it back to my
personal Github. I'm still very proud of the achievement of writing such
a platform in Python, but I want to start rewriting it in Go. The
reasons are twofold; one, I have become very familiar with Go in the
past few months, and believe it could offer much better performance when
it comes to scaling the application. It's never really been tested at
the large scale it should have been, and I'm still a bit leery of the
aspect. I do want to reach out to some larger companies to see if they'd
be interesting in giving me a hand with this. Regardless, a rewrite in
Go + Vue.js is definitely on my mind, and improving the AOR interface so
anyone can write their own version in whatever they already have on
their server.

And I continue to work on articles for [**Git Galaxy**](https://gitgalaxy.com),
writing about whatever comes to mind when it comes to open source
software. I'm currently working on a Hacktoberfest experience roundup,
and researching another opinion piece along the lines of the [Opening
Schools to the
Students](https://gitgalaxy.com/opening-schools-to-the-students/). Analytic numbers are looking solid, and I am more
than happy with how it's turning out.

That is the state of my projects.
