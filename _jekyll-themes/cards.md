---
title: Cards
layout: post
img: webjeda-cards-jekyll-theme.png
desc: Webjeda cards is a bootstrap based minimal Jekyll theme. It is suitable for all kinds of blogs especially image based blogs. It features a sidebar inside posts.
link: https://webjeda.com/cards/
dlink: https://github.com/sharu725/cards/archive/master.zip
---


# Installation: 
Fork the ``master`` branch and delete ``gh-pages`` branch in it. This is important because ``gh-pages`` branch is used here only to host the blog. You should be using the master branch as the source and create a fresh ``gh-pages`` branch.

Watch my video on instlallation
<iframe width="100%" height="400" src="https://www.youtube.com/embed/T2nx6tj-ZH4?rel=0" frameborder="0" allowfullscreen></iframe>

## How to delete old **gh-pages** branch?
After forking the repository, click on **branches**.

![delete gh-pages branch](/images/delete-github-branch.png)

Delete ``gh-pages`` branch.
![delete gh-pages branch](/images/delete-github-branch-2.png)

You have to create a new ``gh-pages`` branch using the master branch. Go back to the forked repository and create ``gh-pages`` branch.

![create gh-pages branch](/images/create-gh-pages-branch.JPG)

Now, go to settings and check the **Github Pages** section. You should see a URL where the blog is hosted.

This process will host the theme as a **Project Page**. You can also download the files for local development. 

Default theme will look like this

![webjeda cards jekyll theme](/images/webjeda-cards-jekyll-theme-1.png){: .noborder}

This theme is responsive.

![webjeda cards responsive jekyll theme](/images/webjeda-cards-responsive-jekyll-theme-2.png){: .noborder}
{:  style="text-align:center" }



# Development
Make changes to the **master** branch and create a pull request. Do not use **gh-pages** branch as it is used to host the theme.


# License
MIT License

[**Demo**]({{page.link}}){: .btn }
[**Download**]({{page.dlink}}){: .btn .red }