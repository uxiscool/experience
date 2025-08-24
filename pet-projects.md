---
layout: default
title: Pet projects
permalink: /pet-projects/
---

<!-- краткое описание раздела, как «лейбл кейса», но только текст -->
<div class="pet-meta">
  <div class="case-summary2">
    Side projects, experiments and “little joys” where you can quickly try out ideas and roll them out into the world.
  </div>
</div>
<div class="pet-grid">
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
  <a class="pet-card-link"
     href="javascript:void(0)"
     onclick="openPetGallery({{ pet_index }}, 0)"
     style="--bg1: {{ p.bg_colors[0] | default: '' }}; --bg2: {{ p.bg_colors[1] | default: '' }}; --bg3: {{ p.bg_colors[2] | default: '' }};">
    <article class="pet-card{% if p.bg_image %} has-bg{% endif %}">
      {% if p.bg_image %}
        <div class="pet-bg" style="background-image:url('{{ site.baseurl }}{{ p.bg_image }}')"></div>
      {% endif %}
      <!-- Шапка: иконка + заголовок -->
      <header class="pet-inner">
        <img class="pet-icon" src="{{ site.baseurl }}{{ p.icon }}" alt="">
        <div class="pet-head">
          <h3 class="pet-title">{{ p.title }}</h3>
        </div>
      </header>
      <!-- Контент: слева медиа, справа текст; низ справа — тип и ссылки -->
      <div class="pet-content">
        <div class="pet-media">
          {% if thumb_src %}
            <img class="pet-media-img" src="{{ site.baseurl }}{{ thumb_src }}" alt="">
          {% else %}
            <div class="pet-media-empty"></div>
          {% endif %}
        </div>
        <div class="pet-side">
          <div class="pet-text">
            <div class="pet-subtitle">{{ p.subtitle }}</div>
            {% if p.desc %}<div class="pet-desc">{{ p.desc }}</div>{% endif %}
          </div>
          <div class="pet-side-bottom">
            {% if p.kind %}<div class="pet-kind">{{ p.kind }}</div>{% endif %}
            <div class="pet-links">
              {% if p.figma %}
                <a class="pet-link-icon" href="{{ p.figma }}" target="_blank" rel="noopener" onclick="event.stopPropagation()">
                  <img src="{{ site.baseurl }}/ui/stores/figma.svg" alt="Figma">
                </a>
              {% endif %}
              {% if p.stores and p.stores.play %}
                <a class="pet-link-icon" href="{{ p.stores.play }}" target="_blank" rel="noopener" onclick="event.stopPropagation()">
                  <img src="{{ site.baseurl }}/ui/stores/googleplay.svg" alt="Google Play">
                </a>
              {% endif %}
              {% if p.stores and p.stores.appstore %}
                <a class="pet-link-icon" href="{{ p.stores.appstore }}" target="_blank" rel="noopener" onclick="event.stopPropagation()">
                  <img src="{{ site.baseurl }}/ui/stores/appstore.svg" alt="App Store">
                </a>
              {% endif %}
            </div>
          </div>
        </div>
      </div>
    </article>
  </a>
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
    <img id="lightbox-img" class="lightbox-img" src="">
    <button class="lightbox-arrow right" onclick="lightboxNext()" aria-label="Next">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_right.svg" width="36" height="36" alt="Next">
    </button>
    <div id="lightbox-caption" class="lightbox-caption"></div>
  </div>
</div>
