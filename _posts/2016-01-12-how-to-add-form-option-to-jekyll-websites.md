---
title: Create a Contact Form in Jekyll Website
desc: Contact forms in Jekyll should be different from normal php forms because Jekyll doesn't support php. Jekyll blog is static, so we should use forms that work for static sites. Here is a simple form that works on any Jekyll blog.
keywords: form in Jekyll, form in Jekyll blog, form in a static website, formspree
author: sharathdt
tags: Jekyll Web-Design
image: how-to-add-form-option-for-jekyll-websites.jpg
layout: post
permalink: /jekyll-contact-form/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

When I moved one of my blogs from WordPress to Jekyll, I faced a big problem. Which was - how to add a form to Jekyll website which is static?! Generally, the backbone of forms is the ```php``` code which takes the data and sends it to the defined email address. Jekyll being static cannot perform any server side execution. So we cannot use ``php`` for forms.
{: .clear}

<div class="clear"></div>   


* Do not remove this line (it will not be displayed) 
{:toc}


## why use a form?
Form is a way to interact with the users. Providing personal emails and phone numbers can lead to receiving a lot of spam. This is the reason why no famous website includes their personal emain or phone number.

Forms on the other hand are very useful in such cases where you do not want to give out your personal details. It is a better way to interact with users.

Forms can be a contact form, subscription form, sign up form, complaint form, survey form etc., where the user enters some data and that reaches the site owner to make further decisions or conclusion based on the entry.

## Form on Jekyll
There are few solutions to create a form in Jekyll blog.

