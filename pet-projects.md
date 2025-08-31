---
layout: default
title: Pet projects
permalink: /pet-projects/
---

<!-- Короткое описание раздела -->
<div class="ppx-meta">
  <div class="case-summary2">
    Side projects, experiments and "little joys" where you can quickly try out ideas and roll them out into the world.
  </div>
</div>

<!-- Сетка карточек -->
<div class="ppx-grid">
  {% assign items = site.petprojects %}

  {% for p in items %}
    {% assign pet_index = forloop.index0 %}

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

    <article class="ppx-card">
      <!-- Шапка -->
      <header class="ppx-head">
        {% if p.icon %}
          <img class="ppx-icon" src="{{ site.baseurl }}{{ p.icon }}" alt="">
        {% endif %}
        <h3 class="ppx-title">{{ p.title }}</h3>
      </header>

      <!-- Медиа слева -->
      <div class="ppx-media">
        {% if thumb_src %}
          {% assign click_url = p.figma | default: p.url %}
          {% if click_url %}
            <a class="ppx-media-link" href="{{ click_url }}" target="_blank" rel="noopener">
          {% endif %}

            <div class="ppx-skel" aria-hidden="true"></div>
            <img class="ppx-img"
                 loading="lazy" decoding="async"
                 src="{{ site.baseurl }}{{ thumb_src }}"
                 alt=""
                 onload="this.classList.add('is-loaded'); this.closest('.ppx-media').classList.add('has-loaded');">

          {% if click_url %}</a>{% endif %}
        {% endif %}
      </div>

      <!-- Текст справа -->
      <div class="ppx-side">
        <div class="ppx-text">
          {% if p.subtitle %}<div class="ppx-subtitle">{{ p.subtitle }}</div>{% endif %}
          {% if p.desc %}<div class="ppx-desc">{{ p.desc }}</div>{% endif %}
        </div>

        <div class="ppx-footer">
          {% if p.kind %}<div class="ppx-kind">{{ p.kind }}</div>{% endif %}
          <div class="ppx-links">
            {% if p.figma %}
              <a class="ppx-store" href="{{ p.figma }}" target="_blank" rel="noopener" aria-label="Open in Figma">
                <img src="{{ site.baseurl }}/ui/stores/figma.svg" alt="Figma">
              </a>
            {% endif %}
            {% if p.stores and p.stores.play %}
              <a class="ppx-store" href="{{ p.stores.play }}" target="_blank" rel="noopener" aria-label="Google Play">
                <img src="{{ site.baseurl }}/ui/stores/googleplay.svg" alt="Google Play">
              </a>
            {% endif %}
            {% if p.stores and p.stores.appstore %}
              <a class="ppx-store" href="{{ p.stores.appstore }}" target="_blank" rel="noopener" aria-label="App Store">
                <img src="{{ site.baseurl }}/ui/stores/appstore.svg" alt="App Store">
              </a>
            {% endif %}
          </div>
        </div>
      </div>
    </article>
  {% endfor %}
</div>