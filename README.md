<!DOCTYPE html>
<html lang="en">
   <head>
      {% include head.html %}  
      {% if page.mathjax %}			
      {% include markdown-enhancements/mathjax.html %}
      {% endif %}
      {% include theme-vue.html%}
      <!-- font awesome -->
      <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.5.0/css/all.css">
      <!-- change font -->
      <link href="https://fonts.googleapis.com/css?family=Roboto+Mono:400,400i,700|Source+Sans+Pro|Ubuntu+Mono" rel="stylesheet">
      {% if page.numbering == true %}
      <!-- link to counter.css -->
      <link rel="stylesheet" href="{{site.url}}{{site.baseurl}}/assets/css/counter.css">
      {% endif %}
      <!-- link to responsive post.css -->
      <link rel="stylesheet" href="{{site.url}}{{site.baseurl}}/assets/css/post.css">
   </head>
   <body>
      <input type="checkbox" class="sidebar-checkbox" id="sidebar-checkbox">
      <!-- this is side bar -->
      <div class="sidebar" id="sidebar">
         <nav class="sidebar-nav">
            {% include navitem.html %}
         </nav>
         {% if page.toc %}
         <div class="toc">
            <div class='toc-container'>
               {% include toc.html html=content %}
            </div>
         </div>
         {% endif %}
      </div>
      <!-- Add all page content inside this div if you want the side nav to push page content to the right
         (not used if you only want the sidenav to sit on top of the page -->
      <div class="wrap">
         <div class="container content">
            <div class="page">
               <div id="title">
                  <h1>
                     {{page.title}}
                  </h1>
               </div>
               <div id="info">
                  <div id="date">
                     {% if page.edit %}
                     <p><code>Edited</code>:  &nbsp; {{ page.edit | date: '%B %d, %Y' }} </p>
                     {% endif %}
                  </div>
               </div>
               {% if page.toc %}
               <div class="toc">
                  <div class='toc-container'>
                     {% include toc.html html=content %}
                  </div>
               </div>
               {% endif %}
               <div id="content-container" style="text-align:justify">
                  {{ content }}			
               </div>
            </div>
         </div>
      </div>
      <label for="sidebar-checkbox" class="sidebar-toggle"></label>
      {% include footer.html %} 
   </body>
   {% if page.mermaid == true %}
   {% include markdown-enhancements/mermaid.html %}
   {% endif %}
   {% if page.highlight == true %}
   {% include markdown-enhancements/highlight.html %}
   {% endif %}
</html>
