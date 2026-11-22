---
layout: page
title: Archives
permalink: /archives/
---
Tous les articles publiés sur le blog :

<ul class="post-list">
  {% for post in site.posts %}
    <li><time>{{ post.date | date: "%d/%m/%Y" }}</time> · <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
