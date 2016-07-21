---
title: 3 Simple steps to setup Jekyll Categories and Tags
desc: I have implemented categories in my Jekyll blog without using any plugin. You can implement Jekyll categories on your website by following these simple steps. 
keywords: 
author: sharathdt
image: jekyll-categories.png
tags: Jekyll
permalink: /jekyll-categories/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

<a target="_blank" rel="nofollow" href="http://www.freepik.com/free-vector/black-friday-tags-collection_821735.htm">Designed by Freepik</a>

## Why Jekyll Categories or Tags?
Imagine you have a blog where you discuss very different things all together. Many bloggers post their personal experiences along with some professional posts. Curating information is very important to make users browse through your website with ease. What if New York Times had no categories like **Politics**, **Business**, **Tech** etc..? How hard would it be to track what happened to last night's football game? There should be a **Sports** category to make readers' life easy.

One more thing I want to clear right away is that tags are nothing but categories in Jekyll. And if you want your post links to be ``/category/title/`` or ``/tag/title/`` then you can do that in **_config.yml** file by using this line
{% highlight html %}
permalink: /:categories/:title/
{% endhighlight %}


* Do not remove this line (it will not be displayed) 
{:toc}

## How to implement Jekyll Categories?
Before implementing Jekyll categories, see if your content can be divided into certain domains. For example on my blog, I have sorted my posts into **Jekyll**, **Web-Desing**, **Github**, etc. You will see the category under the title of my blog posts. On clicking them, you will be redirected to a [tags page](/tags/) where all blog posts are categorized under certain topics. One post may contain more than one category if it is dealing with more than one topic.


{% include adsense-inside-post.html %}

Let's see how we can implement it.

### Add Jekyll Categories to Front matter
This is the first step in any method to implement Jekyll Categories or Jekyll Tags. Decide what categories you want. It is better to have fewer categories. As shown in the example below, add ``categories:`` front matter to all the posts according to their content.


Post 1:

{% highlight html %}
---
layout: post
title: My ways to live life.
categories: Personal
---
{% endhighlight %}


Post 2:

{% highlight html %}
---
layout: post
title: Top innovations in technology.
categories: Tech
---
{% endhighlight %}


Post 3:

{% highlight html %}
---
layout: post
title: New tech to organize your daily tasks.
categories: [Tech, Personal]
---
{% endhighlight %}

Let's imagine there are 3 posts in your blog. One is personal, one is tech and another is a mixed post. Here you can organize them into two categories - **personal** and **tech**. Now, add these categories to all the posts.

<div class="note">
    <h3>Categories count</h3>
    <p>
    Though you can add as many categories as you like, I recommend not to exceed 10. Too much of anything is bad.
    </p>
</div>

Once that is done, create a page to display them.

### Create a Category page
This is the page which will be shown when someone clicks on any category. Something like my [jekyll tags](/tags/) page. Copy below code and paste it into a new file and name it **categories.html**.

{% highlight html %}{% raw %}
---
layout: page
permalink: /categories/
title: Categories
---


<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>
    
    <h3 class="category-head">{{ category_name }}</h3>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>

{% endraw %}{% endhighlight %}



