---
layout: home
title: Now
permalink: /index.html
---

Welcome to the new, much cleaner version of my site. This has been my latest project. This new looks aims to be more minimal and more mature. Slowly adding all the content back from the previous site.

<br>

## Journal

<div class="posts">
  {% for post in site.categories.journal | limit: 1 %}
  <article class="post">
    <strong><time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date: "%A, %B %d, %Y" }}</time></strong>
    {{ post.content }}
  </article>
  {% endfor %}
</div>
[Read more of my daily journal](/journal)
