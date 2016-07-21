---
title: 3 Easy steps to implement Jekyll Collections
desc: Jekyll collections is something that isn't understood by many. For example, a collection of stamps, books, cakes etc. It is very easy to create and organize multiple collections on a Jekyll blog.
keywords: 
author: sharathdt
image: jekyll-collection.svg
tags: Jekyll
permalink: /jekyll-collections/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}
<a class="clear" href="http://www.freepik.com/free-vector/colorful-garget-icons_798073.htm" rel="nofollow" target="_blank">Designed by Freepik</a>

## Why 'collections'?

While blogging you will realize that you have some things that do not fit into the category of posts nor into pages. Here is a comparison between the three.

### Posts:
Chronologically arranged items - generally date wise arrangement.

### Pages:
No particular arrangement or connection between individual items. For example, a **Contact** page has nothing to do with an **About** page and they can be arranged in any manner.

### Collections:
Collections is a set of items which has a certain relation between individual items but may not have a chronological arrangement.


For example, let's consider you have a blog which is about movie reviews. You write your reviews as posts. So for every movie you create a post. Let's say you want to make a list of **Top 25 must watch movies** or **Top 10 scary movies** which will have all the details of each movie. In this case, posts or pages are not a good choice to go with. We can use collections instead. It is a collection of certain kind of movies. You can have any number of collections.

* Do not remove this line (it will not be displayed) 
{:toc}

A better example would be from my own blog. There is a section called [**Themes**](/themes/){:target="_blank"} in the menu bar. I have a collection of themes on that page. If I make new posts for all my themes then it wouldn't make sense. Why would anyone put themes in between tutorials? I can make individual pages for all the themes but how many pages should I make? How should I list those pages? So it had to be a collection.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 717 526.5"><style>.a{fill:none;stroke:#414042;}.b{fill:#00AEEF;}.c{fill:none;stroke-width:5;stroke:#F1F2F2;}.d{fill:none;stroke-width:2;stroke:#808285;}</style><path d="M9.1 515.4V35.8c0-13.7 11.1-24.7 24.7-24.7h650c13.7 0 24.7 11.1 24.7 24.7v479.6" class="a"/><line x1="8.5" y1="514.5" x2="708" y2="514.5" style="fill:none;stroke:#000"/><rect x="34.5" y="61.9" width="648.6" height="426" class="a"/><rect x="34.5" y="61.9" width="648.6" height="118.2" class="b"/><line x1="340.6" y1="102.7" x2="612.7" y2="102.7" class="c"/><line x1="340.6" y1="143.5" x2="542.6" y2="143.5" class="c"/><rect x="228.4" y="28.2" width="453.8" height="19.3" style="fill:none;stroke:#808285"/><rect x="300" y="220.5" width="85.5" height="85.5" class="d"/><rect x="414.4" y="220.5" width="85.5" height="85.5" class="b"/><rect x="528.7" y="220.5" width="85.5" height="85.5" class="d"/><rect x="300" y="327.9" width="85.5" height="85.5" class="b"/><rect x="414.4" y="327.9" width="85.5" height="85.5" class="d"/><rect x="528.7" y="327.9" width="85.5" height="85.5" class="b"/><text transform="matrix(1 0 0 1 87.481 296.8682)"><tspan font-family="sans-serif" font-size="48" class="b">Jekyll </tspan><tspan x="-26.7" y="57.6" font-family="sans-serif" font-size="48" class="b">collection</tspan></text><text transform="matrix(1 0 0 1 74.834 134.3765)" font-family="sans-serif" font-weight="bold" font-size="56" fill="#FFF">WJ</text></svg>
{: .noborder}

<p></p>

## Jekyll collections initial setup
Using Jekyll collections is very easy. The first thing to do is to mention your new collection in your **_config.yml** file. Let's say I want two collections in my Jekyll blog. One is **Themes** where I put all the themes I created and another one is **Designs** where I keep all my designs to show off.

This is how you define collections in _config.yml.
{% highlight yml %}
collections:
    - themes
    - designs
{% endhighlight %}

You can add more metadata if needed

{% highlight yml %}
collections:
    themes:
        output: true
        permalink: /jekyll-themes/:path/
        
    designs:
        output: true
        permalink: /my-designs/:path/
{% endhighlight %}


## Jekyll collection folders
Now at the root of the repository, create two folders(because we mentioned two collections) with the names ``_themes`` and ``_designs``. Underscore is necessary, do not leave it out.

We have to keep our collection inside these folders. Let's keep some files inside ``_themes`` folder. I have created 3 themes so far. I want them to be showed as a collection with certain details. Then I will have to showcase them as a list or a grid.

This is pretty much like how we keep all the posts inside the **_posts** folder and show them via a list on the homepage.

Here is how I have defined individual collection file

{% highlight yml %}{% raw %}
---
title: Purple
layout: page
img: webjeda-purple-jekyll-theme.jpg
description: Webjeda Purple is a minimal theme built on default jekyll theme. It is very light highly customizable. Suitable for minimal blogs.
link: http://webjeda.com/purple/
---

# Features

## Customizable theme
The theme can be customized just by changing few variables in **_config.yml** file.

## Lightweight
Since the theme is based on default Jekyll theme, it is very lightweight. No JavaScript except analytics is used!

[**Preview**]({{page.link}})

{% endraw %}{% endhighlight %}

You can provide any layout you prefer. I'm providing some more data in the YAML front matter since I need them. This one is for the **Purple** theme. Here is another one for the **Thunder** theme.


