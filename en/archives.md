---
layout: page
title: Archives
permalink: /en/archives/
lang: en
french_url: /archives/
---
All articles published on the blog:

{% assign english_posts = site.posts | where: 'lang', 'en' %}<ul class="post-list">{% for post in english_posts %}<li><time>{{ post.date | date: "%d/%m/%Y" }}</time> · <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>{% endfor %}</ul>
