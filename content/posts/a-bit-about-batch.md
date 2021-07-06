---
title: A bit about batch
date: 2016-01-21
---

#### Or: why there is no NodeMC installer

Can we just agree on something -- Batch scripting is
terrible and should go die in a fiery pit where all the other Windows
software goes? I don't think I can name any useful features of batch
scripting besides text-based (and frankly pointless) DOS-like games. It
sucks.

I recently tried to port the NodeMC install script from Linux (bash) to
Windows (batch), and while it seemed possible, the simple tasks of
downloading a file, unzipping it, and moving some others around, it
proved to be utterly impossible.

_A quick note before I proceed -- Yes, I realize something like a custom built installer in a more traditional language would have been possible, however I wanted to see what I could do without it. Also I'm lazy._

First and foremost, there is no native way to download files properly.
Most Linux distros ship with cURL or wget (or are installed fairly early
on), which are both great options for downloading and saving files from
the internet. On Windows, it is suggested
[BITS](https://en.wikipedia.org/wiki/Background_Intelligent_Transfer_Service) could do the job. However, on execution, it simply
*does not work*. I got complaints from Windows about how it didn't want
to do the thing. *Fine*. Let's move on to the other infuriating thing.

Stock Windows has the ability to unzip files just file. So why the hell
can I not call that from batch? There is no reason I shouldn't be able
to. But alas, it cannot be done, [at least not
easily](https://stackoverflow.com/questions/21704041/creating-batch-script-to-unzip-a-file-without-additional-zip-tools) \*grumble grumble\*

In conclusion: Batch is useless. It should be eradicated and replaced
with something useful. Because as of now it has very little if any
redeeming qualities that make me want to use it.
