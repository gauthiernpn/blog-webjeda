---
title: Adding Sitemap to Jekyll Blog
desc: Submitting sitemap to major search engines is important to get indexed and rank better. Jekyll blogs will not have sitemap by default but we can create one using this method. A sitemap facilitates search engines as an easy main-door to crawl through all the post and pages you have in your blog.
keywords: sitemap in Jekyll blog, Jekyll sitemap, sitemap for Jekyll
author: sharathdt
tags: Jekyll SEO
image: add-sitemap-to-Jekyll-github-pages.png
layout: post
permalink: /jekyll-sitemap/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

In one of my previous posts, I wrote on [How to create a Jekyll Blog](/create-jekyll-blog/){:target="_blank"}. If you have created a blog or if you already have a Jekyll blog then go through this tutorial to know how to create a sitemap automatically and manually in easy steps.
{: .clear}

* Do not remove this line (it will not be displayed) 
{:toc}

<div style="border: 1px solid #aaa"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 716 480"><style>.a{fill:#31BEE9;}.b{fill:none;stroke:#58595B;}.c{fill:#FDFDFE;font-family:'Helvetica';font-size:90%}</style><path d="M413.6 41.3c0 9.6-7.8 17.5-17.5 17.5h-74.7c-9.6 0-17.5-7.8-17.5-17.5l0 0c0-9.6 7.8-17.5 17.5-17.5h74.7C405.8 23.9 413.6 31.7 413.6 41.3L413.6 41.3z" fill="#00AEEF"/><path d="M273.9 173.5c0 9.6-5.9 17.5-13.1 17.5h-55.9c-7.2 0-13.1-7.8-13.1-17.5l0 0c0-9.6 5.9-17.5 13.1-17.5h55.9C268.1 156.1 273.9 163.9 273.9 173.5L273.9 173.5z" class="a"/><path d="M273.9 378.5c0 9.6-5.9 17.5-13.1 17.5h-55.9c-7.2 0-13.1-7.8-13.1-17.5l0 0c0-9.6 5.9-17.5 13.1-17.5h55.9C268.1 361 273.9 368.8 273.9 378.5L273.9 378.5z" class="a"/><path d="M523.3 173.5c0 9.6-5.9 17.5-13.1 17.5h-55.9c-7.2 0-13.1-7.8-13.1-17.5l0 0c0-9.6 5.9-17.5 13.1-17.5h55.9C517.5 156.1 523.3 163.9 523.3 173.5L523.3 173.5z" class="a"/><path d="M523.3 376.8c0 9.6-5.9 17.5-13.1 17.5h-55.9c-7.2 0-13.1-7.8-13.1-17.5l0 0c0-9.6 5.9-17.5 13.1-17.5h55.9C517.5 359.4 523.3 367.2 523.3 376.8L523.3 376.8z" class="a"/><path d="M146.9 109.2c0 8.8-5.3 15.8-11.9 15.8H84.3c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C141.6 93.3 146.9 100.4 146.9 109.2L146.9 109.2z" class="a"/><path d="M146.9 173.5c0 8.8-5.3 15.8-11.9 15.8H84.3c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C141.6 157.7 146.9 164.8 146.9 173.5L146.9 173.5z" class="a"/><path d="M146.9 237.9c0 8.8-5.3 15.8-11.9 15.8H84.3c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C141.6 222.1 146.9 229.2 146.9 237.9L146.9 237.9z" class="a"/><path d="M641.7 109.2c0 8.8-5.3 15.8-11.9 15.8h-50.7c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C636.4 93.3 641.7 100.4 641.7 109.2L641.7 109.2z" class="a"/><path d="M641.7 173.5c0 8.8-5.3 15.8-11.9 15.8h-50.7c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C636.4 157.7 641.7 164.8 641.7 173.5L641.7 173.5z" class="a"/><path d="M641.7 237.9c0 8.8-5.3 15.8-11.9 15.8h-50.7c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C636.4 222.1 641.7 229.2 641.7 237.9L641.7 237.9z" class="a"/><path d="M645.2 312.5c0 8.7-5.3 15.8-11.9 15.8h-50.7c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C639.8 296.6 645.2 303.7 645.2 312.5L645.2 312.5z" class="a"/><path d="M645.2 376.8c0 8.8-5.3 15.8-11.9 15.8h-50.7c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C639.8 361 645.2 368.1 645.2 376.8L645.2 376.8z" class="a"/><path d="M645.2 441.2c0 8.8-5.3 15.8-11.9 15.8h-50.7c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C639.8 425.4 645.2 432.5 645.2 441.2L645.2 441.2z" class="a"/><path d="M146.9 344.7c0 8.8-5.3 15.8-11.9 15.8H84.3c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C141.6 328.8 146.9 335.9 146.9 344.7L146.9 344.7z" class="a"/><path d="M146.9 409c0 8.8-5.3 15.8-11.9 15.8H84.3c-6.5 0-11.9-7.1-11.9-15.8l0 0c0-8.7 5.3-15.8 11.9-15.8h50.7C141.6 393.2 146.9 400.3 146.9 409L146.9 409z" class="a"/><path d="M273.9 173.5C360.8 184.3 358.8 58.8 358.8 58.8s13.5 132.2 82.5 114.8" class="b"/><path d="M273.9 378.5c96.7 9.2 84.9-320.2 84.9-320.2s-13.4 304.5 82.5 318.6" class="b"/><path d="M567.3 109.2c-51.1 15.8-43.9 64.4-43.9 64.4h44" class="b"/><path d="M523.3 173.5c0 0 6.1 38 44 64.4" class="b"/><path d="M570.7 312.5c-54.9 10-47.4 64.4-47.4 64.4h47.4" class="b"/><path d="M523.3 376.8c0 0 3.5 73.1 47.4 64.4" class="b"/><path d="M146.9 109.2c48.4 5.7 45 64.4 45 64.4l-45 0" class="b"/><path d="M191.9 173.5c0 0 2 54.2-45 64.4" class="b"/><path d="M146.9 348c47.6 6.5 45 30.5 45 30.5s-4.7 20.1-45 30.6" class="b"/><text transform="matrix(1 0 0 1 343.1787 45.2271)" class="c">  Home</text><text transform="matrix(1 0 0 1 215.5659 382.6826)" class="c">  About</text><text transform="matrix(1 0 0 1 90.6831 348.002)" class="c">  Contact</text><text transform="matrix(1 0 0 1 90.6831 241.4224)" class="c">  Post...</text><text transform="matrix(1 0 0 1 90.6831 175.1274)" class="c">  Post 2</text><text transform="matrix(1 0 0 1 90.6831 113.71)" class="c">  Post 1</text><text transform="matrix(1 0 0 1 90.6831 414.1963)" class="c">  Project</text><text transform="matrix(1 0 0 1 466.6953 380.707)" class="c">  Tags</text><text transform="matrix(1 0 0 1 449.4131 177.9346)" class="c">  Categories</text><text transform="matrix(1 0 0 1 586.1201 177.958)" class="c">  Design</text><text transform="matrix(1 0 0 1 590.2148 241.4233)" class="c">  Apps</text><text transform="matrix(1 0 0 1 587.1436 316.4893)" class="c">  Android</text><text transform="matrix(1 0 0 1 599.0869 380.709)" class="c">  iOS</text><text transform="matrix(1 0 0 1 579.0967 445.0215)" class="c">  Windows</text><text transform="matrix(1 0 0 1 594.3096 111.6626)" class="c">  Dev</text><text transform="matrix(1 0 0 1 217.6133 176.9346)" class="c">  Posts</text></svg></div>
{: .right .half}

