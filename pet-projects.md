---
layout: default
title: Pet projects
permalink: /pet-projects/
lang: en
alt_url: /ru/pet-projects/
---

<div class="pet-meta">
  <div class="case-summary2">
    Side projects, experiments and&nbsp;&ldquo;little joys&rdquo; where you&nbsp;can quickly try&nbsp;out ideas and&nbsp;roll them out into&nbsp;the&nbsp;world.
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
        <h3 class="pp-title">{{ p.title }}</h3>
      </header>
      <div class="pp-body">
        <div class="pp-media">
          {% if thumb_src %}
            <a class="pp-media-link" href="javascript:void(0)" onclick="openPetGallery({{ forloop.index0 }}, 0)" aria-label="Open gallery">
              <img class="lazy-img" decoding="async" data-src="{{ site.baseurl }}{{ thumb_src }}" alt="">
              <noscript><img src="{{ site.baseurl }}{{ thumb_src }}" alt=""></noscript>
            </a>
          {% endif %}
        </div>
        <div class="pp-side">
          <div class="pp-text">
  {% if p.subtitle %}<div class="pp-subtitle">{{ p.subtitle }}</div>{% endif %}
  {% if p.desc %}<div class="pp-desc">{{ p.desc }}</div>{% endif %}

  {%- if p.in_progress -%}
    <div class="pp-inprogress-note" role="note">
      This project is in active development and not public yet.
    </div>
  {%- endif -%}
</div>
<div class="pp-footer">
  {%- if p.in_progress -%}
    <!-- Сверху kind не показываем -->
    <div class="pp-links">
      {% if p.kind %}<div class="pp-kind">{{ p.kind }}</div>{% endif %}
      {# зона стора пустая #}
    </div>
  {%- else -%}
    {% if p.kind %}<div class="pp-kind">{{ p.kind }}</div>{% endif %}
    <div class="pp-links">
      {% if p.store_url and p.store_icon %}
        <a class="pp-store" href="{{ p.store_url }}" target="_blank" rel="noopener">
          <img src="{{ p.store_icon | prepend: site.baseurl }}" alt="{{ p.store_alt | default: 'Store' }}">
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