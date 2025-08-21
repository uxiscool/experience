---
layout: default
title: Pet projects
permalink: /pet-projects/
---

<!-- краткое описание раздела, как «лейбл кейса», но только текст -->
<div class="pet-meta">
  <div class="case-summary2">
    Side-проекты, эксперименты и «маленькие радости», где можно быстро пробовать идеи
    и выкатывать в мир. Тут и плагины для Figma, и мобильные приложения-игрушки.
  </div>
</div>
<div class="pet-grid">
  {% assign items = site.petprojects %}
  {% for p in items %}
    {% assign pet_index = 0 %}
    {% for pp in site.petprojects %}
      {% if pp.url == p.url %}{% assign pet_index = forloop.index0 %}{% break %}{% endif %}
    {% endfor %}
    <a class="pet-card-link" href="javascript:void(0)" onclick="openPetGallery({{ pet_index }}, 0)"
       style="--bg1: {{ p.bg_colors[0] | default: '' }}; --bg2: {{ p.bg_colors[1] | default: '' }}; --bg3: {{ p.bg_colors[2] | default: '' }};">
      <article class="pet-card{% if p.bg_image %} has-bg{% endif %}">
        {% if p.bg_image %}
          <div class="pet-bg" style="background-image:url('{{ site.baseurl }}{{ p.bg_image }}')"></div>
        {% endif %}
        <header class="pet-inner">
          <img class="pet-icon" src="{{ site.baseurl }}{{ p.icon }}" alt="">
          <div class="pet-head">
            <h3 class="pet-title">{{ p.title }}</h3>
            <div class="pet-subtitle">{{ p.subtitle }}</div>
          </div>
          {% if p.kind %}<div class="pet-type">{{ p.kind }}</div>{% endif %}
        </header>
        <div class="pet-body">
          {% assign first = p.gallery[0] %}
          {% if first and (first.thumb == true or p.overlay == true) %}
            {% assign thumb_src = first.src | default:first.file | prepend:p.images_base | default:first.src %}
            <img class="pet-overlay" src="{{ site.baseurl }}{{ thumb_src }}" alt="">
          {% endif %}
          {% if p.stores and (p.stores.appstore or p.stores.play) %}
            <div class="pet-badges">
              {% if p.stores.appstore %}
                <span class="pet-badge"><img src="{{ site.baseurl }}/ui/stores/appstore.svg" alt="App Store"></span>
              {% endif %}
              {% if p.stores.play %}
                <span class="pet-badge"><img src="{{ site.baseurl }}/ui/stores/googleplay.svg" alt="Google Play"></span>
              {% endif %}
            </div>
          {% endif %}
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
