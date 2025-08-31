---
layout: default
title: Cases
permalink: /cases/
---
<!-- Load Playfair (text-friendly) только на /cases/ -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair:ital@1&display=swap" rel="stylesheet">

<!-- Все кейсы подряд в том же лейауте, что и на главной -->
<div class="featured-cases">
  {% assign allcases = site.cases | sort: 'year' | reverse %}
  {% for case in allcases %}
    {% assign case_index = forloop.index0 %}
    <div class="case-block">
      <div class="case-meta2">
        <div class="case-title-row">
          <a href="{{ case.url }}" class="case-title2">{{ case.title }}</a>
        </div>
        <div class="case-meta2-inline">
          {{ case.year }}
          {% if case.company %} · {{ case.company }}{% endif %}
          {% if case.type %} · {{ case.type }}{% endif %}
        </div>
        <div class="case-summary2">{{ case.summary }}</div>
      </div>

      {% if case.stages %}
        {% assign flat_idx = 0 %}
        {% for st in case.stages %}
          {% if st.desc %}
            <div class="stage-summary">{{ st.desc }}</div>
          {% endif %}

          <div class="case-gallery">
            {% for img in st.images %}
              {%- comment -%}
                Формируем путь:
                - если img.src задан — берём его;
                - иначе ждём img.file и склеиваем с case.images_base (если есть).
              {%- endcomment -%}
              {% assign img_path = img.src | default: img.file %}
              {% if img_path %}
                {% if img_path contains '/' or case.images_base == nil %}
                  {% assign img_src = img_path %}
                {% else %}
                  {% assign img_src = case.images_base | append: img_path %}
                {% endif %}
              {% endif %}

              <div class="case-gallery-item">
                <img
                  class="case-thumb2"
                  src="{{ site.baseurl }}{{ img_src }}"
                  alt="{{ img.caption | escape }}"
                  loading="lazy"
                  decoding="async"
                  onclick="openCaseGallery({{ case_index }}, {{ flat_idx }})"
                >
                {% if img.caption %}
                  <div class="case-thumb-caption">{{ img.caption }}</div>
                {% endif %}
              </div>

              {% assign flat_idx = flat_idx | plus: 1 %}
            {% endfor %}
          </div>
        {% endfor %}
      {% else %}
        <!-- Бэкап для старых кейсов с плоским images: -->
        <div class="case-gallery">
          {% for img in case.images %}
            <div class="case-gallery-item">
              <img
                class="case-thumb2"
                src="{{ site.baseurl }}{{ img.src }}"
                alt="{{ img.caption | escape }}"
                loading="lazy"
                decoding="async"
                onclick="openCaseGallery({{ case_index }}, {{ forloop.index0 }})"
              >
              {% if img.caption %}
                <div class="case-thumb-caption">{{ img.caption }}</div>
              {% endif %}
            </div>
          {% endfor %}
        </div>
      {% endif %}
    </div>
  {% endfor %}
</div>

<!-- Лайтбокс (тот же, что на index) -->
<div id="lightbox" class="lightbox" style="display:none;">
  <div class="lightbox-bg" onclick="closeLightbox()"></div>
  <div class="lightbox-content">
    <button class="lightbox-close" onclick="closeLightbox()" aria-label="Close">
      <img src="{{ site.baseurl }}/ui/lightbox_close.svg" width="36" height="36" alt="Close">
    </button>
    <button class="lightbox-arrow left" onclick="lightboxPrev()" aria-label="Previous">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_left.svg" width="36" height="36" alt="Prev">
    </button>
    <img id="lightbox-img" class="lightbox-img" src="">
    <button class="lightbox-arrow right" onclick="lightboxNext()" aria-label="Next">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_right.svg" width="36" height="36" alt="Next">
    </button>
    <div id="lightbox-caption" class="lightbox-caption"></div>
  </div>
</div>
