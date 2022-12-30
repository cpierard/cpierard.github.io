---
layout: page
title: Projects 🔱
permalink: /projects/
---

These are some of the projects I've worked on.
<ul>
{% for post in site.posts %}
<li><a href= "{{ post.url }}">{{post.title}}</a></li>
{% endfor %}
</ul>
