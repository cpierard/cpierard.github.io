---
layout: page
title: Projects
permalink: /projects/
---

Currently under construction.

Some of the projects I have worked on.

{% for post in site.posts %}
<li><a href= "{{ post.url }}">{{post.title}}</a></li>
{% endfor %}
