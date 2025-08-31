---
layout: default
title: Pet projects
permalink: /pet-projects/
---
<!-- краткое описание раздела, как «лейбл кейса», но только текст -->
<div class="pet-meta">
  <div class="case-summary2">
    Side projects, experiments and "little joys" where you can quickly try out ideas and roll them out into the world.
  </div>
</div>
<div class="pp-grid">
  {% assign items = site.petprojects %}
  {% for p in items %}
    {% assign pet_index = 0 %}
    {% for pp in site.petprojects %}
      {% if pp.url == p.url %}{% assign pet_index = forloop.index0 %}{% break %}{% endif %}
    {% endfor %}
    {%- assign first = p.gallery[0] -%}
    {%- assign thumb_src = nil -%}
    {% if first %}
      {% assign thumb_path = first.src | default:first.file %}
      {% if thumb_path %}
        {% if thumb_path contains '/' or p.images_base == nil %}
          {% assign thumb_src = thumb_path %}
        {% else %}
          {% assign thumb_src = p.images_base | append: thumb_path %}
        {% endif %}
      {% endif %}
    {% endif %}
  <article class="pp-card">
    <!-- Шапка -->
    <header class="pp-header">
      <img class="pp-icon" src="{{ site.baseurl }}{{ p.icon }}" alt="">
      <h3 class="pp-title">{{ p.title }}</h3>
    </header>
    <!-- Тело: слева медиа, справа текст + футер, приклеенный к низу -->
    <div class="pp-body">
      <div class="pp-media">
        {% if thumb_src %}
          <a class="pp-media-link"
             href="javascript:void(0)"
             onclick="openPetGallery({{ pet_index }}, 0)"
             aria-label="Open gallery">
            <div class="img-skel" aria-hidden="true"></div>
            <img class="lazy-img"
                 loading="lazy" decoding="async"
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
              <a class="pp-store" href="{{ p.figma }}" target="_blank" rel="noopener">
                <img src="{{ site.baseurl }}/ui/stores/figma.svg" alt="Figma">
              </a>
            {% endif %}
            {% if p.stores and p.stores.play %}
              <a class="pp-store" href="{{ p.stores.play }}" target="_blank" rel="noopener">
                <img src="{{ site.baseurl }}/ui/stores/googleplay.svg" alt="Google Play">
              </a>
            {% endif %}
            {% if p.stores and p.stores.appstore %}
              <a class="pp-store" href="{{ p.stores.appstore }}" target="_blank" rel="noopener">
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
<!-- используем общий lightbox из default.html -->
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