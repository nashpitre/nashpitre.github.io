---
layout: page
title: Photos
permalink: photos
---

<div class="posts">
  {% for post in site.categories.photos %}
  <article class="post">
    <h1 class="post-title">
      <a href="{{ post.url | relative_url }}">
        {{ post.title }}
      </a>
    </h1>
  </article>
  {% endfor %}
</div>