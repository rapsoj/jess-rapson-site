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

<script>
  (function () {
    const gallery = document.querySelector('.art-gallery .gallery');
    if (!gallery) return;

    const items = Array.from(gallery.querySelectorAll('.gallery-item'));
    let resizeFrame;

    function sizeItem(item) {
      const image = item.querySelector('img');
      const styles = window.getComputedStyle(gallery);
      const rowHeight = parseFloat(styles.gridAutoRows);
      const rowGap = parseFloat(styles.rowGap);

      if (image.naturalWidth / image.naturalHeight >= 1.1) {
        item.classList.add('is-wide');
      } else {
        item.classList.remove('is-wide');
      }

      const caption = item.querySelector('figcaption');
      const captionStyles = caption ? window.getComputedStyle(caption) : null;
      const captionHeight = caption
        ? caption.getBoundingClientRect().height + parseFloat(captionStyles.marginTop)
        : 0;
      const itemHeight = image.getBoundingClientRect().height + captionHeight;

      item.style.gridRowEnd = `span ${Math.ceil((itemHeight + rowGap) / (rowHeight + rowGap))}`;
    }

    function layoutGallery() {
      items.forEach(function (item) {
        item.style.gridRowEnd = 'auto';
      });
      items.forEach(sizeItem);
    }

    items.forEach(function (item) {
      const image = item.querySelector('img');
      if (!image.complete) image.addEventListener('load', layoutGallery, { once: true });
    });

    window.addEventListener('load', layoutGallery);
    window.addEventListener('resize', function () {
      window.cancelAnimationFrame(resizeFrame);
      resizeFrame = window.requestAnimationFrame(layoutGallery);
    });

    layoutGallery();
  }());
</script>
