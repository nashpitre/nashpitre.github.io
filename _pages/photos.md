---
layout: page
title: Photos
permalink: photos
---

{% assign postsByYear = site.categories.photos | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for yearS in postsByYear %}
<h2>{{ yearS.name }}</h2>
  <div class="grid">
    {% for post in yearS.items %}
      <div>
      {% assign foundImage = 0 %}
      {% assign images = post.content | split:"<img " %}
      {% for image in images %}
        {% if image contains 'src' %}
            {% if foundImage == 0 %}
                {% assign html = image | split:"/>" | first %}
                <img {{ html }} />
                {% assign foundImage = 1 %}
                {% else %}
                	<h3>{{ post.placeholder }}</h3>
            {% endif %}
        {% endif %}
      {% endfor %}
      <a href="{{ post.url }}">{{ post.title }}</a>
      </div>
    {% endfor %}
  </div>
{% endfor %}