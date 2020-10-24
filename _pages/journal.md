---
layout: page
title: Journal
permalink: journal
---

<div class="posts">
  {% for post in site.categories.journal %}
  <article class="post">
    <strong><time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date: "%A, %B %d, %y" }}</time></strong>
    {{ post.content }}
  </article>
  {% endfor %}
</div>