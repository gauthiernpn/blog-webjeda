---
title: Sync Files and Folders with Github Pages
desc: Uploading files and folders to github repo was hard. Now, with this method you can sync files and folders to a github repository efficiently. In this tutorial I'm uploading a complete website into Github Pages.
keywords: upload folders to github, sync files and folders with github
author: sharathdt
tags: Github-Pages Web-Design Github
image: sync-local-folders-with-github.png
layout: post
permalink: /sync-files-folders-github/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

In my initial days of using Github, I used to see repositories filled with folders, files and what not. I used to wonder how the hell these people are uploading folders to Github! 
{: .clear}

<div class="note">
    <h3>Update</h3>
    <p>
    Github has a new <a href="/github-upload/" target="_blank"><strong>drag and drop upload option</strong></a> available for direct uploading of files and folders. But, the method I'm discussing in this post is also required to make changes and puch only the changes.
    </p>
</div>


* Do not remove this line (it will not be displayed) 
{:toc}

It is only after some tutorials I realized that it is indeed very easy. The day I found out how to upload folders was one of the happiest days because I knew one thing for sure, uploading files = uploading a complete website :sunglasses:

That is exactly what I'm going to do here. This one is going to be a lengthy post, so grab a cup of coffee :coffee:!

I'm going to create this website (or at least host it) - [Hyperspace](http://redgadget.github.io/MyFirstWebsite/){:rel='nofollow'}{:target="_blank"}


Download these things before we start

1. **Link 1:** [Github Desktop](https://desktop.github.com/){:target="_blank"}


2. **Link 2:** [HTML5 sample website - Hyperspace](http://html5up.net/hyperspace/download){:target="_blank"}


## Step 1: Create a repository and make a gh-pages branch

Login to your Github account and create a repository. Name it anything you feel like. I'm calling it **MyFirstWebsite**. Commit once you are done naming it. Now create a **gh-pages** branch in your repository.

Refer to [How to create and host a website](/create-host-website-github-pages/){:target="_blank"} if you are not sure how to create a branch.

Remember - project files can only be hosted using gh-pages branch.


## Step 2: Install Github Desktop

I guess you are smart enough to install a software. Once you are done installing, open the app. You should see something like this.

![How to sync folders with Github]({{ site.url }}/images/sync-folders-with-github-desktop-tutorial-screenshot.jpg){: .full}

## Step 3: Set up Github account in Github Desktop
![How to sync folders with Github]({{ site.url }}/images/github-desktop-settings.jpg)
{: .left .small}
Click on the gear icon on the top-right corner and hit **Options...**. Now you should see an option with name **Accounts**. Click on **Add account**.

<p class="clear"></p>

![How to sync folders with Github - Github Desktop Account setup]({{ site.url }}/images/github-desktop-account-setup.jpg)
{: .right .half}

Enter your Github credentials and hit Login (choose Github Enterprise if you have an Enterprise account).

{% include adsense-inside-post.html %}

## Step 4: Clone the repository you just created
{: .clear}
![How to sync folders with Github - Github Desktop clone screenshot]({{ site.url }}/images/clone-repository-to-local-folder-github-desktop.jpg)
{: .left .half}
Click on the **+** icon on the left-top corner of Github Desktop. You should see these options.

<p class="clear"></p>

![Github Desktop clone screenshot]({{ site.url }}/images/clone-repository-to-local-folder-github-desktop-2.jpg)
{: .right .large}
Click on clone. Github should list all your repository available for cloning. Select the repository you just created. In my case - **MyFirstWebsite**. Then hit the check-mark below which says **Clone MyFirstWebsite**    



You may have to choose a local folder where you want the repository to be downloaded. I usually choose **Documents** folder. Select a folder, click on Ok and wait for the app to sync your repository.
{: .clear}

![How to sync folders with Github - Change branch in Github Desktop]({{ site.url }}/images/change-branch-in-github-desktop.jpg)
{: .left .half}
Now change the branch to **gh-pages** as shown in the screenshot. Now right click on the repository listed on the left side and choose **Open in Explorer**. It will open an Explorer window with just a ```.git``` folder inside it. 

<p class="clear"></p>

![Cloned repository in local folder]({{ site.url }}/images/cloned-repository-inside-local-folder.jpg)
{: .right .half}

Remember: Whatever changes you do inside this folder will be reflected in the app.

## Step 5: Copy complete website in local repository
{: .clear}

![Copy complete website to github repository]({{ site.url }}/images/copy-complete-website-to-repository.jpg)
{: .left .small}
If you have downloaded the file from **Link 1** then open it and extract the contents to a folder. Copy all these files and folders into our locally synced repository.



## Step 6: Sync to github!
{: .clear}
![Commit changes to Github Desktop]({{ site.url }}/images/commit-changes-to-github-desktop.jpg){: .right .large}

Come back to the Github Desktop app and click on **Changes** tab. You should see all the changes you just did, all the files and folders you added etc., 

Once you are satisfied looking at it, hit commit and wait for the app to sync it with remote (but your) Github repository.

## Step 7: Your website must be hosted on Github Pages now.
{: .clear}

![ How to sync folders with Github - Successfully synced files and folders with Github]({{ site.url }}/images/successfully-synced-folders-in-github.jpg)
{: .left .small}

Now, login to your Github account to see whether your website has been hosted. Navigate to your repository that you just synced. 

Change the branch to gh-pages and see if the files you synced are present in that branch.

Now click on settings and look for **Github Pages** section where you will see a green check mark with an ugly looking URL next to it. Hit that URL. You should see your website hosted!
{: .clear}


![How to sync folders with Github - Hosting a complete website on Github Pages]({{ site.url }}/images/hosting-a-complete-website-on-github-pages.jpg){: .full}


<iframe itemscope="" itemprop="video" class="left half video" src="https://www.youtube.com/embed/5BSpJ0bpE14?rel=0" frameborder="0" allowfullscreen></iframe>
Here is the final URL: [MyFirstWebsite](http://redgadget.github.io/MyFirstWebsite/){:rel='nofollow'}{:target="_blank"} and a video demonstration.

### Change the URL to something not ugly?
Read: [How to add custom domain to websites hosted on Github Pages](/custom-domain-github/){:target="_blank"}. 

If you are stuck in any of these steps, please leave a comment. I'll try to help. 
Thanks for reading! For more detailed tutorials like this one, subscribe.
{: .clear}

