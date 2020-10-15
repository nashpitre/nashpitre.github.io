---
layout: page
title: Photos
permalink: photos
---

{% assign postsByYear = site.categories.photos | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for yearS in postsByYear %}
<h2>{{ yearS.name }}</h2>
  <div class="grid">
    {% for post in yearS.items reversed %}
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
      	</div>
      	<span class="boxText">{{ post.title }}</span></a>
      	</div>
    {% endfor %}
  </div>
{% endfor %}