<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 717 526.5"><style>.a{fill:none;stroke:#414042;}.b{fill:none;stroke:#000;}.c{fill:#00AEEF;}.d{fill:none;stroke-width:5;stroke:#F1F2F2;}.e{fill:none;stroke:#808285;}.f{fill:#FFF;}</style><metadata class="undefined"><sfw xmlns="http://ns.adobe.com/SaveForWeb/1.0/" class="undefined"><sliceSourceBounds width="700.5" height="504.8" y="-1.7" x="49.6" bottomLeftOrigin="true" class="undefined"/></sfw></metadata><path d="M9.1 515.4V35.8c0-13.7 11.1-24.7 24.7-24.7H683.8c13.7 0 24.7 11.1 24.7 24.7V515.4" class="a"/><line x1="8.5" y1="514.5" x2="708" y2="514.5" class="b"/><rect x="34.5" y="61.9" width="648.6" height="426" class="a"/><rect x="34.5" y="61.9" width="648.6" height="118.2" class="c"/><line x1="340.6" y1="102.7" x2="612.7" y2="102.7" class="d"/><line x1="340.6" y1="143.5" x2="542.6" y2="143.5" class="d"/><rect x="228.4" y="28.2" width="453.8" height="19.3" class="e"/><text transform="matrix(1 0 0 1 50.9819 243.7363)" class="undefined"><tspan font-family="'Helvetica'" font-size="12" letter-spacing="33" class="c"/><tspan x="36" font-family="'Helvetica'" font-weight="bold" font-size="36" class="c">  Categories</tspan></text><text transform="matrix(1 0 0 1 136.9819 307.7363)" class="undefined"><tspan font-family="'Helvetica'" font-size="21" class="undefined">  Personal</tspan><tspan y="16.8" font-family="'Helvetica'" font-size="14" font-weight="bold" letter-spacing="33" class="undefined"/><tspan x="36" y="16.8" font-family="'Helvetica'" font-size="14" class="c">  My ways to live life.</tspan><tspan y="33.6" font-family="'Helvetica'" font-size="14" letter-spacing="33" class="c"/><tspan x="36" y="33.6" font-family="'Helvetica'" font-size="14" class="c">  New tech to organize your daily tasks.</tspan></text><text transform="matrix(1 0 0 1 136.9819 383.7363)" class="undefined"><tspan font-family="'Helvetica'" font-size="21" class="undefined">  Tech</tspan><tspan y="16.8" font-family="'Helvetica'" font-size="14" font-weight="bold" letter-spacing="33" class="undefined"/><tspan x="36" y="16.8" font-family="'Helvetica'" font-size="14" class="c">  Top innovations in technology.</tspan><tspan y="33.6" font-family="'Helvetica'" font-size="14" letter-spacing="33" class="c"/><tspan x="36" y="33.6" font-family="'Helvetica'" font-size="14" class="c">  New tech to organize your daily tasks.</tspan></text><text transform="matrix(1 0 0 1 74.9819 143.46)" font-family="'Helvetica'" font-size="72" font-weight="bold" class="f">  WJ</text></svg>
{: .half .right}

The page will look like this. It will have all the categories listed out. One article can be listed in many categories. This happens when you use more than one category for a post.


If you want a simple list of all posts inside a certain category then use the below code. A better example for this would be [this website](http://danhixon.github.io/code.html){: target="_blank" rel="nofollow"}.
{: .clear}

**Personal**
{% highlight html %}{% raw %}

{% for post in site.categories.Personal %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}

{% endraw %}{% endhighlight %}


**Tech**
{% highlight html %}{% raw %}

{% for post in site.categories.Tech %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}

{% endraw %}{% endhighlight %}


### Display categories on Jekyll posts.


![jekyll categories in post](/images/jekyll-categories-in-post.svg){: .noborder}
{: .half .right }

It is better to show the categories to which the current article belongs to. And upon clicking any of the categories, users should land on the page we created in the previous step.


This can be done with the following liquid syntax. Copy this to **post layout** wherever you want to show the categories.


{% highlight html %}{% raw %}
<div class="post-categories">
  {% if post %}
    {% assign categories = post.categories %}
  {% else %}
    {% assign categories = page.categories %}
  {% endif %}
  {% for category in categories %}
  <a href="{{site.baseurl}}/categories/#{{category|slugize}}">{{category}}</a>
  {% unless forloop.last %}&nbsp;{% endunless %}
  {% endfor %}
</div>
{% endraw %}{% endhighlight %}
{: .clear}

This is how we can implement categories. If we want tags instead of categories then we should replace **category** with **tag** and **categories** with **tags** everywhere.


{% include adsense-inside-post.html %}

## Conclusion
It is good to categorize items if there is a lot of content on varying topics. But if the content is just on one subject then there is no need to categorize it. Using category slug in the URL helps users to figure out what they will encounter on opening the link. Use Jekyll Categories where you think is necessary.

Let me know if this method worked out for you. Leave any suggestions in the comment section.