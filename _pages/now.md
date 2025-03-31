---
layout: page
title: Now
permalink: now
---

{% for post in site.categories.now %}
	<h2>{{ page.date | date_to_string }}</h2>
	<p>{{ content }}</p>
	<hr>
{% endfor %}