---
title: Add or Edit Jekyll Posts through a Browser
desc: For beginners an easy online editing option is beneficial. Learn how to add posts, edit posts, and other Jekyll files online through prose.io in this tutorial. Also, find out how to upload images using prose.io! This can be really helpful when you are out on a trip and have an urge to write a Jekyll post.
keywords: edit post in Jekyll, edit page in Jekyll, add post in Jekyll
author: sharathdt
tags: Jekyll Web-Design
image: how-to-edit-add-posts-in-jekyll.jpg
layout: post
permalink: /edit-posts-jekyll/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>In my initial days of blogging with Jekyll, I used to edit posts directly inside Github repository. All the posts will be inside ```_posts``` folder. Editing was easy since it was markdown. But the real struggle was to insert images. If the image source is a URL then it was easy but if the image was inside my local computer folder then there was no way uploading it. I did not know [**how to sync files and folders with Github**](http://blog.webjeda.com/how-to-sync-files-folders-with-github){:rel='dofollow'}{:target="_blank"}.
{: .intro}

<a rel="nofollow" target="_blank" href="http://www.freepik.com/free-vector/office-banners_800177.htm">Design by Freepik</a>

## Unable to upload images to Github!
{: .clear}
<div class="note">
   <h3>Update</h3>
    <p>Github finally has a direct upload option where you can upload files and folders just by drag-and-drop! Read <a target="_blank" href="http://blog.webjeda.com/github-upload-file-option/" ><strong>Github Upload Option</strong></a></p>
</div>
As I was unable to upload images to Github I used to upload images to my Google drive, then get the URL of the image and put that as a source in the blog. One of those examples here
[Image from google drive](https://lh3.googleusercontent.com/-j3S-KX7DwQ0/VDi4p2xTzVI/AAAAAAAAAGo/_PP4-udRS4c/s550-no/moto-hint-story-pairit-us.jpg){:rel='nofollow'}{:target="_blank"}.
There is another way to do this by creating an issue on Github where you can drag and drop an image, get the URL and use it as a source. But I doubt its reliability.

<div class="clear"></div>   


* Do not remove this line (it will not be displayed) 
{:toc}



And also, this is not practical. Since you are making a http request, it would take a longer time to load the page. I was not aware of these things. But, that was my workaround for not being able to upload files to Github.


## A nice tool to upload images to Github
![Prose.io jekyll editor screenshot]({{ site.url }}/images/how-to-use-prose-io-with-jekyll.jpg)
{: .right .half}
Eventually I found a tool called [prose.io](http://prose.io){:rel='nofollow'}{:target="_blank"}. It is good, the interface, functionality and even the animations! I wanted something that can upload images to Github. Prose was the Saviour.

I was really impressed with this web app with a feature to upload images. But it will not upload images by default. To make it work, you need to add these lines of code given below inside ```_config.yml```. This will solve the problem of prose.io not uploading images!

<div class="clear"></div>

{% highlight yaml %}

prose:
  rooturl: '_posts'
  siteurl: 'http://prose.github.io/starter/'
  relativeLinks: 'http://prose.github.io/starter/links.jsonp'
  media: 'media'
  ignore:
    - index.md
    - _config.yml
    - /_layouts
    - /_includes
  metadata:
    _posts:
      - name: "layout"
        field:
          element: "hidden"
          value: "blog"
      - name: "tags"
        field:
          element: "multiselect"
          label: "Add Tags"
          placeholder: "Choose Tags"
          options:
            - name: "Apples"
              value: "apples"
            - name: "Bananas"
              value: "bananas"
    _posts/static:
      - name: "layout"
        field:
          element: "hidden"
          value: "page"
      - name: "permalink"
        field:
          element: "text"
          label: "Permalink"
          value: ""
{% endhighlight %}

{% include adsense-inside-post.html %}

![Upload images to github using prose]({{ site.url }}/images/upload-image-to-github-using-prose.jpg)
{: .right .large}
Image upload window on prose.io

Let's say you have a non-jekyll website hosted on Github Pages. Prose.io can be used to edit that as well! But you have to create a ```_prose.yml``` file in the root of your repo and copy paste the same code!

I was happy that I found an option to completely edit my Jekyll posts online. 
{: .clear}
Now in the above snippet, you can change the ```rooturl:``` to any folder you want. I have chosen ```_posts``` because that is the folder I often navigate to edit or add new posts.

## Why prose.io?

Once you figure out [**how to sync files and folders with Github from your local folders**](http://blog.webjeda.com/how-to-sync-files-folders-with-github){:rel='dofollow'}{:target="_blank"}, you will realize that ```prose.io``` is not even required and you may think that you have been following the hard way all this time. But syncing files to Github can be hard for many beginners. Unless you have a little understanding about how ```git``` works, you cannot successfully sync files or at least cannot troubleshoot a simple issue.

This is the reason why I recommend prose.io for beginners. It is simple, easy and GUI!

And also in situations where you are using a Chromebook, there isn't any convenient way to sync Github files locally. Maybe in the future Github will release apps for **Chrome Os** and **Android** but for now there is no option. 

While traveling you may just have a smart-phone or a tablet with you. In such cases you will appreciate **prose.io**!

I'm searching for a reliable Android app that can edit Jekyll posts but had no luck. Let me know if you find one.

Thanks for reading!