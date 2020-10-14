---
layout: page
title: Photos
permalink: photos
---

{% assign postsByYear = site.categories.photos | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for year in postsByYearMonth %}
<h2>{{ year.name }}</h2>
  <div class="grid">
    {% for post in yearMonth.items %}
      <div>
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
      <a href="{{ post.url }}">{{ post.title }}</a>
      </div>
    {% endfor %}
  </div>
{% endfor %}