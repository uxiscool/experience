---
layout: default
title: Cases
permalink: /cases/
lang: en
alt_url: /ru/cases/
---

<div class="featured-cases">
  {% assign groups = site.cases | group_by: "year" | sort: "name" | reverse %}
  {% for g in groups %}
    {% assign group_items = g.items %}
    {% assign with_order = group_items | where_exp: "it", "it.order" %}
    {% assign without_order = group_items | where_exp: "it", "it.order == nil" %}
    {% assign with_order_sorted = with_order | sort: "order" %}
    {% assign items_sorted = with_order_sorted | concat: without_order %}

    {% for c in items_sorted %}
      <div class="case-block">
        <div class="case-year-rail">{{ c.year }}</div>

        <div class="case-meta2">
          <div class="case-title-row">
            <h2 class="case-title3">{{ c.title }}</h2>
          </div>

          <div class="case-meta2-inline">
            {% if c.year %}<span class="case-year-inline">{{ c.year }}</span>{% endif %}
            {% if c.company %}<span class="case-company">{{ c.company }}</span>{% endif %}
            {% if c.type %}<span class="case-type">{{ c.type }}</span>{% endif %}
          </div>

          {% if c.summary %}<div class="case-summary2">{{ c.summary }}</div>{% endif %}
        </div>

{% if c.stages %}
  {% for st in c.stages %}

    <div class="stage-header">
      {% if page.lang == 'ru' %}
        {% if st.name %}<h3 class="case-title2">{{ st.name }}</h3>{% endif %}
        {% if st.desc_ru %}<div class="stage-summary">{{ st.desc_ru }}</div>{% endif %}
      {% else %}
        {% if st.name %}<h3 class="case-title2">{{ st.name }}</h3>{% endif %}
        {% if st.desc %}<div class="stage-summary">{{ st.desc }}</div>{% endif %}
      {% endif %}
    </div>

    <div class="case-gallery">
      {% for img in st.images %}
        {% assign src = img.src | default: img.file | prepend: c.images_base | default: img.src %}
        <div class="case-gallery-item">
          <img class="case-thumb2 lazy-img" data-src="{{ site.baseurl }}{{ src }}" alt="">
          {% if page.lang == 'ru' and img.caption_ru %}
            <div class="case-thumb-caption">{{ img.caption_ru }}</div>
          {% elsif img.caption %}
            <div class="case-thumb-caption">{{ img.caption }}</div>
          {% endif %}
        </div>
      {% endfor %}
    </div>

  {% endfor %}
{% endif %}

</div>