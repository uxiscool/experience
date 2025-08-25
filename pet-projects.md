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
    <a class="pp-item" href="javascript:void(0)" onclick="openPetGallery({{ pet_index }}, 0)">
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
              <img src="{{ site.baseurl }}{{ thumb_src }}" alt="">
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
                  <img src="{{ site.baseurl }}/ui/stores/figma.svg" alt="Figma">
                {% endif %}
                {% if p.stores and p.stores.play %}
                  <img src="{{ site.baseurl }}/ui/stores/googleplay.svg" alt="Google Play">
                {% endif %}
                {% if p.stores and p.stores.appstore %}
                  <img src="{{ site.baseurl }}/ui/stores/appstore.svg" alt="App Store">
                {% endif %}
              </div>
            </div>
          </div>
        </div>
      </article>
    </a>
  {% endfor %}
{%- assign total = items | size -%}
{%- if total | modulo: 2 == 1 -%}
  <!-- Пустая плашка-заполнитель для выравнивания второй колонки последней строки -->
  <div class="pp-filler" aria-hidden="true"></div>
{%- endif -%}
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
