---
layout: page
title: Videos
permalink: videos
---

{% for post in site.categories.video %}
  {% for post in paginator.posts %}
  <div>
	{{ post.content }}
  </div>
  {% endfor %}
{% endfor %}