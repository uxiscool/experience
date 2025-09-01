---
layout: default
title: Cases
permalink: /cases/
---

<!-- Загружаем Playfair только здесь для курсивных подпунктов этапов -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair:ital@1&display=swap" rel="stylesheet">

<!-- Все кейсы в том же лейауте, что на главной -->
<div class="featured-cases">
  {% assign allcases = site.cases | sort: 'year' | reverse %}

  {% for case in allcases %}
    {% assign case_index = forloop.index0 %}

    <div class="case-block">
      <div class="case-meta2">
        <div class="case-title-row">
          <a class="case-title2" href="{{ case.url | relative_url }}">{{ case.title }}</a>
          {% if case.year %}<span class="case-year2">• {{ case.year }}</span>{% endif %}
        </div>
        {% if case.type %}<div class="case-type2">{{ case.type }}</div>{% endif %}
        {% if case.summary %}<div class="case-summary2">{{ case.summary }}</div>{% endif %}
      </div>

      <!-- Галерея кейса -->
      <div class="case-gallery">
        {% comment %}
          Собираем плоский индекс flat_idx, чтобы openCaseGallery(case_index, flat_idx) всегда попадал в нужный кадр
        {% endcomment %}
        {% assign flat_idx = 0 %}

        {% if case.stages %}
          {% for st in case.stages %}
            {% if st.title %}
              <div class="stage-summary">{{ st.title }}</div>
            {% endif %}

            {% if st.images %}
              {% for img in st.images %}
                {% assign img_src = img.src | default: img.file %}
                {% if img_src %}
                  {% if case.images_base %}
                    {% assign img_src = case.images_base | append: img_src %}
                  {% endif %}
                  <div class="case-gallery-item">
                    <img
                      class="case-thumb2 lazy-img"
                      data-src="{{ site.baseurl }}{{ img_src }}"
                      alt="{{ img.caption | escape }}"
                      decoding="async"
                      onclick="openCaseGallery({{ case_index }}, {{ flat_idx }})">
                    <noscript>
                      <img class="case-thumb2" src="{{ site.baseurl }}{{ img_src }}" alt="{{ img.caption | escape }}">
                    </noscript>
                    {% if img.caption %}
                      <div class="case-thumb-caption">{{ img.caption }}</div>
                    {% endif %}
                  </div>
                  {% assign flat_idx = flat_idx | plus: 1 %}
                {% endif %}
              {% endfor %}
            {% endif %}
          {% endfor %}
        {% elsif case.images %}
          {% for img in case.images %}
            {% assign img_src = img.src | default: img.file %}
            {% if img_src %}
              {% if case.images_base %}
                {% assign img_src = case.images_base | append: img_src %}
              {% endif %}
              <div class="case-gallery-item">
                <img
                  class="case-thumb2 lazy-img"
                  data-src="{{ site.baseurl }}{{ img_src }}"
                  alt="{{ img.caption | escape }}"
                  decoding="async"
                  onclick="openCaseGallery({{ case_index }}, {{ forloop.index0 }})">
                <noscript>
                  <img class="case-thumb2" src="{{ site.baseurl }}{{ img_src }}" alt="{{ img.caption | escape }}">
                </noscript>
                {% if img.caption %}
                  <div class="case-thumb-caption">{{ img.caption }}</div>
                {% endif %}
              </div>
            {% endif %}
          {% endfor %}
        {% endif %}
      </div>
    </div>
  {% endfor %}
</div>

<!-- Лайтбокс -->
<div id="lightbox" class="lightbox" style="display:none;">
  <div class="lightbox-bg" onclick="closeLightbox()"></div>
  <div class="lightbox-content">
    <button class="lightbox-close" onclick="closeLightbox()" aria-label="Close">
      <img src="{{ site.baseurl }}/ui/lightbox_close.svg" width="36" height="36" alt="Close">
    </button>

    <!-- Стрелка влево -->
    <button class="lightbox-arrow left" onclick="lightboxPrev()" aria-label="Previous">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_left.svg" width="36" height="36" alt="Prev">
    </button>

    <div class="lightbox-stage">
      <img id="lightbox-img" class="lightbox-img" src="">
      {% include lightbox_loader.html %}
    </div>

    <!-- Стрелка вправо -->
    <button class="lightbox-arrow right" onclick="lightboxNext()" aria-label="Next">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_right.svg" width="36" height="36" alt="Next">
    </button>

    <div id="lightbox-caption" class="lightbox-caption"></div>
    <div id="lightbox-thumbs" class="lightbox-thumbs-wrap" aria-label="Gallery thumbnails">
      <div class="lightbox-thumbs" id="lightbox-thumbs-row"></div>
    </div>
  </div>
</div>
