---
layout: default
desc: Webjeda jekyll themes is a showcase of hand-picked, responsive jekyll themes. You will find some of the best jekyll themes that can be used for your website blog or portfolio.
permalink: /jekyll-themes/
---
 

<div id="mainbox">
     {% for jekyll-themes in site.jekyll-themes %}
       <a class="post-link-index" href="{{ jekyll-themes.url | prepend: site.baseurl }}">
          <div class="card">
                <img alt="{{ jekyll-themes.title }}" class="post-image-index" itemprop="thumbnailUrl" src="/thumbs/{{ jekyll-themes.img }}" width="300" height="auto" />
                <div class="card-footer">
                    <h6 class="post-index-title">{{ jekyll-themes.title }}</h6>
                <p class="post-excerpt">{{ jekyll-themes.desc | truncate: 160 }}</p>
               </div>
     
        </div> 
     </a>
      {% endfor %}   
</div>