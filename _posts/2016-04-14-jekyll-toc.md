---
title: How to add Table of Contents to Jekyll
desc: Table of contents on Jekyll is easy to implement. TOC provides a quick look at what the article is all about. Also, users can skip to any topic they like just by clicking on it. Learn how to add Table of Contents (TOC) to your Jekyll blog.
keywords: 
author: sharathdt
tags: Jekyll  
image: jekyll-toc.png
permalink: /jekyll-toc/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}


## Why Table of Contents?
{: .clear}
I always liked the Wikipedia **Table of Contents** section which is present in almost every article. It gives a good insight to the whole article with headlines. Imagine, if that was not there; how hard it would be to find things that we specifically looking for. Things like someone's career, early life etc., Here is a [sample page](https://en.wikipedia.org/wiki/Kannada){:rel='nofollow'}{:target="_blank"} wikipedia page.

I have used a similar kind of TOC on my blog. At least it looks similar! So here is the Table of Contents of this blog post.


* Do not remove this line (it will not be displayed) 
{:toc}



Table of Contents for Jekyll blog or any blog for that matter is not really necessary if the article is very short. But, for a long detailed article, a TOC section provides a good insight.

## How to add TOC for Jekyll posts?

There are [plugins](https://jekyllrb.com/docs/plugins/){:rel='nofollow'}{:target="_blank"} for Jekyll to generate TOC but, I have stayed away from them for one reason. I want the complete control on my website.

When I was using WordPress, there was a simple plugin called TOC and it used to work like a charm. It also had some color schemes available for it. But when we are dealing with Jekyll, plugins are very new and can be unstable.


I'm not against Jekyll plugins or something but I'm just waiting for them to be simple to use. 

Now, let's dive in and install TOC.


If you are using kramdown as your markdown processor then you can add the following lines anywhere on the post to add a TOC. Which is pretty simple if you do not want to use JavaScript on your blog 
{% highlight md %}
* Do not remove this line (it will not be displayed)
{:toc}
{% endhighlight %}
You can make it look pretty by adding this style

{% highlight css %}

// Adding 'Contents' headline to the TOC
#markdown-toc::before {
    content: "Contents";
    font-weight: bold;
}


// Using numbers instead of bullets for listing
#markdown-toc ul {
    list-style: decimal;
}

#markdown-toc {
    border: 1px solid #aaa;
    padding: 1.5em;
    list-style: decimal;
    display: inline-block;
}

{% endhighlight %}


But if this doesn't work for you then you can follow the procedure below.


### Step 1: Download necessary files

