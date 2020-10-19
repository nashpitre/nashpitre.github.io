---
layout: page
title: Videos
permalink: videos
---

{% for post in paginator.posts %}
  {% if site.categories["video"] %}
    <div class="video">
  	  {{ post.content }}
    </div>
  {% endif %}
{% endfor %}