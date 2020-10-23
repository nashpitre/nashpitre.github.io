---
layout: default
title: Blog
permalink: blog
---

# Blog

{% assign postsByYearMonth = site.categories.blog | group_by_exp: "post", "post.date | date: '%B, %Y'" %}
{% for yearMonth in postsByYearMonth %}
  <strong>{{ yearMonth.name }}</strong>
  <ul>
    {% for post in yearMonth.items %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
