---
title: The TVDB Google App Script
date: 2016-12-06
---

#### Let's learn something new!

My girlfriend Becky and I enjoy watching TV shows
together. So much so, in fact, that we've started putting together a
spreadsheet of the shows the need to binge watch together. So just for
the hell of it, I threw together a rather basic (and messy) Google App
Script that lives in the spreadsheet, which pulls information from [The
TVDB](https://thetvdb.com/) regarding
how many episodes there are and how long it would take to binge watch
all the shows (roughly).

Some things I learned while working in the Google App Script IDE. First,
tabs are only two spaces, instead of the usual four I work with in
Python. Which messed me up slightly when I first started, but I go much
more used to it. Second, it's just JavaScript, really. I expected some
sort of stripped down programming language but it's really just a
slightly tweaked JS environment, with some functions that allow you to
interact with Google Docs/Sheets/Forms etc. And finally, I learned just
how useful Google App Scripts can be -- I never really used them, and
believed them to be a waste of time to learn. Alas, I was wrong, my
elitist thinking getting the better of me.

So let's talk about the actual script. You can find the whole thing in
the Gist below, a slightly tidied up and revised version. You'll need an
API key from The TVDB, and I highly recommend you check out [their API
docs](https://api.thetvdb.com/swagger) so you know exactly what sort of info and routes
we're using.

Essentially, what happens in this. First, we search (using
`searchTvdb(show, network)`) for the specific show, using the network to
filter out results in case there are multiple shows with the same name.
Next, we take the showId it returns and query TVDB for the info
corresponding to the show -- we're most interested in the average
runtime from this query. We also ask TVDB for the summary of the
episodes, which returns the number of seasons, episodes aired, and so
on. We aggregate all this data into one clump of data and then throw it
into the spreadsheet.

It's very inefficient, I realize that. There are plenty of things I
could probably improve performance wise, however it works fine. I expect
the more shows in the spreadsheet the longer it will take (about 12
seconds with a 14 item list), but I'll refine a bit in the future.

![How the spreadsheet looks](https://cdn-images-1.medium.com/max/600/1*a6NU2Lv_H2gHrffRT2pfEw.png)

[Gist source](https://gist.github.com/gmemstr/d0024ab38a9cd0aae3a8cce25202c9b0)

> "If everyone demanded peace instead of another television set, then
> there'd be peace." -- [**John
> Lennon**](https://www.goodreads.com/author/show/19968.John_Lennon) **(Probably)**
