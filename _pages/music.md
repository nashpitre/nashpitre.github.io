---
layout: page
title: music
permalink: music
---

![][image-1]

## Discography

- 2020 - [Chasing My Ghost][1]
- 2020 - [The Illusion of Progress][2]
- 2019 - [How We See The World][3]
- 2018 - [Invisible Man][4]
- 2017 - [The Loop][5]
- 2016 - Pilot
- 2016 - The Land of Unfamiliar
- 2016 - Side B
- 2015 - [The Mask][6]
- 2015 - The Hero Dies
- 2014 - Learning to Fly
- 2014 - [For My Brother][7]
- 2013 - [PlasticSky][8]
- 2013 - The Art of Storytelling
- 2012 - Landing Gear
- 2010 - The Lighthouse
- 2010 - The Great Escape
- 2008 - NASHP & D-Low Show
- 2008 - Circle of Success
- 2007 - The Science Project
- 2006 - One Man Army
- 2005 - Triple Threat
- 2005 - Spotlight Kid
- 2005 - Underground Vol. 2
- 2004 - Blast From The Past
- 2003 - Underground Vol. 1

---- 

## Featured Albums

<div class="grid">
{% for post in site.categories.music %}
  {% for post in site.tags.ablums %}
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
{% endfor %}
</div>

[1]:	ghost
[2]:	progress
[3]:	world
[4]:	/invisible
[5]:	/loop
[6]:	/mask
[7]:	/brother
[8]:	/plasticsky

[image-1]:	https://i.imgur.com/XxufeAA.jpg