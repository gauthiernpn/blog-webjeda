---
title: Lazy Loading CSS
desc: Loading big CSS file at the end of the document makes sense because some times CSS takes up a lot of time to load. Learn how to defer CSS loading which makes your website super-fast. PageSpeed is a tool by Google where you can find the website speed.
keywords: defer css, lazy load css, load css at the end
author: sharathdt
tags: Jekyll SEO Web-Design
image: lazy-load-css-for-fast-website.jpg
layout: post
permalink: /lazy-load-css/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}
<a target="_blank" rel="nofollow" href="http://www.freepik.com/free-vector/cartoon-animals_802878.htm">Designed by Freepik</a>

## Why lazy load css?
{: .clear}
Along with loading JavaScript at the end of the document, you should also load big css files at the end. This makes your website super-fast. Because the main content loads first. So even on a slow connection, the content will be available for the user. And also faster the website SEO friendly it is.

<div class="clear"></div>   


* Do not remove this line (it will not be displayed) 
{:toc}


Many a times - on a slow connection - a user may wait for a maximum of 5 to 6 seconds and if the website is blank and still busy loading your **head tag** with a huge ```css``` file, the user may hit the back button!

You just lost a potential subscriber or even customer if you are selling something. Using a pre-loader like I did on [my website](http://webjeda.com){:target="_blank"} can engage the users for a few more seconds but not forever. So you should not make your users wait for the main content.

In this method of lazy loading css, the content loads without any style and then the stylesheet loads followed by JavaScript. You may have observed this while browsing my website. This is important for a user with a slow connection. Content(visible stuff) should load at the very beginning. Style(css) and scripts(js) can wait.

This ensures that even if the style or script fails to load, the user can still read the content (if the content is text). You can also [minify your blog for faster loading](/how-to-compress-html-in-jekyll/){:target="_blank"}.

What I did was, I put a script at the end of the html document to insert the css **link tag** only after loading the document. This was helpful because my ```main.css``` is a huge file and also font awesome stylesheet that loads from a CDN.

{% include adsense-inside-post.html %}

After testing in [PageSpeed](https://developers.google.com/speed/pagespeed/insights/){:rel='nofollow'}{:target="_blank"} I found that my website is faster than ever! Do use this tool to find out what is slowing down your website.

Another very good tool to analyze website loading time is [GT Metrix](https://gtmetrix.com/){:rel='nofollow'}{:target="_blank"}. This tool will give you a deep analysis on why your website is slow and provides optimized files to use.


## How to load CSS at the end?

This is possible if I declare my link tag at the end of the document. But it is advised by w3c to place link tags only in the head section. So I'm using a script to place the link tag( linking css) in the head section.

{% highlight html %}

<script defer>
var cb = function() {
var l = document.createElement('link'); l.rel = 'stylesheet';
var m = document.createElement('link'); m.rel = 'stylesheet';
l.href = '/css/main.css';
m.href = 'https://maxcdn.bootstrapcdn.com/font-awesome/4.5.0/css/font-awesome.min.css';
var h = document.getElementsByTagName('head')[0]; h.parentNode.insertBefore(l, h);
var i = document.getElementsByTagName('head')[0]; i.parentNode.insertBefore(m, i);
};
var raf = requestAnimationFrame || mozRequestAnimationFrame ||
webkitRequestAnimationFrame || msRequestAnimationFrame;
if (raf) raf(cb);
else window.addEventListener('load', cb);
</script>

{% endhighlight %}

The above code loads two CSS files. One is local ```main.css``` and the other is remote ```font-awesome.min.css```. You can make use of this code and change it accordingly. Make sure you edit the path properly.


If you observe the script tag carefully, I have added ```defer``` attribute to it. This will load this script at the very end. You can change this to ```async``` if you want it to load along with the content. Test it out and see which one works best for you.

## Problems I faced while lazy loading css

This problem occurred because I have Adsense. My AdSense code is responsive. It adjusts to the screen size mentioned in the media query. And the media query is inside ```main.css``` which I have made to load at the very end!

Adsense script loads before ```main.css``` and assumes that the screen is full width whereas my content is not full width. My content only goes in the center leaving some gap on both left and right sides. But AdSense has already assumed that it is full screen and adjusts its ad size to full screen and hence the ad flows out of the content.


## Inline critical CSS

I struggled hard to tackle this. And after a while, I realized that I can define the width of my content with inline-css even before the AdSense code loads! Thus avoiding it to overflow. You can inline any style that you think is required in the beginning.

{% highlight html %}
  <div id="container" style="max-width:730px;padding: 0 1.5rem;margin: 0 auto;">
        <main>
         {% raw %}{{ content }}{% endraw %}
        </main>
  </div>
{% endhighlight %}

So that solved the problem :) You can in-line important css this way. When the css file is made to load at the end, your content will not have any styling which means the content may show up on the left side of the screen for a fraction of a second, fonts appear with a default web-font and some SVGs and images may show up in their full size.

To avoid this, in-line some of the css which makes everything look smooth. Do not in-line too much css though. It is not a good practice and also your users shouldn't get an impression that you do not know how to use css.

## Inline SCSS in Jekyll
Jekyll supports sass preprocessor. So any number of ``scss`` files can be used to make a single ``main.scss`` file which in turn generates a ``main.css`` file upon build.

And also, Jekyll supports linking ``scss`` file directly inside html and can be changed to ``css`` file using scssify filter.

{% highlight html %}{% raw %}
  <style>
          {% capture include_to_scssify %}
          {% include critical.scss %}
          {% endcapture %}
          {{ include_to_scssify | scssify }}
  </style>
{% endraw %}{% endhighlight %}

But remember, the scss file you want to include should be inside **_includes** folder.


I hope this article has helped you to speed up your website. Let me know how it went. Leave a comment if you have any suggestion. I would be happy to implement it.


Thanks for reading!