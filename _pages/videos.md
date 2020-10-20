---
layout: page
title: Videos
permalink: videos
---

{% for post in site.categories.video limit:10 %}
  <div class="video">
  	{% assign foundiFrame = 0 %}
	{% assign iFrames = post.content | split:"<iframe " %}
	{% for iFrame in iFrames %}
		{% if iFrame contains 'src' %}
			{% if foundiFrame == 0 %}
				{% assign html = iFrame | split:">" | first %}
				<iframe {{ html }}></iframe>
				{% assign foundiFrame = 1 %}
			{% endif %}
		{% endif %}
	{% endfor %}
  </div>
{% endfor %}

<div>
  <h2>All Posts</h2>
  <ul>
	{% for post in site.categories.video %}
		  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor %}
  </ul>
</div>