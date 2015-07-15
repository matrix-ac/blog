---
layout: page
title: Zion Archive
permalink: /zion-archive/
---

The Zion Archive contains documentation for the Matrix. 

<div class="home">
{% for cat in site.zion-list %}
<h2 class="body-text-header">{{ cat }}</h2>
<ul class="post-list">
  {% for page in site.pages %}
    {% if page.resource == true %}
      {% for pc in page.categories %}
        {% if pc == cat %}
          <li>
          <h3><a  href="{{ page.url }}">{{ page.title }}</a></h3>
          </li>
        {% endif %}   <!-- cat-match-p -->
      {% endfor %}  <!-- page-category -->
    {% endif %}   <!-- resource-p -->
  {% endfor %}  <!-- page -->
</ul>
{% endfor %}  <!-- cat -->
</div>