---
title: Making a link shortner
date: 2015-10-26
---

My first thought when I got the following message

> Also, do you know how to make a URL shortner?

was *yes, probably, all things considered*. The last two days I'm been
working on it, and it's turned out semi-well. There's a bug or two that
needs fixing, but I figured I could post a short tutorial on how to do a
simple one.

Right, I'm assuming a few things:

-   [You have a web server]{#6644}
-   [You have a short domain/subdomain]{#0b99}
-   [You have MySQL & PhpMyAdmin]{#f238}
-   [You know how to use PHP]{#91de}

With that out of the way, let's set up our MySQL database. You'll need a
table called **links**, in which it should have the columns laid out
like so:

```yaml
links:
 - actual [text]
 - short [text] (no other special values are required)
```

Now, in our file named shorten.php (which you should download
[here](https://ghostbin.com/paste/xk7gh), we need to edit a few things, first, make sure you change the PDO to connect to your database. Also, change

```php
$b = generate_random_letters(5);
```

to be any length you'd like. Lastly, make sure

```php
value="url.com
```

is the domain or subdomain of your site.

Great! Now that we can create short links, we need to interpret them. In
long.php ([link](https://ghostbin.com/paste/yzbdj)), change the first

```php
header('Location: url.com');
```

to redirect to your main website. This will redirect users to the main
website if there is no short link.

Fantastic, you're all done! As a bonus though, you can use a .htaccess
file to tidy up your URL.

```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^([A-Za-z0-9-]+)/?$ long.php?short=$1 [NC,L]
```

So instead of *http://url.com/long.php?short=efkea*, it will be
[*http://url.com/efkea*](http://url.com/efkea).

That's all for today :)

#### Files index:

[shorten.php -- GhostBin](https://ghostbin.com/paste/xk7gh)

[long.php -- GhostBin](https://ghostbin.com/paste/yzbdj)

[.htaccess -- GhostBin](https://ghostbin.com/paste/vznww)
