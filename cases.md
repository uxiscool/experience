---
layout: default
title: Cases
permalink: /cases/
---
<!-- Load Playfair (text-friendly) только на /cases/ -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair:ital@1&display=swap" rel="stylesheet">

<!-- Все кейсы, отсортированные по году (убыв.) и order внутри года -->
<div class="featured-cases">
  {%- comment -%}
    1) Группируем site.cases по году и сортируем группы по убыванию года.
    2) Внутри года: сначала те, у кого задан 'order' (по возрастанию), затем без 'order' в исходном порядке.
    3) Для lightbox используем case_index как реальный индекс внутри site.cases.
  {%- endcomment -%}
  {% assign groups = site.cases | group_by: "year" %}
  {% assign groups_sorted = groups | sort: "name" | reverse %}

  {% for g in groups_sorted %}
    {% assign group_items = g.items %}
    {% assign with_order = group_items | where_exp: "it", "it.order" %}
    {% assign without_order = group_items | where_exp: "it", "it.order == nil" %}
    {% assign with_order_sorted = with_order | sort: "order" %}
    {% assign items_sorted = with_order_sorted | concat: without_order %}

    {% for case in items_sorted %}
      {% assign case_index = 0 %}
      {% for c in site.cases %}
        {% if c.url == case.url %}
          {% assign case_index = forloop.index0 %}
          {% break %}
        {% endif %}
      {% endfor %}

      <div class="case-block">
        <div class="case-year-rail">{{ case.year }}</div>
        <div class="case-meta2">
          <div class="case-title-row">
            {% assign case_anchor = case.url | replace:'/cases/','' | replace:'/','' | downcase %}
            <h2 id="case-{{ case_anchor }}" class="case-title3">{{ case.title }}</h2>
          </div>

          <div class="case-meta2-inline">
            <span class="case-year-inline">{{ case.year }}</span>
            {% if case.company %}<span class="case-company">{{ case.company }}</span>{% endif %}
            {% if case.type %}<span class="case-type">{{ case.type }}</span>{% endif %}
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
                    class="case-thumb2 lazy-img"
                    data-src="{{ site.baseurl }}{{ img_src }}"
                    alt="{{ img.caption | escape }}"
                    decoding="async"
                    onclick="openCaseGallery({{ case_index }}, {{ flat_idx }})">
                  <noscript><img src="{{ site.baseurl }}{{ img_src }}" alt="{{ img.caption | escape }}"></noscript>
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
                  class="case-thumb2 lazy-img"
                  data-src="{{ site.baseurl }}{{ img_src }}"
                  alt="{{ img.caption | escape }}"
                  decoding="async"
                  onclick="openCaseGallery({{ case_index }}, {{ forloop.index0 }})">
                <noscript><img src="{{ site.baseurl }}{{ img_src }}" alt="{{ img.caption | escape }}"></noscript>
                {% if img.caption %}
                  <div class="case-thumb-caption">{{ img.caption }}</div>
                {% endif %}
              </div>
            {% endfor %}
          </div>
        {% endif %}
      </div>
    {% endfor %}
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
    <div class="lightbox-stage">
      <img id="lightbox-img" class="lightbox-img" src="">
      {% include lightbox_loader.html %}
    </div>
    <button class="lightbox-arrow right" onclick="lightboxNext()" aria-label="Next">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_right.svg" width="36" height="36" alt="Next">
    </button>
    <div id="lightbox-caption" class="lightbox-caption"></div>
    <div id="lightbox-thumbs" class="lightbox-thumbs-wrap" aria-label="Gallery thumbnails">
      <div class="lightbox-thumbs" id="lightbox-thumbs-row"></div>
    </div>
  </div>
</div>