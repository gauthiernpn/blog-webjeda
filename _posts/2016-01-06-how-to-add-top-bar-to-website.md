---
title: Adding Top Bar to Websites
desc: Top bars are beautiful looking lines at the top of a website. A colored top bar would not do any harm. Instead, it increases the beauty of your website (if used correctly). Read to know how I have implemented it in my websites.
keywords: top bar, website top line, top border of website, top colored line in websites
author: sharathdt
tags: Github-Pages Web-Design
image: top-bar-on-websites.png
layout: post
permalink: /top-bar-website/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}


## Why top bar?
{: .clear}
I started considering top bar only after I saw the designers from [Quora](https://www.quora.com){:rel='nofollow'}{:target="_blank"} started using it. I also used to have a top bar on this blog but after the new design I no longer use it. But, one of my blogs [Nallikayi](http://nallikayi.com){:target="_blank"} has a nice top bar which goes with the design.

<div class="clear"></div>   

* Do not remove this line (it will not be displayed) 
{:toc}

I remember YouTube using a red top bar to show how the progress of page loading. That was only for a while and <strike>for some reason they stopped it.</strike> But it seems like they are still using it! You can see it when you click on a video link. Actually it is a great idea to show the users how much page has been loaded without any distractions. By the time I'm writing this blog <a rel="nofollow" href="https://www.freecharge.in" alt="Freecharge">Freecharge</a> is using the top bar as a progress indicator. It must be a ```div``` on top with a 1 pixel border but looks like body top border.

{% include adsense-inside-post.html %}

![Android chrome browser top loading bar]({{ site.url }}/images/android-chrome-browser-using-top-bar-screenshot.jpg)
{: .right .half}
If you have seen Chrome browser on android, they still use this. May be it is using a different code but visually similar to that we use in websites.

So here it is giving some valuable information. But what I want is just a minimal colored top bar to enhance the visual appearance. It is very easy and can be done with a single line of code!
{: .clear}

## what is the code for top bar!

Just copy these lines to your css file and you'll have a top bar! So far we have called this top bar but in reality it is the top border of your body. Normally it is invisible, we are just giving it a size, style and color. Pretty neat. Isn't it? There is not a single extra ```div``` used. So there is no extra load on your website!


{% highlight css %}
body {
  border-top: 4px solid #37ba8a;
  margin: 0;
}
{% endhighlight %}


So that's all there is! Use ```em``` instead of ```px``` if you like. I use ```em``` as I have configured it to adjust to the screen-size.  Now change the color according to your theme and don't make it very contrasting, say a blue top bar on red background. That is not very pleasing to eyes. And also make sure the body has no margin. Otherwise you may not get the top bar where you wanted.

Though it is a simple thing, it gives a huge impact on the look and aesthetics.
Check the difference between these two sample websites I made for my mom.

No top bar: [No top bar](http://webjeda.com/No-top-bar/){:rel='nofollow'}{:target="_blank"} 


Top bar: [Top bar](http://webjeda.com/top-bar/){:rel='nofollow'}{:target="_blank"}

## Extensible!
![top border used by google]({{ site.url }}/images/top-border-used-by-gmail.jpg)
{: .right .half}
This can be used on buttons to make them look awesome! This can give a modern look to almost all the elements. One such thing I have noticed is in **gmail** categories.

Here is a button with just borders
{: .clear}

<button class="border-style">WebJeda</button>

<style>
.border-style {
    font-size: 18px;
    color: #41A720;
    margin: 0;
    padding: 10px 25px 10px 25px;
    background-color: transparent;
    border: 1px solid #41A720;
    border-radius: 2px;
}
</style>

Here is the HTML code..

{% highlight html %}
<button class="border-style">WebJeda</button>
{% endhighlight %}

.. and CSS

{% highlight css %}
button.border-style {
    font-size: 18px;
    color: #41A720;
    margin: 0;
    padding: 10px 25px 10px 25px;
    background-color: transparent;
    border: 1px solid #41A720;
    border-radius: 2px;
}
{% endhighlight %}

Try mplementing top bar on your website and let me know how it went.

And don't forget to leave the link in the comment section, of your website with newly created top bar.

Thanks for reading!