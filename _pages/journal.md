---
layout: page
title: Journal
permalink: journal
---

{% for posts in site.categories.journal %}
  <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>
  {{ content }}
{% endfor %}
