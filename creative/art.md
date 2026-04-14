---
layout: default
title: Art
permalink: /creative/art/
---

<h1>{{ page.title }}</h1>

<div class="gallery">
  {% for image in site.data.art %}
    <figure class="gallery-item">
      <img src="{{ image.src }}" alt="{{ image.alt }}">
      {% if image.caption %}
        <figcaption>{{ image.caption }}</figcaption>
      {% endif %}
    </figure>
  {% endfor %}
</div>