---
layout: page
title: Art
permalink: /creative/art/
sub_title: Things I made (sketches, paintings, and experiments).
---

<div class="art-gallery">
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
</div>