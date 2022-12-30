---
layout: page
title: Projects 🔱
permalink: /projects/
---

This are some of the plots I've worked on.
<ul>
{% for post in site.posts %}
<li><a href= "{{ post.url }}">{{post.title}}</a></li>
{% endfor %}
</ul>
