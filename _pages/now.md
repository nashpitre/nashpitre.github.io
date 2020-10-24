---
layout: home
title: Now
permalink: /index.html
---

Welcome to the new, much cleaner version of my site. This has been my latest project. This new looks aims to be more minimal and more mature. Slowly adding all the content back from the previous site.

<br>

## [Journal](/journal)
<div class="posts">
  {% for post in site.categories.journal | limit: 3 %}
    <strong><time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date: "%A, %B %d, %Y" }}</time></strong>
    {{ post.content }}
    <br>
  {% endfor %}
</div>

## [Blog](/blog)
<div class="posts">
  <ul>
  {% for post in site.categories.blog | limit: 3 %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
    </ul>
</div>
<br>

## [Photos](/photos)
<div class="grid">
  {% for post in site.categories.photos | limit: 4 %}
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
	  	<span class="boxText">{{ post.title }}</span></a>
	  </div>
  {% endfor %}
</div>

## [Music](/music)
<div class="grid">
  {% for post in site.tags["albums"] reversed | limit: 4 %}
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
	  	<span class="boxText">{{ post.title }}</span></a>
	  </div>
  {% endfor %}
</div>

## [Shop](/shop)
<div class="grid">
  {% for post in site.categories.shop reversed | limit: 4 %}
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

## [Videos](/videos)
{% for post in site.categories.video limit:1 %}
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
