---
layout: page
title: Videos
permalink: videos
---

{% for post in site.categories.video %}
  <div class="video">
  	{% assign foundiFrame = 0 %}
	{% assign iFrames = post.content | split:"<iframe " %}
	{% for iFrame in iFrames %}
		{% if iFrame contains 'src' %}
			{% if foundiFrame == 0 %}
				{% assign html = iFrame | split:"/>" | first %}
				<img {{ html }} />
				{% assign foundImage = 1 %}
			{% endif %}
		{% endif %}
	{% endfor %}
  </div>
{% endfor %}