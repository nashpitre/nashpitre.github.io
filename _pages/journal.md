---
layout: page
title: Journal
permalink: journal
---

{% for post in site.categories.journal %}
  <div class="journal">
    <strong><time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time></strong>
    {{ content }}
  </div>
{% endfor %}