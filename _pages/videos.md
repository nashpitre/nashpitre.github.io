---
layout: page
title: Videos
permalink: videos
---

{% for post in site.categories.video limit:10 %}
  <div>
	{{ post.content }}
  </div>
{% endfor %}