{% highlight yml %}{% raw %}
---
title: Thunder
layout: page
img: thunder-jekyll-theme.png
description: Thunder is a lightning fast responsive theme based on default Jekyll theme. It is minimal and free from JavaScript. It has a css file of size 5kb. This theme is best suited for minimal blogs. 
link: http://webjeda.com/thunder/
---

# Features

## Customizable theme
The theme can be customized just by changing few variables in **_config.yml** file.

## Inline CSS
Since the style used in this theme is very less, I'm inlining it. This will save a request and hence speeds up website loading.

## Light-weight
Since the theme is based on default Jekyll theme, it is very light-weight. No JavaScript except analytics is used!

[**Preview**]({{page.link}})

{% endraw %}{% endhighlight %}

{% include adsense-inside-post.html %}




## Jekyll collection index

So I have two themes in my Theme collection. How to show them on a page? we have to create an index file. Create a file with the name **themes.md** in the root. 

{% highlight html %}{% raw %}
{% for themes in site.themes %}


<a href="{{ themes.url | prepend: site.baseurl }}">
        <h2>{{ themes.title }}</h2>
</a>

<p class="post-excerpt">{{ themes.description | truncate: 160 }}</p>

{% endfor %}      
{% endraw %}{% endhighlight %}

Above liquid syntax will find all the theme files inside **_themes** folder and list them out along with their title and description. I have also included images in my theme collection using ``{% raw %}{{page.image}}{% endfor %}``. For simplicity, I haven't included it here. This will render a theme list like this.
<div style="border: 1px solid #aaa">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 639.007 213.476" >
<text transform="matrix(1 0 0 1 21.2764 29.0781)"><tspan x="0" y="0" style="fill:#3B97D3; font-family:'Helvetica'; font-size:24;font-weight:bold">Purple</tspan><tspan x="0" y="14.4" style="font-family:'Helvetica'; font-size:12;">Purple is a minimal theme built on default jekyll theme. It is very light highly customizable. Suitable for minimal blogs.</tspan><tspan x="0" y="57.6" style="fill:#3B97D3; font-family:'Helvetica'; font-size:24;font-weight:bold">Sidebar</tspan><tspan x="0" y="72" style="font-family:'Helvetica'; font-size:12;">Webjeda Sidebar is an elegant theme which offers a nice toggleable sidebar. </tspan><tspan x="0" y="86.4" style="font-family:'Helvetica'; font-size:12;">The theme stands out in its features like changable color scheme and pre-installed sharebar, analytics and disqus. </tspan><tspan x="0" y="100.8" style="font-family:'Helvetica'; font-size:12;">It is suitable for all kinds of blogging.</tspan><tspan x="0" y="144" style="fill:#3B97D3; font-family:'Helvetica'; font-size:24;font-weight:bold">Thunder</tspan><tspan x="0" y="158.4" style="font-family:'Helvetica'; font-size:12;">Thunder is a lightning fast responsive theme based on default Jekyll theme. </tspan><tspan x="0" y="172.8" style="font-family:'Helvetica'; font-size:12;">It is minimal and free from JavaScript. It has a css file of size 5kb. This theme is best suited for minimal blogs.</tspan></text></svg>
</div>

<p></p>

By clicking on one of them will open up the theme file we created in the beginning. which will look something like this
<div style="border: 1px solid #aaa">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 380.979"><text xmlns="http://www.w3.org/2000/svg" transform="matrix(1 0 0 1 64.5713 81.3892)"><tspan x="0" y="0" style="font-family:'Helvetica';font-weight:bold; font-size:28;">Features</tspan><tspan x="0" y="43.2" style="font-family:'Helvetica';font-weight: semibold; font-size:24;">Customizable theme</tspan><tspan x="0" y="72" style="font-family:'Helvetica'; font-size:12;">The theme can be customized just by changing few variables in </tspan><tspan x="339.379" y="72" style="font-family:'Helvetica';font-weight:bold; font-size:12;">_config.yml</tspan><tspan x="408.838" y="72" style="font-family:'Helvetica'; font-size:12;"> file.</tspan><tspan x="0" y="115.2" style="font-family:'Helvetica';font-weight: semibold; font-size:24;">Lightweight</tspan><tspan x="0" y="144" style="font-family:'Helvetica'; font-size:12;">Since the theme is based on default Jekyll theme, it is very lightweight. No JavaScript except analytics is used!</tspan><tspan x="0" y="187.2" style="font-family:'Helvetica';font-weight: semibold; font-size:24;">Pre-installed features</tspan><tspan x="0" y="216" style="font-family:'Helvetica'; font-size:12;">Analytics and Disqus are pre-installed in this theme. You can set it up in </tspan><tspan x="383.006" y="216" style="font-family:'Helvetica';font-weight:bold; font-size:12;">_config.yml</tspan><tspan x="452.465" y="216" style="font-family:'Helvetica'; font-size:12;"> file. If left blank, these features will not load!</tspan><tspan x="0" y="244.8" style="fill:#3B97D3; font-family:'Helvetica'; font-weight:semibold; font-size:12;">Demo</tspan></text></svg>
</div>
<p></p>

This is how Jekyll Collections are made. For a real example, take a look my **Themes** section.

Jekyll collections index page: [**Themes**](/jekyll-themes/){:target="_blank"}

An individual item from the collection: [**Thunder**](/jekyll-themes/thunder/){:target="_blank"}


## Conclusion
Try to fit in any content into a post or a page first. If they don't fit in, then think of using collections. Many times a simple list would do the job. Compare your Jekyll blog to a grocery store where things can be segregated into different collections. A collection of fruits, a collection of veggies, collections of beverages etc. Do not create collections for subsets, for example, say exotic fruits. They come under the fruit collection. In such cases use **categories**.

Thanks for reading!