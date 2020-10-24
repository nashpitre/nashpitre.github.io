---
layout: page
title: Shop
permalink: shop
---

<div class="grid">
{% for post in site.categories.shop %}
  <div class="gridBox">
	<a href="{{ post.url }}">
	{% assign foundImage = 0 %}
	{% assign images = post.content | split:"<img " %}
	{% for image in images %}
		{% if image contains 'src' %}
			{% if foundImage == 0 %}
				{% assign html = image | split:"/>" | first %}
				<img {{ html }} />
				{% assign foundImage = 1 %}
			{% endif %}
		{% endif %}
	{% endfor %}
	</a>
  </div>
{% endfor %}
</div>