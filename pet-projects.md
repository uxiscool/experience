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

    {% assign first = p.gallery[0] %}
    {% assign thumb_src = nil %}
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

        <!-- новый упорядоченный макет -->
        <div class="pet-layout">
          <div class="pet-media">
            {% if thumb_src %}
              <img class="pet-media-img" src="{{ site.baseurl }}{{ thumb_src }}" alt="">
            {% else %}
              <div class="pet-media-empty"></div>
            {% endif %}
          </div>

          <div class="pet-info">
            <header class="pet-head-row">
              <img class="pet-icon" src="{{ site.baseurl }}{{ p.icon }}" alt="">
              <h3 class="pet-title">{{ p.title }}</h3>
              {% if p.kind %}<span class="pet-type">{{ p.kind }}</span>{% endif %}
            </header>

            <div class="pet-subtitle">{{ p.subtitle }}</div>
            {% if p.desc %}<div class="pet-desc">{{ p.desc }}</div>{% endif %}

            {% if p.tags and p.tags.size > 0 %}
              <ul class="pet-tags">
                {% for t in p.tags %}<li class="pet-tag">{{ t }}</li>{% endfor %}
              </ul>
            {% endif %}

            <div class="pet-actions">
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
              {% if p.cta and p.cta.url %}
                <a class="pet-cta" href="{{ p.cta.url }}" target="_blank" rel="noopener" onclick="event.stopPropagation()">
                  {{ p.cta.label | default: "Open project" }}
                </a>
              {% endif %}
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
