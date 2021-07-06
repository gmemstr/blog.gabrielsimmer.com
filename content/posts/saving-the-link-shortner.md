---
title: Saving the Link Shortner (Quick Post)
date: 2015-10-30
---

#### Aka a very silly mistake 

You may remember the link shortner I wrote about in a past blog post.
Well, I fixed an issue where it couldn't decide if a link was http://,
https://, or just blank. Here's what I did.

Basically, had my strpos() in the wrong order. You need the haystack
*first*, not second. That was an issue. Here's the correct code:

```php
if(strpos($link[0][ 'actual '], 'http://') == false || strpos($link[0]['actual'], 'https://') == false){
    header( 'Location: '.$link[0]['actual']);
 }
```

And then, of course, the little else statement in case it doesn't match:

```php
}else{
    header('Location: http://'.$link[0]['actual']);
}
```

I do love PHP.
