---
layout: page
title: Journal
permalink: journal
---

<div class="posts">
  {% for post in site.categories.journal %}
  <article class="post">
    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>
    {{ post.content }}
  </article>
  {% endfor %}
</div>