---
title: Adding Multiple Author Section to Jekyll Blog
desc: Adding multiple authors to a Jekyll blog was hard. But not anymore. Learn how to add an author box to your Jekyll blog with these easy steps. You can also create a nice author section for your Jekyll blog using this method.
keywords: author box Jekyll, author tab Jekyll, Jekyll author box, Jekyll author section
author: sharathdt
tags: Jekyll
image: author-box-jekyll.png
layout: post
permalink: /author-box-jekyll/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

When I wanted an author section for my blog [Nallikayi Articles](https://articles.nallikayi.com){:target="_blank"}, I thought of differnt ways to make it possible. I had multiple authors. Placing different code for different author was not practical.

I can make a template, add it to every post manually and change author name, image and other details accordingly but it is also not practical if you have too many authors. 

I like how WordPress handles different authors. All you need is to add user. But for Jekyll we still don't have that option. We are doing this the hard way.
{: .clear}


* Do not remove this line (it will not be displayed) 
{:toc}


There should be a provision where you just mention authors name in the post and that should be enough for the post to update itself with particular author details. We are doing just that!

This tutorial explains how to add a multiple author box to Jekyll blog posts step by step.

**Templating**, **configuration file** and **site variables** are the saviors here.

## Step 1: Make an author box

Create a new ```html``` file inside **_includes** folder, name it **author.html** and copy paste the below code.


{% highlight html %}
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.5.0/css/font-awesome.min.css">

<div class="w3-card-2">
  <div id="author-content">
    <h3>Author</h3>
    <hr>
     <div itemprop="author" id="name-author"><strong>{% raw %}{{ author.display_name }}{% endraw %}</strong></div>

     <img itemprop="image" id="image-author" src="{% raw %}{{ author.gravatar }}{% endraw %}">
      <div id="about-author">{% raw %}{{ author.about }}{% endraw %}</div>
      <div id="social-author"> 
            <a href="{% raw %}{{ author.facebook }}{% endraw %}" ><i class="fa fa-facebook-square fa"></i></a>
            <a href="{% raw %}{{ author.twitter }}{% endraw %}" ><i class="fa fa-twitter-square fa"></i></a>
            <a href="{% raw %}{{ author.github }}{% endraw %}" ><i class="fa fa-github-square fa"></i></a>
            <a href="{% raw %}{{ author.email }}{% endraw %}" ><i class="fa fa-envelope-square fa"></i></a>
      </div>
    </div>
</div>
{% endhighlight %}

Design the layout however you want it to be. Make it match to your website layout and color scheme. I'm using font awesme to load icons here. This is a heavy css file. You can omit this if you don't want any icons in the author section. If you are using font awrsome in your Jekyll blog already then you don't have to include this again.

## Step 2: Add authors in configuration file

Now copy below details into your **_config.yml** which is in the root of the repository. Change details accordingly. Here I have mentioned only for two authors - **sharathdt** and **sampaths**. You can use any number of authors. Add details of new authors to this file in this format.

{% highlight yaml %}
authors:
      sharathdt:
        display_name: Sharath Kumar
        about: Sharath is a full-time chess coach, part-time web designer and a hobby blogger. He posts his Web Development blogs in <a href="http://blog.webjeda.com" >Webjeda Blog</a></p>
        email: mailto:info@dxartist.com
        web: http://webjeda.com/
        facebook: https://www.facebook.com/sharu725
        twitter: https://twitter.com/sharathdt
        github: https://github.com/sharu725/
        gravatar: https://s.gravatar.com/avatar/73c67b9ce8685bfb9e906a5865c0aef8?s=80
        
        
        sampaths:
        display_name: Sampath Sirimane
        about: Sampath is a blogger, story and novel writer for a damous daily news paper.
        email: mailto: sirimane@gmail.com
        web: http://samapathsirimane.com
        facebook: https://www.facebook.com/sirimane.sampath
        twitter: https://twitter.com/sirimane
        github: https://github.com/sirimane/
        gravatar: https://raw.githubusercontent.com/sharu725/lanyon/gh-pages/public/img/samapths.jpg        
{% endhighlight %}

## Step 3: Include author section in post layout

Now in your **post** template file, which is inside **_layout** folder add these lines at the end of the post layout as shown in the example below.

 Sample **post layout**
 
{% highlight html %}
---
layout: default
---

<article id="post-page" >
        <h2>{% raw %}{{ page.title }}{% endraw %}</h2>        
        <time datetime="{% raw %}{{ page.date | date_to_xmlschema }}{% endraw %}" class="by-line" >{% raw %}{{ page.date | date_to_string }}{% endraw %}</time>
        <div class="content" >

        {% raw %}{{ content }}{% endraw %}
        
        </div>
    
        {% raw %}{% assign author = site.authors[page.author] %}{% endraw %}
        {% raw %}{% include  author.html %}{% endraw %}
        
        
</article>
 {% endhighlight %}


{% include adsense-inside-post.html %}


## Step 4: Add author name in all posts
Now in all your posts which are inside **_post** folder, you should add a new attribute called author and respective author name that you have used for details in **_config.yml** file.

{% highlight html %}
---
title: Some Title
author: sharathdt
---
{% endhighlight %}

<svg xmlns="http://www.w3.org/2000/svg" width="573" height="204" viewBox="0 0 573 204"><style>.a{font-family:'Helvetica';font-size:20;}.b{fill:#C74244;}.c{fill:#E9C0A7;}.d{fill:#F2D8BC;}.e{fill:none;stroke-width:0.5;stroke:#58595B;}</style><text transform="matrix(1 0 0 1 26.1904 42.8574)" style="font-family:'Helvetica';font-size:20;font-weight:bold">  Author</text><line x1="17.5" y1="63.5" x2="602.4" y2="64.3" fill="none"/><line x1="26.2" y1="60.3" x2="545.9" y2="60.3" style="fill:none;stroke-width:0.8;stroke:#58595B"/><text transform="matrix(1 0 0 1 26.1904 92.0635)" style="font-weight:600" class="a">  Sharath Kumar</text><circle cx="55.1" cy="131.7" r="28.9" fill="#F5A11D"/><path d="M84 131.7c0-16-12.9-28.9-28.9-28.9v57.8C71.1 160.7 84 147.7 84 131.7z" fill="#ED9B21"/><defs><circle cx="55.1" cy="131.7" r="28.9"/></defs><g clip-path="url(#SVGID_2_)"><rect x="51" y="139" width="8.5" height="9.3" fill="#D9A88C"/><path d="M59.4 144h1.4c2.7 0.7 5.6 1.2 7.6 3.5 1.2 1.4 3.3 13.2 3.3 13.2h-5.1H55.2v-10.8 -2.6C57.5 147.3 59.4 145.8 59.4 144z" class="b"/><path d="M50.9 144h-1.4c-2.7 0.7-5.6 1.2-7.6 3.5 -1.2 1.4-3.3 13.2-3.3 13.2h5.1 11.5v-10.8 -2.6C52.8 147.3 50.9 145.8 50.9 144z" class="b"/><path d="M55.2 112.5c4.1 0 10.6 2.3 10.6 13.3 0 6.3-2.1 10.5-3 11.6 -0.8 1.1-5.5 3.3-7.7 3.3C55.2 129.6 55.2 112.5 55.2 112.5z" class="c"/><path d="M67.9 128.4c0.2-1.7-0.7-3.3-1.9-3.5 -1.2-0.2-2.3 1.1-2.5 2.9 -0.2 1.8 0.7 3.3 1.9 3.5C66.6 131.4 67.7 130.1 67.9 128.4z" class="c"/><path d="M55.2 112.5c-4.1 0-10.6 2.3-10.6 13.3 0 6.3 2.1 10.5 3 11.6 0.8 1.1 5.5 3.3 7.7 3.3C55.2 129.6 55.2 112.5 55.2 112.5z" class="d"/><path d="M42.6 128.4c-0.2-1.7 0.7-3.3 1.9-3.5 1.2-0.2 2.3 1.1 2.5 2.9 0.2 1.8-0.7 3.3-1.9 3.5C43.9 131.4 42.7 130.1 42.6 128.4z" class="d"/><path d="M55.2 136.5c1.9 0 3.5-0.6 3.5-1.4h-6.9C51.7 135.9 53.3 136.5 55.2 136.5z" fill="#FFF"/><path d="M63.8 126.6c0.4-1.1 1.3-1.9 2.2-1.7 0 0 0 0 0 0 0.4-1.3 0.6-2.8 0-4.5 -3.1-8.7 0.4-10.3 0.4-10.3s-3.4-0.2-6 2c1.8-2.8 2.6-3.5 2.6-3.5s-3.8-0.8-7.9 3.4c0.9-2.3 2-3.4 2-3.4s-8.5 0.1-11.6 6.2c-1.8 3.5-1.9 7.3-1.5 10.2 0.1 0 0.2-0.1 0.3-0.1 0.4-0.1 0.8 0.1 1.1 0.3 0-1.3 0-2.5 0-2.7 1.6-0.7 3.4-1.6 3.3-5.3 3.8 0 5.9 0 5.9 0h6.1c0 0-0.3 4.1 3 5.1C63.8 124 63.8 125.5 63.8 126.6z" fill="#563929"/><path d="M55.2 148.4c3.1 0 5.7-2 5.7-4.4h-1.5c0 1.8-1.9 3.3-4.2 3.3 -2.3 0-4.2-1.5-4.2-3.3h-1.5C49.5 146.4 52 148.4 55.2 148.4z" fill="#0F958D"/></g><text transform="matrix(1 0 0 1 112.6982 120.6353)"><tspan class="a">  Sharath is a full time chess coach, part time web designer </tspan><tspan x="0" y="20.4" class="a">  and a hobby blogger.</tspan></text><text transform="matrix(1 0 0 1 462.8564 179.8418)"><tspan style="fill:#3058A8;font-size:20">  f     </tspan><tspan x="25.7" style="fill:#1FBDE2;font-size:20">  t     </tspan><tspan y="-2" x="52.1" style="fill:#E02058;font-size:20">  g</tspan></text><circle cx="465.9" cy="173" r="10.9" class="e"/><circle cx="492.2" cy="173" r="10.9" class="e"/><circle cx="520.4" cy="173" r="10.9" class="e"/><path d="M568.3 194.4c0 2.2-1.6 4-3.6 4H9.9c-2 0-3.6-1.8-3.6-4V8c0-2.2 1.6-4 3.6-4H564.7c2 0 3.6 1.8 3.6 4V194.4z" class="e"/></svg>{: .right .large}
Now your post recognizes the author as **sharathdt** and all the details like author name, author image, author about are updated accordingly. Here is how it looks like in my blog posts

Your author box may not be styled as mine but you can style it however you want it to be. I have used w3-css cards for card style.
{: .clear}
Here is how I have styled it

{% highlight css %}
<link rel="stylesheet" href="http://www.w3schools.com/lib/w3.css">

div#author-content {
    width:90%;
    margin:0 auto;
    padding-bottom: 35px;
}

img#image-author {
    margin-left: 0px;
    margin-top: 10px;
    float: left;
}

#social-author {
    float:right;    

}

#im-ab {
    padding-bottom: 2px;
}
{% endhighlight %}

So that is about adding multiple author section for Jekyll blog. Let me know if you were able to successfully implement this in your Jekyll blog or website. 

Also, post the link to your blog in the comment section once you successfully implement this. 

Thanks for reading!
