---
title: Adding Facebook Like Button to Jekyll Blog
desc: Adding facebook button on a Jekyll blog site is different compared to HTML sites. This is because Jekyll blogs have the advantage of including html files which are inside _includes folder. We are taking advantage of this option! 
keywords: facebook like button github pages, like button to Jekyll blog
author: sharathdt
tags: Jekyll SEO
image: adding-facebook-like-button-to-jekyll.png
layout: post
permalink: /facebook-like-button-jekyll/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

Understanding Jekyll is really important to manipulate the options available to handle different things. Usually all Jekyll themes will have a **header** and a **footer** template inside ```_includes``` folder.
{: .clear}

<div class="clear"></div>   


* Do not remove this line (it will not be displayed) 
{:toc}


## Basics before implementation

Most of the Jekyll layouts make use of these templates. If you observe **default** layout inside    the ```_layouts``` folder, you'll see that  at some point they have included header and footer with the following code.

```{% raw %}{% include header.html %}{% endraw %}```
<br />
```{% raw %}{% include footer.html %}{% endraw %}```

This kind of templating can be done with any html file inside ```_includes``` folder. 

A basic Jekyll site structure looks like this. 


{% highlight html %}

.
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
├── .jekyll-metadata
└── index.html

{% endhighlight %}

* A master configuration file ```_config.yml``` and an ```index.html``` in the root.

* Folders such as ```_includes```, ```_layouts``` ```_posts```, ```_sass``` etc.,

I will be explaining the functions of these files and folders in a different post. For now I will be concentrating on ```_includes```.

Just like including header or footer with just a line of code, we can add html files inside ```_includes``` and can spit it out wherever we want it.

## Let's create a like button
For facebook like button, you should have a facebook page for your website or business. If you do not have one then [create a page here](https://www.facebook.com/pages/create/){:rel='nofollow'}{:target="_blank"}.

Once you are done creating a page, go to [facebook like button creator plugin](https://developers.facebook.com/docs/plugins/like-button){:rel='nofollow'}{:target="_blank"}. You may have to create an app if this is your first time fiddling with facebook developer tools. Create an app using **Add a new app** option and select platform **website**.

In the URL input, paste your facebook page URL and select width (this is important while using it on a responsive website), check or uncheck other options based on your requirement and hit **Get code**

![like button to website]({{ site.url }}/images/how-to-add-facebook-like-button-to-jekyll.jpg){: .full}

Now create a html file inside ```_includes```, name it ```fb-like.html``` and copy paste both the codes in it. Save the file.
The code will look somewhat like this

{% highlight html %}
<div id="fb-root"></div>
<script>(function(d, s, id) {
  var js, fjs = d.getElementsByTagName(s)[0];
  if (d.getElementById(id)) return;
  js = d.createElement(s); js.id = id;
  js.src = "//connect.facebook.net/en_US/sdk.js#xfbml=1&version=v2.5&appId=1409800511270506";
  fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));</script>
{% endhighlight %}

{% highlight html %}
<div class="fb-like" data-href="https://developers.facebook.com/docs/plugins/" data-layout="standard" data-action="like" data-show-faces="true" data-share="true"></div>
{% endhighlight %}

{% include adsense-inside-post.html %}

## Include it in your posts
 Now you can call the file ```fb-like.html``` from wherever you like it just by using this line code. 
 <pre>{% raw %}{% include fb-like.html %}{% endraw %}</pre>
 
I usually place it at the bottom of my articles. If you want it on all the posts, you should call this inside posts layout (which will be inside ```_layouts``` folder)
 
Using it on all posts
 
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
    {% raw %}{% include  fb-like.html %}{% endraw %}
     
</article>
 {% endhighlight %}

You can check the like button in my page. I have used the same menthod. But I have added ```defer``` to the script so that the content appears first and only after everything loads, facebook like will appear. This is useful in loading the contents in priority.

{% highlight html %}
<script defer>(function(d, s, id) {
.
.
.
</script>
{% endhighlight %}

Make use of ```defer``` on any ```js``` file you want to load at the end. You can also use ```async``` which loads ```js``` along with ```html```.

Let me know if there is a better way to implement like button in Jekyll. Leave a comment if you are stuck at any step.

Thanks for reading!
