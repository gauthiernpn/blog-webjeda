---
title: Adsense on Subdomain and Adsense on Jekyll
desc: Adsense was successfully implemented on this Jekyll blog only after a deep research on Adsense policies. It is indeed possible to have ads on subdomain but you should know what you are doing. Just placing Adsense ads will not work.
Keywords: adsense on subdomain, adsense on Jekyll
author: sharathdt
tags: Jekyll Adsense
image: adsense-on-subdomain-adsense-on-Jekyll.jpg
layout: post
permalink: /adsense-jekyll-subdomain/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

<a rel="nofollow" target="_blank" href="http://www.freepik.com/free-vector/office-banners_800177.htm">Design by Freepik</a>

I had no hopes on this blog either. But I tried my best to deliver the content that somehow helps someone. Many of my posts are actually the problems I faced while figuring out stuff. I think it worked.
{: .clear}

<div class="clear"></div>   


* Do not remove this line (it will not be displayed) 
{:toc}


## Adsense on subdomain
The first problem I faced was applying for Adsense using a subdomain. My subdomain ```blog.webjeda.com``` cannot be used to applying for Adsense. Google has this policy for a reason. May be you have good content on your subdomain but what if you have bad content in your domain which is non-compliant with Adsense policies. Say some adult content or content related to drugs?

So one thing was sure by the answers on Google Product Forum that **I cannot apply for Adsense with a subdomain**. But I can always apply with the domain name even if it doesn't have much content. For instance my domain [webjeda.com](http://webjeda.com){:target="_blank"} doesn't have many pages. It is actually a single page website meant for my business.

So I applied with my domain ```webjeda.com``` and placed ads on my subdomain(only after placing ads, Google will check your website for compliance). It did not get an approval for days. I thought it doesn't work. Then I read somewhere that I have to put at least one ad in the main domain to get approved.

{% include adsense-inside-post.html %}

I can easily place an ad on ```webjeda.com``` but I was afraid that Google will reject it for having no content. But that was my last hope anyway. There was actually another alternative. Moving the blog to a new domain. I was in no mood to move all my contents in the subdomain to a new domain. That's not just practical.

I decided to place an ad on my domain. And just after a day, while I was browsing my blog ```blog.webjeda.com``` I saw ads showing up. It was showing blank spaces before approval. But after seeing the ads I was really happy that finally something happened!

So follow the guidelines for approval on subdomain

1. **It doesn't matter how much content is present in your domain but it should be compliant with Adsense policies.**

2. **Always apply with your domain name, not subdomain(I don't think you can apply with a subdomain)**

3. **Place at least one ad on your domain along with subdomain.**

4. **Follow all other [Adsense Policies](https://support.google.com/adsense/answer/23921?hl=en){:rel='nofollow'}{:target="_blank"} without miss.**

Once you get the approval, read the below section on how to place Adsense ads on Jekyll blog.

## Adsense on Jekyll blog

Though it is very easy to automatically place ads on all pages and places, I wasn't able to place the ads automatically where I wanted. 

I have placed ads on top and bottom of my blog posts and pages. And one more ad appears somewhere in the middle of all the posts. So how did I do this?

### 1. Get responsive Adsense code
The advantage is that it adopts to all screen-size so that you don't have to add media queries and adjust the width.

### 2. Create html files of Adsense code
Create 3 html files with different names inside ```_includes``` folder(you can place only 3 ads per page. But this is not a hard and fast rule). Copy paste the Adsense code(responsive) that you generated in Adsense. Here is a sample Adsense code for the file. Keeping the script tags inside a ```div``` tag is optional.

{% highlight html %}
<div>
<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- text-resp-top -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-4186856386076933"
     data-ad-slot="5705299846"
     data-ad-format="auto"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>
</div>
{% endhighlight %}

### 3. Call them wherever you need them
These files can be called anywhere inside the layouts, posts and pages using this line
<pre>{% raw %}{% include adsense-file-1.html %}{% endraw %}</pre>

Change ```adsense-file-1``` to whatever the name you have given to your Adsense html.

I have a total of 3 Adsense html files

1. Called inside ```default``` layout at the bottom portion (appears in almost all pages). 

2. Called at the top portion of ```post``` layout .

3. At the top portion of ```page``` layout. Here is how I have used it on ```page``` layout.

{% highlight css %}
---
layout: default
---
<article id="page">
    {% raw %}{% include adsense-file-1.html %}{% endraw %}
  {% raw %}{{ content }}{% endraw %}

</article>
{% endhighlight %}


### 4. Where not to show Adsense code
It is against the Adsense policy to show Adsense ads on 404 page, a blank page or a page which doesn't have much content. So I decided not to include adsense on about, contact, 404 page etc., 

But how? I have defined Adsense files in default, page and post layouts. So any page using any of these layouts would automatically get Adsense ads in it.

Then it hit me. I can add a front matter and write a condition not to include those pages! Here I have added a front matter attribute called ```adallow: 0``` to all those pages in which I don't want my adsense ads to appear.

This is how the front matter in my about page looks like

{% highlight css %}
---
layout: page
title: About
permalink: /about/
adallow: 0
---
{% endhighlight %}

And here is the condition for the adsense code.

{% highlight css %}
  {% raw %}{% if page.adallow != 0 %}{% endraw %}
       {% raw %}{% include adsense-file-1.html %}{% endraw %}  
   {% raw %}{% endif %}{% endraw %}
{% endhighlight %}

The condition says, if the adallow value for a page is not zero then include the adsense code! Pretty clever isn't it?!

So this is how you can include adsense ads on all your present and upcoming Jekyll blog posts and pages automatically. This is a neat approach than pasting codes on every single post and page.

Let me know how you have implemented adsense ads in Jekyll. If there is a better way, I would be happy to implement it.

Thanks for reading!