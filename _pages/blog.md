---
layout: default
title: Words
permalink: blog
---

# Words

{% assign postsByYearMonth = site.categories.blog | group_by_exp: "post", "post.date | date: '%B, %Y'" %}
{% for yearMonth in postsByYearMonth %}
  <h2>{{ yearMonth.name }}</h2>
  <ul>
    {% for post in yearMonth.items %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
