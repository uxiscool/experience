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

    {%- assign _title = p.title_ru | to_s | strip | default: p.title -%}
    {%- assign _subtitle = p.subtitle_ru | to_s | strip | default: p.subtitle -%}
    {%- assign _desc = p.desc_ru | to_s | strip | default: p.desc -%}
    {%- assign _kind = p.kind_ru | default: p.kind -%}
    {%- assign _store_alt = p.store_alt_ru | default: p.store_alt | default: 'Магазин' -%}

    <article class="pp-card">
      <header class="pp-header">
        {% if p.icon %}<img class="pp-icon" src="{{ site.baseurl }}{{ p.icon }}" alt="">{% endif %}
        <h3 class="pp-title">{{ _title }}</h3>
      </header>
      <div class="pp-body">
        <div class="pp-media">
          {% if thumb_src %}
            <a class="pp-media-link" href="javascript:void(0)" onclick="openPetGallery({{ forloop.index0 }}, 0)" aria-label="Открыть галерею">
              <img class="lazy-img" decoding="async" data-src="{{ site.baseurl }}{{ thumb_src }}" alt="{{ _title }}">
              <noscript><img src="{{ site.baseurl }}{{ thumb_src }}" alt="{{ _title }}"></noscript>
            </a>
          {% endif %}
        </div>
        <div class="pp-side">
          <div class="pp-text">
  {% if _subtitle %}<div class="pp-subtitle">{{ _subtitle }}</div>{% endif %}
  {% if _desc %}<div class="pp-desc">{{ _desc }}</div>{% endif %}

  {%- if p.in_progress -%}
    <div class="pp-inprogress-note" role="note">
      Проект в разработке и ещё не выложен публично.
    </div>
  {%- endif -%}
</div>
<div class="pp-footer">
  {%- if p.in_progress -%}
    <div class="pp-kind" style="display:none;"></div>
    <div class="pp-links">
      {% if _kind %}<span class="pp-kind pp-kind--as-store">{{ _kind }}</span>{% endif %}
    </div>
  {%- else -%}
    {% if _kind %}<div class="pp-kind">{{ _kind }}</div>{% endif %}
    <div class="pp-links">
      {% if p.store_url and p.store_icon %}
        <a class="pp-store" href="{{ p.store_url }}" target="_blank" rel="noopener">
          <img src="{{ p.store_icon | prepend: site.baseurl }}" alt="{{ _store_alt }}">
        </a>
      {% endif %}
    </div>
  {%- endif -%}
</div>
        </div>
      </div>
    </article>
  {%- endfor -%}
</div>