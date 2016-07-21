---
title: Why did I choose Jekyll over WordPress?!
desc: Jekyll will be taking over a significant share among blogging platforms. I chose a simple static CMS - Jekyll over world's most famous CMS - WordPress! There are reasons why I made this choice and I have tried to put them before you.
author: sharathdt
tags: Jekyll
image: why-jekyll-over-wordpress.png
layout: post
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

<a target="_blank" rel="nofollow" href='http://www.freepik.com/free-vector/fist-coming-out-of-cracked-ground_720279.htm'>Designed by Freepik</a>

A long time ago I had few blogs that were running on WordPress. I bought domain names and a reliable hosting space to keep them running. WordPress blog is very easy to set up. There are thousands of themes and plugins for all kinds of looks and functionalities.

**But, what's wrong?**

# WordPress

## 1. Heavy!
WordPress is heavy. By saying heavy what I mean is it has a lot of code in it. Even a minimal WordPress blog will have too much code. Take a minimal theme from WordPress and compare it with my theme [Thunder](http://webjeda.com/thunder/) or any Jekyll theme. You will observe a significant difference in size.

* Do not remove this line (it will not be displayed) 
{:toc}


## 2. Slow
This is the by-product of being heavy. More the code slower the website. WordPress has some framework that makes it light and fast but doesn't come anywhere close to Jekyll's simplicity.


## 3. Difficulty in writing Posts
If you have written posts on WordPress then you know what I'm talking about. It almost always is online. There are offline apps to write blogs but then you will have to test it online. It is not a big deal. Actually, WordPress has image drag and drop option which os so much easier than Jekyll. But Jekyll stands out because of Markdown support by default. Editing in markdown is addictive!

## 4. Hosting cost
WordPress needs a hosting which supports ``php`` and ``mySQL``. So, it is comparatively costly to host. Jekyll being static can be hosted for cheap on static file hosting providers or for free on Github!

## 5. Design restrictions
This is actually the key reason to migrate from WordPress. WordPress has a lot of themes and plugins to choose from but if you want to change something, say you want the logo to be some pixels down then it becomes a hassle.

---
<p></p>

**What's so good about Jekyll?**

# Jekyll is

## 1. Simple
Jekyll has no database! Jekyll runs nothing in the server. It just keeps files ready to be served. Jekyll is really simple once you understand the basic structure and functions. It supports markdown for posts and pages. It uses the famous **Liquid Syntax** for condition logic and other functionalities which are human readable way of coding! I think this way of coding is very comprehensive even to a non-coder.


## 2. Light, fast and secure
Since Jekyll is light by default, it is fast. The community is growing and creating many Jekyll themes and plugins. Since it is a static site, it is almost unhackable!

## 3. You are in control!
You are responsible for even a single extra space added to the code! So you have the complete control of the website or blog. This also means that you can easily minify, compress all the assets as you like.

{% include adsense-inside-post.html %}

Eventually, I switched all my blogs to Jekyll and I always have a local copy of my blog which wasn't easy to have in WordPress. I'm pretty happy with the performance of my blogs. They do not earn much but I'm the designer for all of them.

You don't have to worry about the design part. There are hundreds of themes already available. You can subscribe to my blog to get a detailed list of free responsive Jekyll themes and their links. 

# Start here
Usually, Jekyll is hosted on github pages but you can also host it on any conventional hosting service. But one thing you observe is that, all the Jekyll themes are put in a github repository. So you should know how to fork(copy) them to your own account. To do that, you should have a github account. So [sign up for a free account](https://github.com/join?source=header-home){: target="_blank" rel="nofollow"}.

Once that is done, you have to find a nice theme for your blog. So do some research or [sign up here](http://eepurl.com/bZdvSP){: target="_blank"} to get a quick checklist. You can also checkout themes section in my blog. Now you should visit the theme's homepage. Here is a video to guide you.

<iframe class="video" src="https://www.youtube.com/embed/T2nx6tj-ZH4?rel=0" frameborder="0" allowfullscreen></iframe>

## Understand baseurl
Now you have the theme file hosted on some URL. You can make changes to this by editing most of the files in the repository. But you should be careful while editing **_config.yml**. Many beginners edit the ``baseurl:`` to something and get 404 error!

To avoid this, you should understand why is it used. Baseurl is the base of your repository where the files are located. If your repository name is ``jekyll-blog`` then your baseurl is ``/jekyll-blog``.

## Understand Jekyll file structure
If you observe the forked repository, it will have some folders with names starting with an underscore. These folders are meant for certain things. For example ``_posts`` is where all the posts should reside.

Read [Layman's Guide to Jekyll](http://blog.webjeda.com/jekyll-guide/){: target="_blank"} for a good insight.

## Write more posts
Jekyll offers markdown support. So you can edit your blog posts in markdown and Jekyll will convert it into html. You can use prose.io to write your posts on the go, even from a smartphone. Read [How to edit or add Jekyll posts through Browser using Prose](http://blog.webjeda.com/edit-posts-jekyll/){: target="_blank"}.

## Use a custom domain name for your blog
Your blog may be hosted with a URL ``http://username.github.io`` which is a third party domain. If you want to use your own domain name then read [How to add a custom domain name to Jekyll blog](http://blog.webjeda.com/custom-domain-github/){: target="_blank"}. Though the procedure is for github pages, the same thing applies to Jekyll blog.



## Create a contact form for your Jekyll blog
Beginners try php forms inside Jekyll and see that it doesn't work. It doesn't because Jekyll doesn't execute code on the server. So restrain yourself from using ``php``. Since Jekyll blog is a static site, you should use something that works on a static website. Read [How to create a contact form in Jekyll](http://blog.webjeda.com/jekyll-contact-form/){: target="_blank"}.

## Create a subscribe form for your Jekyll blog
Maintaining a mailing list is good for initial traffic. Mailchimp forms can be used inside Jekyll. I hope even Aweber forms can be used in Jekyll (I haven't tried Aweber). Read [How to create a mailchimp subscribe form in Jekyll](http://blog.webjeda.com/jekyll-subscribe-form/){: target="_blank"}.

{% include adsense-inside-post.html %}

## Make your blog super fast!
Faster websites keep users happy. Your blog is already fast because you are using Jekyll but you may have too many things loading up or have heavy media files. For a fast Jekyll blog read [How to speed up Jekyll blog](http://blog.webjeda.com/jekyll-speed/){: target="_blank"}.

## Optimize Jekyll blog for SEO
Now your blog is ready to rock. But let's find some organic traffic. Read [How to optimize Jekyll blog for SEO](http://blog.webjeda.com/optimize-jekyll-seo/){: target="_blank"}.

## Secure your Jekyll blog with https
Using SSL on Jekyll blog will improve your search engine ranking! It also keeps users session safe. Read [How to get SSL certificate for Jekyll](http://blog.webjeda.com/jekyll-ssl/){: target="_blank"}.

## Conclusion
There are 100 other things you can do using Jekyll but for a beginner, the above tasks are enough to tackle for a while. I don't think I will ever go back to WordPress. But I still suggest WordPress for non-technical people who do not want to touch a single line of code. Try Jekyll at least for fun and let me know how you felt.

I may have missed points about WordPress and Jekyll regarding their advantages and disadvantages. Let me know what is missing so that I can add to the list. 

Thanks for reading!