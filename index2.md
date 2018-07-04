---
layout: page
title: Index
permalink: /index/
---

<ul>
{% for post in site.posts %}
  <li>
      <a href="{{ post.url }}">{{ post.title }}</a> ({{ post.date | date_to_string }})<br>
    {{ post.description }}
  </li>
{% endfor %}
</ul>