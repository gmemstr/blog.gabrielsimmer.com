---
title: I discovered a /r/programmingcirclejerk of NodeMC...
date: 2016-03-02
---

#### Haters do exist, but hey, publicity right?!

So recently I was looking at the graphs for NodeMC's
traffic on GitHub and realized... there was a thread from
/r/programmingcirclejerk (which I won't link for obvious reasons) that
was directing a bit of traffic (actually quite a bit) to the GitHub
repository. So out of idle curiosity of just having woken up, I decided
*"Why not?"* and opened up the thread. I was greeted with what on the
surface seemed like hatred towards me and my product but upon further
investigation I found it seemed more general mockery towards a few of my
decisions or wording -- or just Node.js in general. So let's analyze
and reply to some comments!

![Top comment](https://cdn-images-1.medium.com/max/800/1*lK1kKdzGiKVu0pyf0PYGGQ.png)

So this is obviously attacking my wording in the README... I claim that
because NodeMC is written in Node.js, it is fast. And I admit, maybe
Node.js in general is not that fast. *However* -- NodeMC has actually
proven to be quite speedy in tests, so I stand by my statement, perhaps
with some tweaked wording...

![](https://cdn-images-1.medium.com/max/800/1*z7IAUMH05TmOiJPrb1Y_Rg.png)

![](https://cdn-images-1.medium.com/max/800/1*xWqHee4G3FlMGeZnZaN57Q.png)

This is most likely touching on (or slapping) my little confusion about
\*nix permissions. The EPIPE error was due to the fact Java couldn't
access the Minecraft server jarfiles, and was throwing an error that
Node.js just had no f\*kng clue what to do with it. I did manage to fix
it.

![](https://cdn-images-1.medium.com/max/800/1*Hcwl8cD1kWwns5lqgpoebg.png)

Unfortunately, I do have to agree with this commenter, Node.js isn't
exactly the most reliable thing, and **most definitely** not the easiest
to debug \*grumble EPIPE grumble\*. Now that said, it's not as
unreliable as Windows 10 \*badum tish\*.

![](https://cdn-images-1.medium.com/max/800/1*QGsJMCN-p0QagVKINTKjvg.png)

And the final comment. I do want to learn Ruby at some point. But I did
laugh when I saw this lovely comment.

![](https://cdn-images-1.medium.com/max/800/1*rIupWDN17_YNRPbrcHt5aA.png)

And of course, my comment, to finish off the pile of steaming comments.
I love you all\~
