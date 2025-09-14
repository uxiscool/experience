---
layout: default
title: Пет-проекты
permalink: /ru/pet-projects/
lang: ru
alt_url: /pet-projects/
---

<div class="pet-meta">
  <div class="case-summary2">
    Сайд-проекты, эксперименты и «маленькие радости», где можно быстро пробовать идеи и выпускать их в мир.
  </div>
</div>

<div class="pp-grid">
  {%- assign items = site.petprojects -%}
  {%- assign with_order = items | where_exp: "it", "it.order" -%}
  {%- assign without_order = items | where_exp: "it", "it.order == nil" -%}
  {%- assign with_order_sorted = with_order | sort: "order" -%}
  {%- assign items_sorted = with_order_sorted | concat: without_order -%}

  {%- for p in items_sorted -%}
    {%- assign first = p.gallery[0] -%}
    {%- assign thumb_src = nil -%}
    {%- if first -%}
      {%- assign tp = first.src | default:first.file -%}
      {%- if tp -%}
        {%- if p.images_base -%}
          {%- assign thumb_src = p.images_base | append: tp -%}
        {%- else -%}
          {%- assign thumb_src = tp -%}
        {%- endif -%}
      {%- endif -%}
    {%- endif -%}

    <article class="pp-card">
      <header class="pp-header">
        {% if p.icon %}<img class="pp-icon" src="{{ site.baseurl }}{{ p.icon }}" alt="">{% endif %}
        <h3 class="pp-title">{{ p.title_ru | default: p.title }}</h3>
      </header>
      <div class="pp-body">
        <div class="pp-media">
          {% if thumb_src %}
            <a class="pp-media-link" href="javascript:void(0)" onclick="openPetGallery({{ forloop.index0 }}, 0)" aria-label="Открыть галерею">
              <img class="lazy-img" decoding="async" data-src="{{ site.baseurl }}{{ thumb_src }}" alt="">
              <noscript><img src="{{ site.baseurl }}{{ thumb_src }}" alt=""></noscript>
            </a>
          {% endif %}
        </div>
        <div class="pp-side">
          <div class="pp-text">
            {% if p.subtitle or p.subtitle_ru %}<div class="pp-subtitle">{{ p.subtitle_ru | default: p.subtitle }}</div>{% endif %}
            {% if p.desc or p.desc_ru %}<div class="pp-desc">{{ p.desc_ru | default: p.desc }}</div>{% endif %}
          </div>
          <div class="pp-footer">
            {% if p.kind %}<div class="pp-kind">{{ p.kind }}</div>{% endif %}
            <div class="pp-links">
              {% if p.store_url and p.store_icon %}
                <a class="pp-store" href="{{ p.store_url }}" target="_blank" rel="noopener">
                  <img src="{{ p.store_icon | prepend: site.baseurl }}" alt="{{ p.store_alt | default: 'Store' }}">
                </a>
              {% endif %}
            </div>
          </div>
        </div>
      </div>
    </article>
  {%- endfor -%}
</div>
