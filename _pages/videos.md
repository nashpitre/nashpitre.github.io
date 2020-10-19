---
layout: page
title: Videos
permalink: videos
---

{% for post in paginator.posts %}
  {% if post.categories contains video %}
    <div class="video">
  	  {{ post.content }}
    </div>
  {% endif %}
{% endfor %}