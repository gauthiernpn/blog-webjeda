---
title: Optimize Font Awesome to 10KB!
desc: Font Awesome is a huge css file. We can optimize it for only used cases and trim it down to just 10KB! Use this method to reduce the size of font awesome.
keywords: 
author: sharathdt
image: optimize-fontawesome.svg
tags: Web-Design
permalink: /optimize-fontawesome/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

Icons are an integral part of web designing. Gone are the days where individual icons were used like an image. Now it's the time of web fonts. Font awesome is one such web font. It is just like a font but in place of letters, we have icons! Dave Gandy created font awesome in 2012. Many designers use this instead of SVG images because font awesome makes designing easy. Almost all kinds of icons are available and they are infinitely scalable!
{: .clear}

<i class="fa fa-github-alt fa"></i>
<i class="fa fa-github-alt fa-2x"></i>
<i class="fa fa-github-alt fa-3x"></i>
<i class="fa fa-github-alt fa-4x"></i>
<i class="fa fa-github-alt fa-5x"></i>

A simple website uses at least 4 to 5 icons. If we include share button icons and footer icons, the number grows. Why do we use such a huge library for just 10 icons? Because adding or removing or changing an icon is very easy in font awesome. If you have used local png icons using css sprite sheets, you'll know the pain of changing or adding an icon.

Font awesome makes a web designers life easy. Adding icons is as simple as adding a ``<h1>`` tag. Resizing is done through attributes, flipping, stacking, spinning is all possible with font awesome. But apart from those 10 icons we use and some styles, all other icons are of no use to us. They load along with the ones we need. Though font awesome is cached by browsers since many websites use it, we have to give attention to first-time visitors who may have a browser without cached font awesome css. Moreover, font awesome version updation is done every time new icons are added and you should also keep version of the CDN link up to date.

## Why should we optimize font awesome?
Since it is a huge file, we have to trim it down to our needs. If we are using only 10 icons then why do we need 100 other icons? The size of font awesome web font is 90KB by the time I'm writing this article. Added to that, minified font awesome css is 30KB. So overall 120KB! What I'm trying is to reduce this to below 12KB which is more than **90%** compression!!

Imagine how fast the icons will load! After implementing this, my website scored 89% on Google pagespeed insights. It used to be 52%!

* Do not remove this line (it will not be displayed) 
{:toc}


## How can we optimize font awesome?
Basic idea is to edit the font file to make it as small as possible. Removing unwanted glyphs will reduce the size drastically. But we should analyze our website to make sure we note down all the font awesome icons that are in use.

Removing unused glyphs reduced the ``woff`` file size from 90KB to 8.5KB. This size depends on how many icons you need. The size increase with the increase in the number of icons. Removing unwanted css from ``fontawesome.min.css`` reduced the size to 2KB from 30KB. The overall size of font awesome after optimizing is around 11KB!

{% include adsense-inside-post.html %}

### Step 1: Localize Font awesome
We cannot edit font served from CDN. So we should use font awesome locally. Remove the font awesome CDN link from the head tag if you are using it. Go to http://fontawesome.io/ and download the latest version of fontawesome. Unzip and keep it in the website repository. In our case, the root of the repository.

Call the css file which is inside font awesome css folder in the head tag like this.

{% highlight html %}
<link rel="stylesheet" href="/font-awesome/css/font-awesome.css">
{% endhighlight %}

You will also have a minified file ``font-awesome.min.css``. But let's not use it right now as we may have to edit css.

Once this is done, clear cache from the browser and load your website locally (``jekyll serve`` if Jekyll site). Check if the font awesome icons are loading. Try to refresh by pressing ``Ctrl+f5`` several times. If the font is still loading then we are good to go to the next step.

### Step 2: Remove unnecessary files
For a font to load, modern browsers just need ``woff`` file. So other files such as ``woff2``, ``ttf``, ``eot``, ``svg`` are not necessary. So delete all these files from the **fonts** folder and leave only ``fontawesome-webfont.woff``.

![font awesome contents](/images/optimize-fontawesome-css.jpg)
{: .right .half}

Font awesome has **less** and **scss** variants which you can use or delete them. Since using only the css variant, so I'm deleting others. So **css** and **fonts** folders are enough to work with.

### Step 3: Edit the font file
{: .clear}
This step needs an application. Go to [FontForge](http://fontforge.github.io/en-US/){:rel='nofollow'}{:target="_blank"}, download and install the application.

Open ``fontawesome-webfont.woff`` with this application and find the glyphs. You may have to scroll down a lot. You can go to **Encoding** then click on **Compact** to get them right on the top.

Now clear any glyph you think is not necessary and you do not use it in the future. This is where you have to browse through the website and look for all the icons you have used.

![edit fontawesome webfont](/images/edit-fontawesome-webfont.jpg)
{: .right .half}

I use icons for share bar, footer and mostly on about page. So I kept those icons and cleared out everything else. Hold **Shift** for multiple selection. Now, click on **File** and then in **Generate Fonts**. Save it with any name you like. 

This file is your new web font ``woff`` that should be used inside fonts folder. It is better to rename it back to ``fontawesome-webfont.woff`` and replace the original with this one.

Test the website again to check whether all the icons are loading(they should) and push changes. This can be further optimized by converting the font to base64 and hence reducing one more request!

## Conclusion
You may use Bootstrap, Font awesome or any similar web font in your website. But make sure you optimize them to use only things that are necessary. Every byte you save, every request you reduce improves page speed by milliseconds. Even a single millisecond improvement in page speed matters. 

Thanks for reading!