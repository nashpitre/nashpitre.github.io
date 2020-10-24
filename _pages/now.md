---
layout: home
title: Now
permalink: /index.html
---

Welcome to the new, much cleaner version of my site. This has been my latest project. This new looks aims to be more minimal and more mature. Slowly adding all the content back from the previous site.

This has been a very quiet year for me. Even though I released three new albums—[When The Satellite Fell](satellite), [Chasing My Ghost](ghost), and [The Illusion of Progress](progress) (the most I’ve ever done in a single year)—there has been hardly any discussions or promotion for them. Most of this music was made prior to 2020. *Ghost* and *Progress* were recorded last year, then released in February and June. *Satellite* was recorded this year in March, and then released in September.

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
