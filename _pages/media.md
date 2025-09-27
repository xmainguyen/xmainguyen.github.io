---
layout: page
permalink: /media/
title: Media Mentions
description: Highlights of academic achievements, press features, and research
nav: true
nav_order: 2
horizontal: false
---

<div class="projects">

{% assign sorted_media = site.media | sort: "importance" %}

  {% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for item in sorted_media %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for item in sorted_media %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
</div>