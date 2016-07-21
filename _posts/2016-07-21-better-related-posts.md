---
title: Better Jekyll Related Posts
desc: Jekyll related posts only shows recent posts by default. There is a better way to do this where we can filter posts with similar topics. This method will ensure that related posts are actually related.
author: sharathdt
tags: Jekyll
image: jekyll-related-posts.png
layout: post
permalink: /jekyll-related-posts/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

<a target="_blank" rel="nofollow" href='http://www.freepik.com/free-vector/cartoon-dinosaurs-pack_874040.htm'>Designed by Freepik</a>


## Why should we use Related Posts?
If you have a lot of great content on your website and you want it easier for your users to see it then you should use **related posts**. A viewer landing on one of your posts may be hungry for a similar type of information. You should have an easy way for them to browse around. This is where related posts come into the picture. Related posts are those articles which are related to the current article. They are usually at the bottom of the post.

* Do not remove this line (it will not be displayed) 
{:toc}

## What's wrong with Jekyll **related_posts** ?
As I have discussed in my [earlier post](/related-post-jekyll/){: target="_blank"} ``site.related_posts`` should be called ``site.recent_posts`` because it just shows 10 recent posts. Your recent posts can be on a different category but, this variable doesn't recognize that. I was looking for a better way to solve this issue. 

A possible solution was to look for posts with matching category or tag. This will make sure the related posts are actually related. To make it even better we are comparing more categories or tags. If they match then those posts will show up.

{% include adsense-inside-post.html %}

## Pre-requisites
Assigning categories or tags is the first step in using this method of extracting related posts. You should categorize all your posts into few topics. If you are not sure how to use tags or categories then please refer to [How to use Jekyll categories](/jekyll-categories/){: target="_blank"}. Proceed to other next only after this.


## How to implement a better Jekyll Related Posts?

Use the below liquid syntax code to get 4 related posts. You can change many parameters here. I picked it up from a [post on stackoverflow](http://stackoverflow.com/questions/25348389/jekyll-and-liquid-show-related-posts-by-amount-of-equal-tags-2){: target="_blank" rel="nofollow"}. This works if you are using **tags**. 

{% highlight html %}{% raw %}
<div class="relatedPosts">

<h4>You May Also Enjoy</h4> 

{% assign maxRelated = 4 %}
{% assign minCommonTags =  2 %}
{% assign maxRelatedCounter = 0 %}

  {% for post in site.posts %}

    {% assign sameTagCount = 0 %}
    {% assign commonTags = '' %}

    {% for tag in post.tags %}
      {% if post.url != page.url %}
        {% if page.tags contains tag %}
          {% assign sameTagCount = sameTagCount | plus: 1 %}
          {% capture tagmarkup %} <span class="label label-default">{{ tag }}</span> {% endcapture %}
          {% assign commonTags = commonTags | append: tagmarkup %}
        {% endif %}
      {% endif %}
    {% endfor %}

    {% if sameTagCount >= minCommonTags %}
      <div>
      <h5><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}{{ commonTags }}</a></h5>
      </div>
      {% assign maxRelatedCounter = maxRelatedCounter | plus: 1 %}
      {% if maxRelatedCounter >= maxRelated %}
        {% break %}
      {% endif %}
    {% endif %}

  {% endfor %}

</div>
{% endraw %}{% endhighlight %}


If you are using **categories** then use the code below.

{% highlight html %}{% raw %}
<div class="relatedPosts">

<h4>You May Also Enjoy</h4> 
  
{% assign maxRelated = 4 %}
{% assign minCommonTags =  2 %}
{% assign maxRelatedCounter = 0 %}

{% for post in site.posts %}

    {% assign sameTagCount = 0 %}
    {% assign commonTags = '' %}

    {% for category in post.categories %}
      {% if post.url != page.url %}
        {% if page.categories contains category %}
          {% assign sameTagCount = sameTagCount | plus: 1 %}
          {% capture tagmarkup %} <span class="label label-default">{{ category }}</span> {% endcapture %}
          {% assign commonTags = commonTags | append: tagmarkup %}
        {% endif %}
      {% endif %}
    {% endfor %}

    {% if sameTagCount >= minCommonTags %}
      <div>
      <h5><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}{{ commonTags }}</a></h5>
      </div>
      {% assign maxRelatedCounter = maxRelatedCounter | plus: 1 %}
      {% if maxRelatedCounter >= maxRelated %}
        {% break %}
      {% endif %}
    {% endif %}

  {% endfor %}

</div>
{% endraw %}{% endhighlight %}

## Brief explaination of the code
``{% raw %}{% assign maxRelated = 4 %}{% endraw %}`` - Maximum number of related posts that will be shown in the output.

``{% raw %}{% assign minCommonTags =  2 %}{% endraw %}`` - Minimum number of tags or categories that should be equal to be considered as related. In this case, at least 2 tags or categories should match with the current post to be considered as related.

``{% raw %}{% if post.url != page.url %}{% endraw %}`` - Current post will not be shown in the related posts output