**Download the zip file:** [jekyll-table-of-contents](https://github.com/ghiculescu/jekyll-table-of-contents/archive/master.zip){:rel='nofollow'}{:target="_blank"}. Thanks to [Alex Ghiculescu](https://github.com/ghiculescu){:rel='nofollow'}{:target="_blank"} for this repository. Don't forget to give a star to this repository if it works for you.

So the repository you just downloaded has a single JavaScript file ```toc.js``` which is enough for creating Table of Contents.

### Step 2: Install the script in Jekyll repository

Place the ```toc.js``` inside your repository somewhere. Maybe inside a folder called **js** where all your scripts are placed.

Now call this JavaScript file where you want the TOC to show up. Usually, all the posts require TOC. So you can call it in the **post layout**. If you want it to be shown on pages then call it on **page layout**. And if you want it everywhere then it is wise to call the file in the **default layout**.

Add this line of code in the layout file you would like the TOC to appear. 
{% highlight html %}
<sript src="/path/to/toc.js"></sript>
{% endhighlight %}

I'm using it only on my posts. So I'm calling it only on the posts layout. This is how it looks like

{% highlight html %}{% raw %}
---
layout: default
---
<sript src="/path/to/toc.js"></sript>
<article class="post">
  <h1 class="post-title note info">{{ page.title }}</h1>
  <time datetime="{{ page.date | date_to_xmlschema }}" class="post-date">{{ page.date | date_to_string }}</time>
  {{ content }}
</article>
{% endraw %}{% endhighlight %}

{% include adsense-inside-post.html %}

### Step 3: Call TOC in the layout.

I personally like calling it in particular places of my articles. So I go into all my posts and paste the below line in certain places. So if you look at my posts, the Table of Contents does not belong to one fixed place. It can be in the first paragraph or second paragraph and so on.

But this is a tedious task if you have a lot of posts. It is better to place the code in the layout itself than individual posts.

Use this line of code in the layout and the TOC will load there.

{% highlight html %}
<div id="toc"></div>
{% endhighlight %}

I'm calling it in my post layout; just above the content.

{% highlight html %}{% raw %}
---
layout: default
---
<sript src="/path/to/toc.js"></sript>
<article class="post">
  <h1 class="post-title note info">{{ page.title }}</h1>
  <time datetime="{{ page.date | date_to_xmlschema }}" class="post-date">{{ page.date | date_to_string }}</time>
  <div id="toc"></div>
  {{ content }}
</article>
{% endraw %}{% endhighlight %}


### Step 4: Initiate TOC

Before initiating Table of Contents, it is logical to wait till all the contents are loaded. Because TOC uses all the headers and it is necessary that all the headers are loaded before the initiation of TOC. So to the post layout, add this snippet of code that waits till the page is completely loaded.

{% highlight html %}
<script type="text/javascript">
$(document).ready(function() {
    $('#toc').toc();
});
</script>
{% endhighlight %}

Here is the complete **post layout** that is ready to load Table of Contents on your Jekyll posts.

{% highlight html %}{% raw %}
---
layout: default
---
<sript src="/path/to/toc.js"></sript>
<article class="post">
  <h1 class="post-title note info">{{ page.title }}</h1>
  <time datetime="{{ page.date | date_to_xmlschema }}" class="post-date">{{ page.date | date_to_string }}</time>
  <div id="toc"></div>
  {{ content }}
</article>

<script type="text/javascript">
$(document).ready(function() {
    $('#toc').toc();
});
</script>

{% endraw %}{% endhighlight %}



This code will call the TOC function once the DOM is ready. After rendering, this is how it will look like

<svg xmlns="http://www.w3.org/2000/svg" width="335.714" height="207.937" viewBox="0 0 335.71 207.94" class="undefined"><style>.a{fill:#FFF;stroke:#58595B;}.b{fill:#58595B;font-family:'Helvetica';font-size:12;}.c{fill:#3B97D3;font-family:'Helvetica';font-size:12;}.d{fill:#3B97D3;font-family:'Helvetica';font-size:12;letter-spacing:33;}.e{font-family:'Helvetica';font-size:15;font-weight:bold}</style><rect width="335.71" height="207.94" class="a"/><text transform="matrix(1 0 0 1 10.9521 52.3813)" class="x"><tspan class="b">    1. </tspan><tspan x="13.05" class="c">    Why Table of Contents?</tspan><tspan x="-2.95" y="21" class="b">    2. </tspan><tspan x="14.05" y="21" class="c">    How to add TOC for Jekyll posts?</tspan><tspan y="42" class="d"/><tspan x="33" y="42" class="b">    1. </tspan><tspan x="49.05" y="42" class="c">    Step 1: Download necessary files</tspan><tspan y="63" class="d"/><tspan x="33" y="63" class="b">    2. </tspan><tspan x="49.05" y="63" class="c">    Step 2: Install the script in Jekyll repo</tspan><tspan y="84" class="d"/><tspan x="33" y="84" class="b">    3. </tspan><tspan x="49.05" y="84" class="c">    Step 3: Call TOC in the layout.</tspan><tspan y="105" class="d"/><tspan x="33" y="105" class="b">    4. </tspan><tspan x="49.05" y="105" class="c">    Step 4: Initiate TOC</tspan><tspan y="126" class="d"/><tspan x="33" y="126" class="b">    5. </tspan><tspan x="49.05" y="126" class="c">    Step 5: Configuration</tspan></text><text transform="matrix(1 0 0 1 41.2378 23.0161)" class="e">    Contents</text></svg>
{: .right .half}
It may not look the same when you first set up TOC but I will give you the styling that I have used for this one which looks like Wikipedia TOC.

{% highlight css %}
div#toc {
    padding: 10px;
    border: 1px solid #aaa;
    display: inline-block !important;
}
{% endhighlight %}
{: .clear}

And also the word **Contents** was actually **Jump to. .** by default. You can change this in the JavaScript file ```toc.js``` between ```<i>``` tag.

{% highlight css %}
title: '<i>Jump to...</i>';
{% endhighlight %}

For some reason, the TOC section assumes the style ```display: block``` which will cover the whole page. But I wanted it on one side of the page. So I have added the code ```display: inline-block!important```. I personally do not like using **!important** but here I had to. It is at least better than in-line CSS!

Now, different markdown handlers process markdown differently. Table of Contents will create an anchor tag for every headline. But this is not supported by all the markdown processors. **Kramdown** is good with it but if you are using **redcarpet** or **rdiscount** you have to make some changes in the **_config.yml** file.


<div class="note">
    <h3>Note</h3>
    <p>I suggest you change the markdown processor to <strong>kramdown</strong> as it is the <a href="https://github.com/blog/2100-github-pages-now-faster-and-simpler-with-jekyll-3-0" target="_blank">only supported markdown engine</a> by github pages.</p>
</div>



**redcarpet**
{% highlight css %}
markdown: redcarpet
redcarpet:
    extensions: [with_toc_data]
{% endhighlight %}


**rdiscount**
{% highlight css %}
markdown: rdiscount
rdiscount:
    extensions:
      - generate_toc
{% endhighlight %}


### Step 5: Configuration
{: .clear}
Table of Contents by default will consider all the headers h1, h2, h3, h4, h5 and h6.

What if you don't want any h4 or h5 displayed? Use this code in place of the one we used in [Step 4](#step-4-initiate-toc).

{% highlight js %}
$('#toc').toc({ headers: 'h1, h2, h3, h6' });
{% endhighlight %}

This code will ensure that only the mentioned headers will be considered for TOC. There are also other things that you can change. If you want to know all the configurations then please visit [this repository](https://github.com/ghiculescu/jekyll-table-of-contents){:rel='nofollow'}{:target="_blank"} and go through instructions given.

I hope that helped you set up TOC on your website. Ask any doubts you have through comments.

Thanks for reading!