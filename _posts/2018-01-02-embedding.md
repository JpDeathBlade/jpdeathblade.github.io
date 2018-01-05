---
layout: post
title:  "Embedding"
date:   2018-01-02 00:00:00 -0500
categories: blog
tags: [JpDeathBlade, Blog]
published: true
author: "Jp"
excerpt_separator: <!--more-->
---
Since I'm working on this blog most of the early blog posts will be about it. The first thing that needs to be done is embedding of media. Some of it is simple, some of it not so much but I'll cover some of the more important social media things first.

<!--more-->

### Images
Images are the most important and with Jekyll it's super easy to make them display. I've added some images for iOS so that when you bookmark this blog to your springboard you'll see an image instead of a photo of the blog. We can use one of those images as our test. It looks like this:

![Hunk]({{ "/assets/images/apple-icon/apple-touch-icon.png" | absolute_url }})

The code to generate it is super straight forward. You give Jekyll a url and some alt-text and it does the work for you.

{% raw %}
```
![Hunk]({{ "/assets/images/apple-icon/apple-touch-icon.png" | absolute_url }})
```
{% endraw %}

The only real problem is that you cannot set the size of the image, so you are stuck with whatever size the image is. Which might not be a problem for most images but doesn't give you the control you might like. To get around this, you could make an image include and pass the url, alt-text, and size to it as parameters. This is something I'll do in the future so I can control images, make them reactive to screen size, or even add an overlay so when you click on them it opens into a fullscreen version of the image. Lots of room to improve here.

### Youtube Videos
Youtube is the next big player that I want to support. I make videos from time to time so being able to share that with an audience is important. Even more so if the video in question has something to do with the post itself. Here is an example of a song I enjoy.

{% include youtubePlayer.html id="7VEtjp4sVA8" %}

Youtube's embedding is actually pretty nifty, the only thing different about the code between videos is the video id. That means we can break it out into it's own file and pass the video id as a parameter and embed any video we want.

First create a file called 'youtubePlayer.html' and include the following:

{% raw %}
```
<iframe width="560" height="315" src="https://www.youtube.com/embed/{{ include.id }}" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>
```
{% endraw %}

And then call this from a post:

{% raw %}
```
{% include youtubePlayer.html id="7VEtjp4sVA8" %}
```
{% endraw %}

### Tweets
Tweets are a bit harder. Since the HTML for them is so locked into what the tweet itself is you need a special
plugin for tweets to display, The [Jekyll Twitter Plugin](https://github.com/rob-murray/jekyll-twitter-plugin). To be honest, I'm not even sure if this works with Github Pages at the time of writing so hopefully you see a tweet below.

The code to do that is simple, and included on the plugins page:

{% raw %}
```
{% twitter https://twitter.com/JpDeathBlade/status/918879290283954176 %}
```
{% endraw %}

There are plenty of other social websites that I want to support (like Facebook or Instagram) but for the time being these three things are more than enough for what I want out of this blog. I'll continue to grow it and add little features as I learn more about Jekyll and I'm excited to watch this place grow as we continue into the new year.

**EDIT:**    
Looks like it didn't work. So instead we have to use Twitter's embedding HTML:

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">My <a href="https://twitter.com/hashtag/Destiny2?src=hash&amp;ref_src=twsrc%5Etfw">#Destiny2</a> video made it onto the <a href="https://twitter.com/Bungie?ref_src=twsrc%5Etfw">@Bungie</a> Community Page! - <a href="https://t.co/D4OWDflu5q">https://t.co/D4OWDflu5q</a></p>&mdash; Joseph Stuhr (@JpDeathBlade) <a href="https://twitter.com/JpDeathBlade/status/918879290283954176?ref_src=twsrc%5Etfw">October 13, 2017</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Which looks like this:

```
<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">My <a href="https://twitter.com/hashtag/Destiny2?src=hash&amp;ref_src=twsrc%5Etfw">#Destiny2</a> video made it onto the <a href="https://twitter.com/Bungie?ref_src=twsrc%5Etfw">@Bungie</a> Community Page! - <a href="https://t.co/D4OWDflu5q">https://t.co/D4OWDflu5q</a></p>&mdash; Joseph Stuhr (@JpDeathBlade) <a href="https://twitter.com/JpDeathBlade/status/918879290283954176?ref_src=twsrc%5Etfw">October 13, 2017</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
```

Ugly... there seems to be no easy way to include Tweets without just manually including it. I guess I got to look into that more.

~ Jp
