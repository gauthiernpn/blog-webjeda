---
title: Grab Images from Jekyll Post
desc: Featured images in WordPress is something I always wanted for my Jekyll blog. I liked how images to show up on the index page automatically. But I had no idea how to fetch images from Jekyll posts. Jekyll post images can be fetched using this tutorial. 
keywords: fetch images from Jekyll post, grab images from Jekyll post, get images from post Jekyll, jekyll post images
author: sharathdt
tags: Jekyll
image: how-to-fetch-images-from-jekyll-post.jpg
layout: post
permalink: /fetch-image-jekyll/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

If you observe this blog's homepage, you'll see that I have used a card-style container to fit in everything. It looks better with a proper shadow. Now my index page grabs the first image(now it uses a different way to fetch images) from my post and shows it in the list along with its title. The best part is that the images are grabbed automatically from every post of my Jekyll blog.
{: .clear}

* Do not remove this line (it will not be displayed) 
{:toc}


## Why fetch an image from Jekyll post?
{: .clear}
I always wanted to have a homepage with a list of posts with their respective images. Just like a WordPress blog page. This seemed almost impossible in Jekyll. But I had hope.

Finally I stumbled across a [stackoverflow answer](http://stackoverflow.com/questions/25463865/in-jekyll-how-do-i-grab-a-posts-first-image){:rel='nofollow'}{:target="_blank"} that helped me achieve this. Now my post index includes tiny images fetched from the particular blog post. So here is how I made this possible.

## How to grab the first image in Jekyll?

Here is the exact code mentioned in the answer. This will just give you a list of all the first images from all your posts. Make sure you do not have any other embedded video or flash(which has ```src``` attribute) file before your first image. This might result in a wrong behavior of the code. It may grab the video or some other file instead of the image.

What I suggest is to have an image at the very beginning of the post like I have in my posts or at least after a paragraph. Make sure it is not too wide or way too tall. I keep most of my featured images in **800x500** ratio. 

{% include adsense-inside-post.html %}

Copy this code to your index page but keep a backup of your index file if the changes you make doesn't work out. Make edits on this code in any way so as to get a list of posts along with **post title**, **published date**, **post image** and **post author**(if you have different authors writing for you). Present them the way you feel like. 

{% highlight html %}
<ul>
  {% raw %}{% for post in site.posts %}{% endraw %}
    <li>
      {% raw %}{% assign foundImage = 0 %}{% endraw %}
      {% raw %}{% assign images = post.content | split:"<img " %}{% endraw %}
      {% raw %}{% for image in images %}{% endraw %}
        {% raw %}{% if image contains 'src' %}{% endraw %}

            {% raw %}{% if foundImage == 0 %}{% endraw %}
                {% raw %}{% assign html = image | split:"/>" | first %}{% endraw %}
                <img {% raw %}{{ html }}{% endraw %} />
                {% raw %}{% assign foundImage = 1 %}{% endraw %}
            {% raw %}{% endif %}{% endraw %}
        {% raw %}{% endif %}{% endraw %}
      {% raw %}{% endfor %}{% endraw %}

      <a href="{% raw %}{{ post.url }}{% endraw %}">{% raw %}{{ post.title }}{% endraw %}</a>
    </li>
  {% raw %}{% endfor %}{% endraw %}
</ul>
{% endhighlight %}

I have made changes to the above code to get a nice index of posts with title, date, image, and description. Here is the raw code that I have used.

{% highlight html %}
<ul id="posts">
    {% raw %}{% for post in paginator.posts %}{% endraw %}
 <a href="{% raw %}{{ post.url }}{% endraw %}">
    <li>
      <div>
        {% raw %}{% assign foundImage = 0 %}{% endraw %}
          {% raw %}{% assign images = post.content | split:"<img " %}{% endraw %}
              {% raw %}{% for image in images %}{% endraw %}
                {% raw %}{% if image contains 'src' %}{% endraw %}
                    {% raw %}{% if foundImage == 0 %}{% endraw %}
                    {% raw %}{% assign html = image | split:"/>" | first %}{% endraw %}
                    <time>{% raw %}{{ post.date | date:"%d %b %Y" }}{% endraw %}</time>
                    <h3>{% raw %}{{ post.title }}{% endraw %}</h3>
                    <hr>
                    <div><img width="250" {% raw %}{{ html }}{% endraw %} />{% raw %}{{ post.desc }}{% endraw %}</div>
                     {% raw %}{% assign foundImage = 1 %}{% endraw %}
                    {% raw %}{% endif %}{% endraw %}
             {% raw %}{% endfor %}{% endraw %}
        </div>
     </li>
 </a>
    {% raw %}{% endif %}{% endraw %} 
    {% raw %}{% endfor %}{% endraw %}
</ul>
{% endhighlight %}

You may have to style it the way you want. I'm not providing the styling details but I hope you can figure that out. You can use w3-css for the card layout. It is also available from Bootstrap and Polymer. You can make your own raised box style by fiddling with box-shadow a little bit.

![How to fetch image from jekyll]({{ site.url }}/images/how-to-grab-image-from-jekyll-post.jpg){: .full}

## Love for Jekyll (no offense WordPress)
This feature gave me a hope that things are indeed possible with Jekyll. I see people migrating from Jekyll to WordPress for certain features. For instance [kanishkkunal](https://codingtips.kanishkkunal.in/jekyll-to-wordpress/){:rel='nofollow'}{:target="_blank"} who writes real good articles on Jekyll moved from Jekyll to WordPress. He has his reasons. But some writers(including myself) find Jekyll to be easier and comfortable than WordPress, for example, Vito Botta. He writes his frustrations in this [article](http://vitobotta.com/migrating-from-wordpress-to-jekyll-part-one-why-i-gave-up-on-wordpress/){:rel='nofollow'}{:target="_blank"} while using WorPress to write posts. I found all the points he made to be true. WordPress post writing interface sucks real bad. There should have been a local editing option.

Writing a post in WordPress itself is a mess. I like to use a text editor like Brackets or Sublime to write my posts. I can always write in an editor and copy paste it to the WordPress editor page but it is not practical. On the bright side, Jekyll supports Markdown. I love it. It's easy and editor-friendly. So I think I'm sticking with Jekyll for a long time. But again it depends on one's priorities. There are not many plugins available for Jekyll.

If you have any feature that you think is only available in WordPress and cannot be implemented in Jekyll, please leave a comment. Maybe there is a solution that you are not aware of.

PS: Let me know if you have successfully implemented fetching images from Jekyll posts on your blog index.

Thanks for reading!