A sitemap is a list of links to all your web pages. It will be in ```.xml``` format. It helps search engine bots to crawl your website. It will also have metadata such as dates of posts, pages, last modified date and how often it was updated etc., It looks something like your **feed.xml** file but with different tags. 

Here is [my blog's Sitemap](/sitemap.xml){:rel='dofollow'}{:target="_blank"}


## Why is a Sitemap used?
{: .clear}
If your website doesn't have any posts or pages, you may not need a sitemap. But for a blog with several posts, a sitemap is necessary (if you want to rank better in search engines). You can submit your sitemap to major search engines like Google, Bing, Yahoo etc., so that their respective bots crawl your site and index them. Only after indexing, your website link appears in the search results.

Leaving a link to your sitemap inside your website is also a good idea. Let's say someone refers to a post of yours in their well-ranked blog. There are chances that a bot will crawl that link and land on your post. You shouldn't miss a chance of giving the link to your sitemap when the bot is crawling your post! 

[Submit your sitemap to Google](https://www.google.com/webmasters/tools/home?hl=en){:rel='nofollow'}{:target="_blank"} if you already have one. I usually submit my sitemap to Webmaster tools of Google, Bing, and Yahoo. 

I use [SEO-checkup](https://toolbox.seositecheckup.com/apps/seo-checkup){:rel='nofollow'}{:target="_blank"} to check whether my websites comply with common SEO parameters. I found out that I did not have a sitemap by using this app. I will write a detailed post on some useful on-line tools to optimize your website to make perform well and search engine friendly.

## How to create a sitemap for Jekyll blog?

In WordPress, creating a sitemap using a plugin is very easy! What if I tell you that creating a sitemap in Jekyll is much easier! 

Jekyll blogs will not have sitemap by default. You can always generate them using a small snippet of code. Add the below code to your **_config.yml** file. This will create a sitemap for you with the link ```/sitemap.xml```.

{% highlight css %}
gems:
  - jekyll-sitemap
{% endhighlight %}


Here is my [_config.yml](https://raw.githubusercontent.com/sharu725/emerald/gh-pages/_config.yml){:rel='nofollow'} file for reference. You will not be able to see the XML file created for sitemap inside your directory.

{% include adsense-inside-post.html %}

Now, commit the changes and hit the URL ``yourwebsite.com/sitemap.xml``. You should see all your links listed there.

<iframe class="left half video" src="https://www.youtube.com/embed/kiBtQClK-XQ?rel=0" frameborder="0" allowfullscreen></iframe>
Here is a video demonstration



## The hard way to insert sitemap in Jekyll blog!
{: .clear}
You can also list all the links by yourself. Don't worry, we will be using ```ul``` so that it gets and arranges the links  one by one. Create a file in the root of the repository and name it **whatever.xml**. Copy this code inside it

{% highlight html %}---
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    {% raw %}{% for post in site.posts %}{% endraw %}
    <url>
        <loc>{% raw %}{{site.url}}{% endraw %}{% raw %}{{ post.url | remove: 'index.html' }}{% endraw %}</loc>
    </url>
    {% raw %}{% endfor %}{% endraw %}

    {% raw %}{% for page in site.pages %}{% endraw %}
    {% raw %}{% if page.layout != nil %}{% endraw %}
    {% raw %}{% if page.layout != 'feed' %}{% endraw %}
    <url>
        <loc>{% raw %}{{site.url}}{% endraw %}{% raw %}{{ page.url | remove: 'index.html' }}{% endraw %}</loc>
    </url>
    {% raw %}{% endif %}{% endraw %}
    {% raw %}{% endif %}{% endraw %}
    {% raw %}{% endfor %}{% endraw %}
</urlset>
{% endhighlight %}

This is a feed file written in liquid tags. It will look for all the posts and pages you have and list them inside a ``sitemap.xml`` file. It also gets updated upon adding new posts and pages.

In this method, you will have the full control of your sitemap. You can exclude whatever you think is not important and include links that you want it to be in the sitemap.

I hope that helped. If you are having problems with generating a sitemap please leave a comment. I will try to fix it. 

Thanks for reading!