The code basically compares the current posts' tags or categories with other posts. If the ``minCommonTags`` is satisfied then it will show such posts in the output.

If our post has tags ``Jekyll`` ``Github`` and ``Web-Design`` then the code looks for all the posts with at least two common tags. Which means posts with tags ``Jekyll`` and ``Github`` are candidates, ones with ``Github`` and ``Web-Design`` are candidates, ones with ``Jekyll`` and ``Web-Design`` are candidate and ones with all three tags are also candidates.

If there are more than ``maxRelated`` posts are available then only the recent ones are considered. 

{% include adsense-inside-post.html %}

## How to increase the accuracy of Jekyll Related Posts?
``minCommonTags`` is directly proportional to the relation between posts. If posts have more common tags then they must be related isn't it? This code uses the same logic. You can increase this number to get highly targeted related posts but sometimes you may get no output. 

Use this variable carefully so that for every post you get some output. I have given it a value ``1`` because at this point I don't have too much content on my website and I use less number of tags.

## Jekyll Related Posts for collections
If you are new to collections then please refer to [3 Easy steps to implement Jekyll Collections](/jekyll-collections/){: target="_blank"}. In my blog, I have a [theme collection](/jekyll-themes/){: target="_blank"}. I wanted related posts(themes) on that as well.

Here is the code I have used. This may change according to your collection.

{% highlight html %}{% raw %}
<h4>You May Also Enjoy</h4> 
{% if page.url contains 'jekyll-themes' %}
<div class="relatedPosts">

    {% assign maxRelated = 4 %}
    {% assign minCommonTags =  1 %}
    {% assign maxRelatedCounter = 0 %}

    {% for jekyll-themes in site.jekyll-themes %}

    {% assign sameTagCount = 0 %}
    {% assign commonTags = '' %}

    {% for tag in jekyll-themes.tags %}
      {% if jekyll-themes.url != page.url %}
        {% if page.tags contains tag %}
          {% assign sameTagCount = sameTagCount | plus: 1 %}
          {% capture tagmarkup %} <span class="label label-default">{{ tag }}</span> {% endcapture %}
          {% assign commonTags = commonTags | append: tagmarkup %}
        {% endif %}
      {% endif %}
    {% endfor %}

    {% if sameTagCount >= minCommonTags %}
      <div>
      <h5><a href="{{ site.baseurl }}{{ jekyll-themes.url }}">{{ jekyll-themes.title }}{{ commonTags }}</a></h5>
      </div>
      {% assign maxRelatedCounter = maxRelatedCounter | plus: 1 %}
      {% if maxRelatedCounter >= maxRelated %}
        {% break %}
      {% endif %}
    {% endif %}

 {% endfor %}

</div>
  
{% else %}

//Related posts code for usual posts
{% endif %}
{% endraw %}{% endhighlight %}

## How I have implemented Related Posts?
I have implemented the same method but with the value of variable ``minCommonTags`` is 1. I'm showing 4 posts at the bottom of every post along with thumbnails. Here is the verbatim code I'm using.

{% highlight html %}{% raw %}
<div class="rect">

  {% assign maxRelated = 4 %}
  {% assign minCommonTags =  1 %}
  {% assign maxRelatedCounter = 0 %}

 
  {% for post in site.posts %}

   
    {% assign sameTagCount = 0 %}
    {% assign commonTags = '' %}

    {% for tag in post.tags %}
      {% if post.url != page.url %}
        {% if page.tags contains tag %}
          {% assign sameTagCount = sameTagCount | plus: 1 %}
          {% capture tagmarkup %} <span class="label label-default">{{ tag }}</span> {% endcapture %}
          {% assign commonTags = commonTags | append: tagmarkup %}
        {% endif %}
      {% endif %}
    {% endfor %}

    {% if sameTagCount >= minCommonTags %}
    
          <a href="{{ site.baseurl }}{{ post.url }}">
              <div class="rel">
                  <h5>{{ post.title }}</h5>
                  <img width="100%" src="/thumbs-small/{{post.image}}">
              </div>
          </a>

      {% assign maxRelatedCounter = maxRelatedCounter | plus: 1 %}
      {% if maxRelatedCounter >= maxRelated %}
        {% break %}
      {% endif %}
    {% endif %}
  {% endfor %}
</div>
{% endraw %}{% endhighlight %}

I'm using some CSS to give it a nice look.
{% highlight css %}

.rect {
    border-top: 3px solid #333;
    border-bottom: 3px solid #333;
    padding-top: 15px;
    margin:0 auto;
}

.rel {
    width: 200px;
    display: inline-block;
    padding: 5px;
    opacity: 0.8;
    &:hover{
        opacity: 1;    
    }

}

{% endhighlight %}

Here is a screenshot of the same
![collection jekyll related posts](/images/better-jekyll-related-posts.PNG){: .full}

## Conclusion
Even though Jekyll did not provide a simple variable to fetch related content, the community has found some ways to overcome that. Do implement this instead of simple ``related_posts`` because the links should be related to the content of the current post. 

Let me know if you are facing issues while implementing this. Leave any suggestions in the comment section.

Thanks for reading!