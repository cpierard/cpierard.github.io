---
layout: home
# This replaces the default 'Welcome!' title
alt_title: "Claudio M. Pierard"
sub_title: "Physicist & Physical Oceanographer"

# Your introductory text
introduction: |
  <!-- Top Frame (Rotated 180°) -->
  <div style="display: flex; justify-content: center; overflow: hidden; margin-bottom: 20px; transform: rotate(180deg);">
    {% for i in (1..10) %}
      <img src="{{ '/assets/conv_23.gif' | relative_url }}" width="80" style="margin: 0 0px;" />
    {% endfor %}
  </div>

  I'm a physicist with a PhD in physical oceanography interested in the development of new statistical methods for the analysis of geophysical data. This is a personal archive of the projects that I worked on. 
  
  Feel free to reach out.

  <!-- Bottom Frame -->
  <div style="display: flex; justify-content: center; overflow: hidden; margin-top: 20px;">
    {% for i in (1..10) %}
      <img src="{{ '/assets/a1.gif' | relative_url }}" width="80" style="margin: 0 0px;" />
    {% endfor %}
  </div>

# These create nice buttons under your text
actions:
  - label: "View Projects"
    icon: folder
    url: "/projects/"
  - label: "About Me"
    icon: user
    url: "/about/"
---
