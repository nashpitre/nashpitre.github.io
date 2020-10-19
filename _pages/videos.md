---
layout: page
title: Videos
permalink: videos
---

{% for post in site.categories.video %}
  <div class="video">
    {{ post.content }}
  </div>
{% endfor %}