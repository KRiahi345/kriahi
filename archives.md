---
layout: page
title: Archives
permalink: /archives/
---
Tous les articles publiés sur le blog :

<ul class="post-list">
  {% assign french_posts = site.posts | where_exp: "post", "post.lang != 'en'" %}{% for post in french_posts %}
    <li><time>{{ post.date | date: "%d/%m/%Y" }}</time> · <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
