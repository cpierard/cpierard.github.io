---
layout: page
title: Projects
permalink: /projects/
---

**I'm currently working on the posts for the different projects I've worked on. I will upload them as I finish them.**

Some of the projects I have worked on.
<ul>
{% for post in site.posts %}
<li><a href= "{{ post.url }}">{{post.title}}</a></li>
{% endfor %}
</ul>
