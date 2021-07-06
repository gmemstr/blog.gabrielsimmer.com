---
title: Python / Flask Logins
date: 2017-02-22
---

#### This was fun! \*twitch\*

Bloody hell, where do I start...So I recently got back
from a two week vacation down to LA (Disneyland) and then further south
to Mexico. During those two weeks I did little to no coding, which
greatly relaxed me and allowed me to think about what my goals with my
many projects were.

And then I got home. And decided that the best thing to do (besides
getting a violent cold) was to start work on a login system for
Platypus. You know, so that admins can edit servers and whatnot. Oh boy
are we in for some fun.

#### Initial Approach

At first I wanted to use Flask-Login, because that seemed like the
logical way of doing things. It integrated with Flask, which is
fantastic because I use that framework for literally everything (sorry
Django, not feeling you yet). It (seemed) to provide an easy way to
handle restricting views to logged in users. And thus I set out.

The first thing I noticed was that, like Flask, Flask-Login assumes
nothing about your stack or how you should implement things. It requires
you to write your own class for users and implement methods for
retrieving users and passwords from a database, and also validating
users login details. And then it hit me. Flask-Login is for *session*
management, not *user* management. Back to the drawing board, slightly
red faced when I realised what I was doing wrong.

#### IYWIDP, DIY

**I**f **y**ou **w**ant **i**t **d**one **p**roperly, **d**o **i**t
**y**ourself. And so I did. I grabbed bcrypt's Python implementation and
started writing my own system that relies on old school cookies as
authentication. There were some false starts, but I eventually rigged
together something that works, albeit with duct tape. What happens is
thus. First, user requests /admin, which is obviously not a route we
want unrestricted. So Flask grabs a cookie the browser provides and
checks it against the current session token internally. If the two don't
match or the cookie is blank, you're redirected to a login screen. The
login form POSTS the data to the login route, which compares the passed
password the the encrypted, salted and hashed password stored (as most
logins do). Then, the function returns a unique key (actually a bcrypt
salt) that acts as the session token. Cookie is set, user is sent to
admin page. Brilliant!

Obviously there are some drawbacks that are not entirely intentional.
For one, only one user can be auth'd at a time. This isn't a
particularly troublesome problem in my deployment, however it's
definitely not ideal. Also the session key is a bcrypt salt
stringified -- this looks a bit funky but was a quick hacky way to
generate a pseudo-random key. It's never used for anything beyond
authenticating the browser.

*Hopefully it's secure enough.*

Now anyone who wants to have a crack at breaking the login, go right
ahead, I won't stop you. Hell, I encourage it, and file issues as you
see fit.

[Platypus on GitHub](https://github.com/ggservers/platypus)
