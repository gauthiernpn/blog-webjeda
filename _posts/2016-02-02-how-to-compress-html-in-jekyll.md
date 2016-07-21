---
title: Minify Jekyll Blog HTML
desc: Minifying HTML makes Jekyll superfast. Minifying CSS and JS is already in practice but compressing html is not practiced by everyone. Since Jekyll posts and pages are in markdown and you may not be able to minify all of them using a task runner. Learn how to minify Jekyll html using this method. 
keywords: minify Jekyll html, Jekyll minify, jekyll html minify
author: sharathdt
tags: Jekyll SEO
image: how-to-minify-jekyll-html.png
layout: post
permalink: /compress-html-jekyll/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

## Why do we have to minify HTML?
{: .clear}
Speed is a factor to rank high in Google search page. Minifying HTML can lead to an increase in speeds around 5% or more. Lighter the website easier to load even on a slow connection. Usually, html file consists of a lot of empty spaces, comments in between {% raw %}<!-- and -->{% endraw %}, new lines, blank spaces etc., It is good to keep what really matters and omit the rest.

<div class="clear"></div>   


* Do not remove this line (it will not be displayed) 
{:toc}


Though minifying CSS and JS is largely practiced, minifying HTML is not given such an importance. Maybe because there is not much to minify compared to static files like CSS and JS. But it does help loading your website at a better speed even on 2G connections. Moreover, [PageSpeed](https://developers.google.com/speed/pagespeed/insights/){:rel='nofollow'}{:target="_blank"} recommends minifying HTML.

I have seen huge benefits by minifying my Jekyll blog. What if I tell you that minifying reduces the file size by more than 20%! May be because I have a lot of blank spaces and new lines in the un-minified version. And that's an improvement I shouldn't be missing.

Here are the minified and unminified files of my last post. They have the same content by the way. You can check the file size by downloading them.

[Unminified](/data/view-source_blog.webjeda.com_how-to-fetch-first-image-from-jekyll-post.html){:rel='nofollow'}{:target="_blank"} - 130kb

[Minified](/data/view-source_blog.webjeda.com_how-to-fetch-first-image-from-jekyll-post-minified.html){:rel='nofollow'}{:target="_blank"} - 100kb

{% include adsense-inside-post.html %}

## How to minify Jekyll html?

So far in my tutorials, I have never used command line interface. Not that I hate it but I think it's difficult for beginners to comprehend. Likewise, you can minify html using ```Grunt``` or ```Gulp``` task runners but for a beginner they might seem alien technologies. And when we are using an automatic minifier that takes care of everything then why do we need a task runner?! And also I prefer solutions that does not involve plugins.

Now to minify Jekyll blog, 

### Step 1: Download Compress html
Go to [this link](http://jch.penibelst.de/){:rel='nofollow'}{:target="_blank"} and download the ```compress.html``` file. It should be under the **Installation** heading. 

### Step 2: Place Compress in layouts
Place this html file inside your ```_layout``` folder.

### Step 3: Add front matter to default layout
Open ```default.html``` in ```_layouts``` folder and copy the below front matter at the top of the page. If you do not have ```default.html``` then use a top level layout which is used in all pages.

<pre>{% raw %}
---
layout: compress
---
{% endraw %}</pre>

The ```default.html``` should look something like this after copying the code

{% highlight html %}
{% raw %}
---
layout: compress
---
{% endraw %}
<!DOCTYPE html>
<html>
.
.
.

</html>
{% endhighlight %}



### Step 4: Save changes
Save and commit the changes. By default the ```compress``` layout replaces contiguous whitespace with a single whitespace character. But if you want additional options then you can use this snippet inside your ```_config.yml``` file.

{% highlight yaml %}
compress_html:
    clippings: []
    comments: []
    endings: []
    ignore:
    envs: []
    blanklines: false
    profile: false
    startings: []
{% endhighlight %}


Read all about these settings in the [documentation](http://jch.penibelst.de/){:rel='nofollow'}{:target="_blank"}.

Now all your web-pages that directly or indirectly uses the layout ```default``` will be minified. You can exclusively mention for certain pages to minify by adding the front matter given above. 

So I hope this tutorial helped you minify your Jekyll blog. If there is a better way to do this, then please let me know in the comment section.

<div class="warning">
<h3>Warning</h3>
<p>My disqus comment stopped loading after using this method. So for the time being I'm not using it. If you are using disqus then do not use this method (for now).</p>
</div>

<div class="tips">
    <h3>Update</h3>
    <p>
        Disqus started to work after cleaning up unnecessary comments inside disqus.html. Here is the <a href="https://raw.githubusercontent.com/sharu725/emerald/gh-pages/_includes/disqus.html" target="_blank" ><strong>raw file</strong></a>.
    </p>
</div>

Thanks for reading!