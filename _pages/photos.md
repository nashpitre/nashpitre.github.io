---
layout: page
title: Photos
permalink: photos
---

{% assign postsByYearMonth = site.categories.photos | group_by_exp: "post", "post.date | date: '%B %Y'" %}
{% for yearMonth in postsByYearMonth %}
  <div class="grid">
    {% for post in yearMonth.items %}
      <div><a href="{{ post.url }}">{{ post.title }}</a></div>
    {% endfor %}
  </div>
{% endfor %}


<ul>
  {% for post in site.categories.photos %}
    <li>
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
    </li>
  {% endfor %}
</ul>