1. [Formspree](http://formspree.io){:rel='nofollow'}{:target="_blank"}

2. [SimpleForm](https://getsimpleform.com/){:rel='nofollow'}{:target="_blank"}

Formspree has a restriction 1000 entries/month. It is more than enough for a starter like myself. You can choose Gold membership for more entries and gain access to Formspree database.

But, I prefer SimpleForm because one form created in simple form can be used on any page without verification. So to know how to set up simpleform, read: [How to create a form using SimpleForm](/jekyll-subscribe-form/){:target="_blank"}

I'm going to explain the simplest among the two - Formspree. 

## Step 1: Create a form

Let's create a simple form and make it work. I will have only two options for user input - Name and Email. Copy and paste the below form code inside the body tag (or wherever you want the form to be).

Keep [this repository](https://github.com/Redgadget/form/tree/gh-pages){:rel='nofollow'}{:target="_blank"} open. Here I've a simple form created using Formspree.

{% highlight html  %}
<form action="" method="">
    <p>Name: </p><input type="text" name="name"><br />
    <p>Email: </p><input type="email" name="email"><br />
    <input type="submit" value="Send">
</form>
{% endhighlight %}


![Sample Jekyll form]({{ site.url }}/images/form-sample-screenshot.JPG)
{: .right .half}

So the output should look something like this. 

<div class="clear"></div>

{% include adsense-inside-post.html %}



## Step 2: Make it work

If you see the code for the form, **action** and **method** are empty. Formspree suggests you to add an action and method in this format.
{% highlight html %}

<form action="//formspree.io/your@email.com" method="POST">
    <p>Name: </p><input type="text" name="name"><br />
    <p>Email: </p><input type="email" name="email"><br />
    <input type="submit" value="Send">
</form>

{% endhighlight %}

Whenever a user submits his name and email, the data will be sent to ``formspree.io`` website and then formspree sends it back to your email with the details. 

Try to enter something and see if you receive the mail. For the first time, you have to verify your email address. After that, you can receive mails without any hassle.

This is the brief process of making a form in GitHub pages website. What if you want to redirect users to a custom web page once they are done submitting the form on Jekyll blog or GitHub pages website?

## Step 3: Custom thank-you page 
After the submission, users are redirected to a formspree thank you page by default. But if you want it to be your own custom thank you page then you can do so adding this code.

{% highlight html %}
<input type="hidden" name="_next" value="//path/thanks.html" />
{% endhighlight %}

I have a working example here - [nallikayi contact](https://articles.nallikayi.com/contact-us.html){:target="_blank"}. Once you fill all the details you will be redirected to a custom page with a **thank you** message.

Make sure you create a **thank you** page in Github-pages with the name ```thanks.html```. 

## Step 4: Security from bots

If your form is not secure, it may result in receiving spam emails. This is because an email harvester can pick up your email from the form code.

To fool the bots, Formspree has provided an option called ```_gotcha```. This is an input field only visible to bots but not to users. If an entry is made in this invisible field, that means that someone can see through your invisible element! Must be a bot!! This form entry is neglected.

{% highlight html %}
<input type="text" name="_gotcha" style="display:none" />
{% endhighlight %}

## Step 5: Secure your email
When you mention your email in clear text inside your form, email harvesting bots can easily capture it. Which may result in receiving a lot of spam emails. So you can use this code to inject your email. The code will join the strings to a meaningful email address. But bots will not recognize this as an email. 

{% highlight html %}
<form id="formaction" method="POST">
    <p>Name: </p><input type="text" name="name"><br />
    <p>Email: </p><input type="email" name="email"><br />
    <input type="submit" value="Send">
</form>
<script>
    var contactform =  document.getElementById('formaction');
    contactform.setAttribute('action', '//formspree.io/' + 'your' + '@' + 'email' + '.' + 'com');
</script>
{% endhighlight %}

## Step 6: Ultra security 
In step 5, your email cannot be read by a bot but a human can obviously connect the dots and find out the email address. If you are paranoid about giving out your email in any way then use this method.

### Encode the whole form!
Log on to [Enkoder](http://hivelogic.com/enkoder/){:rel='nofollow'}{:target="_blank"} and copy paste your entire Formspree form and hit submit. This tool will encode your data to something like this.

{% highlight html %}
<script type="text/javascript">
//<![CDATA[
<!--
var x="function f(x,y){var i,o=\"\",l=x.length;for(i=0;i<l;i++){if(i>(69+y))" +
"y*=2;y%=127;o+=String.fromCharCode(x.charCodeAt(i)^(y++));}return o;}f(\"#3" +
")+=#$\\\"m(g(x)%5'v>t6gy~q13]\\031L\\017\\001\\013\\001\\023\\000E\\006V\\0" +
"03\\001U\\030\\030\\030\\036\\026\\\\\\rX\\024\\020\\030\\0108\\023\\031\\0" +
"33Au*o+45.)4>3%vz}ijj8)m-{3$v a~\\177kCI\\nF\\r^[ZNFX\\003E\\020B\\002\\001" +
"\\n[\\r\\t\\005\\r^\\025\\024\\023@S\\026\\003Gn\\\"*\\\"6\\0042o!`q6>(::\\" +
"\"?r<z+-(slq13IZ\\037\\005LGOU]E6I + 2!=F@D)*EHI&'LMN\\\\^6?.b\\\"BR3>.b" +
"\\\"615>BbJYF?>.\\016\\\"\\\\pZR)\\016N\\\\^4L-\\016N\\\\^e67\\tE/zs`Bb_=<6" +
"*=SL22ZRn\\027E3?n=-\\013T*|gn)\\rN\\\\^0=.b\\\"SbOh)\\016N\\\\^1<.b\\\"706" +
"RBz)036RBL\\\"\\\\24>Bb\\023\\\\^ZRXq>IvZRh\\nL0^ZCTy5426RB\\017N0^ZpSw\\00" +
"0sz8I9B\\026n`3nx\\\\I73ZRg\\rN}!1$-Z\\020gjG3l\\003^^_ZRBbK22ZR8\\rO0^Z*Wg" +
"+626RB\\017L0^Z@QlM336RB\\016N0^Z|BbK02ZRV\\013+226RB\\rO0^Z:.\\016\\\"\\\\" +
"lZR]~C406RB\\031E)|1>.b\\\"g>. B\\034\\\"\\\\w&(B\\034\\\"\\\\=?}n\\003\\03" +
"5whu#4\\031M12ZRd\\r\\000ab1=.b\\\"616RBm\\036Id1>.b\\\"216RBU\\034fye>,\\0" +
"16\\\"\\\\otRBu?EZHIjb\\\"n^ZuUt9r^Z@V\\177\\014{_haiQE}{&gqD\\010wmt<,\\01" +
"6\\\"\\\\75>Bb(XU)B/\\016N\\\\^4>.b\\\"226RB\\013M0^Z:.\\016\\\"\\\\66>Bb=4" +
"36RB\\023L=gss#\\003T9^$RB\\005Nk5)TNp$XSZ,6X\\003;m&`lK\\nep{57\\027U+{.P7" +
"WVtCcjq}\\014aje f\\026\\033dmE|\\177V=mmth0Y\\020ipr]#\\025\\021;54?#\\033" +
"\\007;)-w7\\014K<k.hwEW+)o5r\\002\\027;2;g6L\\021f9nzyP\\033l,~3r\\022\\\"\\"+
"\"^$3q\\022\\027 pgxe\\027\\007,z.h>P\\021ive`kX\\\\)\",69)"                 ;
while(x=eval(x));
//-->
//]]>
</script>
{% endhighlight %}

You don't recognize anything. Do you?

It is actually

{% highlight html %}
<form action="//formspree.io/your@email.com" method="POST">
    <p>Name: </p><input type="text" name="name"><br />
    <p>Email: </p><input type="email" name="email"><br />
    <input type="submit" value="Send">
</form>
{% endhighlight %}


This works like a charm. You are not only cheating bots but also human email harvesters. It is not impossible to decode this but it is hard!

## Things to keep in mind

Be careful not to include your personal email in form action as it is easily visible when website source is viewed. You can include an alternative email which forwards emails to your personal email. 

Also, I don't recommend using formspree if you are asking your users for any sensitive data because a copy of it is saved in the formspree database. But for general non-sensitive data submission, formspree works like a charm.

<iframe itemscope="" itemprop="video" class="right half video" src="https://www.youtube.com/embed/IP6HsgwQkvs?rel=0" frameborder="0" allowfullscreen></iframe>

Here is a video demonstration on how to set up formspree form on static websites. Don't forget to leave the link of your website with newly created form, in the comment section.

Thanks for reading!
{: .clear}