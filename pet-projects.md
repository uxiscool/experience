---
layout: default
title: Pet projects
permalink: /pet-projects/
---

<!-- Короткое описание раздела -->
<div class="pet-meta">
  <div class="case-summary2">
    Side projects, experiments and "little joys" where you can quickly try out ideas and roll them out into the world.
  </div>
</div>

<!-- Сетка карточек pet projects -->
<div class="pp-grid">
  {% assign items = site.petprojects %}

  {% for p in items %}
    {% assign pet_index = forloop.index0 %}

    {%- assign first = p.gallery[0] -%}
    {%- assign thumb_src = nil -%}
    {% if first %}
      {% assign t = first.src | default:first.file %}
      {% if t %}
        {% if p.images_base %}
          {% assign thumb_src = p.images_base | append: t %}
        {% else %}
          {% assign thumb_src = t %}
        {% endif %}
      {% endif %}
    {% endif %}

    <article class="pp-card">
      <!-- Шапка -->
      <header class="pp-header">
        {% if p.icon %}
          <img class="pp-icon" src="{{ site.baseurl }}{{ p.icon }}" alt="">
        {% endif %}
        <h3 class="pp-title">{{ p.title }}</h3>
      </header>

      <!-- Тело: слева медиа, справа текст + футер -->
      <div class="pp-body">
        <div class="pp-media">
          {% if thumb_src %}
            <a class="pp-media-link"
               href="javascript:void(0)"
               onclick="openPetGallery({{ pet_index }}, 0)"
               aria-label="Open gallery">
              <img
                class="lazy-img"
                decoding="async"
                data-src="{{ site.baseurl }}{{ thumb_src }}"
                alt="">
              <noscript>
                <img src="{{ site.baseurl }}{{ thumb_src }}" alt="">
              </noscript>
            </a>
          {% endif %}
        </div>

        <div class="pp-side">
          <div class="pp-text">
            {% if p.subtitle %}<div class="pp-subtitle">{{ p.subtitle }}</div>{% endif %}
            {% if p.desc %}<div class="pp-desc">{{ p.desc }}</div>{% endif %}
          </div>

          <div class="pp-footer">
            {% if p.kind %}<div class="pp-kind">{{ p.kind }}</div>{% endif %}
            <div class="pp-links">
              {% if p.figma %}
                <a class="pp-store" href="{{ p.figma }}" target="_blank" rel="noopener" aria-label="Open in Figma">
                  <img src="{{ site.baseurl }}/ui/stores/figma.svg" alt="Figma">
                </a>
              {% endif %}
              {% if p.stores and p.stores.play %}
                <a class="pp-store" href="{{ p.stores.play }}" target="_blank" rel="noopener" aria-label="Google Play">
                  <img src="{{ site.baseurl }}/ui/stores/googleplay.svg" alt="Google Play">
                </a>
              {% endif %}
              {% if p.stores and p.stores.appstore %}
                <a class="pp-store" href="{{ p.stores.appstore }}" target="_blank" rel="noopener" aria-label="App Store">
                  <img src="{{ site.baseurl }}/ui/stores/appstore.svg" alt="App Store">
                </a>
              {% endif %}
            </div>
          </div>
        </div>
      </div>
    </article>
  {% endfor %}
</div>

<!-- Лайтбокс -->
<div id="lightbox" class="lightbox" style="display:none;">
  <div class="lightbox-bg" onclick="closeLightbox"></div>
  <div class="lightbox-content">
    <button class="lightbox-close" onclick="closeLightbox()" aria-label="Close">
      <img src="{{ site.baseurl }}/ui/lightbox_close.svg" width="36" height="36" alt="Close">
    </button>

    <!-- Стрелка влево (вернули) -->
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
