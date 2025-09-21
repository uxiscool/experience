---
layout: default
title: Cases
permalink: /cases/
lang: en
alt_url: /ru/cases/
---

<div class="featured-cases">
  {%- assign groups = site.cases | group_by: "year" | sort: "name" | reverse -%}
  {%- for g in groups -%}
    {%- assign items_by_order = g.items | sort: "order" -%}
    {%- for c in items_by_order -%}{% if c.order %}
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
          {% if c.summary %}
            <div class="case-summary2">{{ c.summary }}</div>
          {% endif %}
        </div>
        {% if c.stages %}
          {% for st in c.stages %}
            {% if st.desc %}
              <div class="stage-summary">{{ st.desc }}</div>
            {% endif %}
            <div class="case-gallery">
  {% for img in st.images %}
    {% if page.lang == 'ru' %}
      {% assign _base = c.images_base_ru | default: c.images_base %}
    {% else %}
      {% assign _base = c.images_base %}
    {% endif %}
    {% if page.lang == 'ru' %}
      {% assign _rel = img.src_ru | default: img.file_ru | default: img.src | default: img.file %}
      {% assign _caption = img.caption_ru | default: img.caption %}
    {% else %}
      {% assign _rel = img.src | default: img.file %}
      {% assign _caption = img.caption %}
    {% endif %}
    {% if _base %}
      {% assign _src = _base | append: _rel %}
    {% else %}
      {% assign _src = _rel %}
    {% endif %}
    <div class="case-gallery-item">
      <img class="case-thumb2 lazy-img" data-src="{{ site.baseurl }}{{ _src }}" alt="">
      {% if _caption %}<div class="case-thumb-caption">{{ _caption }}</div>{% endif %}
    </div>
  {% endfor %}
</div>
          {% endfor %}
        {% endif %}
      </div>
    {% endif %}{%- endfor -%}
    {%- for c in items_by_order -%}{% unless c.order %}
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
          {% if c.summary %}
            <div class="case-summary2">{{ c.summary }}</div>
          {% endif %}
        </div>
        {% if c.stages %}
          {% for st in c.stages %}
            {% if st.desc %}
              <div class="stage-summary">{{ st.desc }}</div>
            {% endif %}
            <div class="case-gallery">
  {% for img in st.images %}
    {% if page.lang == 'ru' %}
      {% assign _base = c.images_base_ru | default: c.images_base %}
    {% else %}
      {% assign _base = c.images_base %}
    {% endif %}
    {% if page.lang == 'ru' %}
      {% assign _rel = img.src_ru | default: img.file_ru | default: img.src | default: img.file %}
      {% assign _caption = img.caption_ru | default: img.caption %}
    {% else %}
      {% assign _rel = img.src | default: img.file %}
      {% assign _caption = img.caption %}
    {% endif %}
    {% if _base %}
      {% assign _src = _base | append: _rel %}
    {% else %}
      {% assign _src = _rel %}
    {% endif %}
    <div class="case-gallery-item">
      <img class="case-thumb2 lazy-img" data-src="{{ site.baseurl }}{{ _src }}" alt="">
      {% if _caption %}<div class="case-thumb-caption">{{ _caption }}</div>{% endif %}
    </div>
  {% endfor %}
</div>
          {% endfor %}
        {% endif %}
      </div>
    {% endunless %}{%- endfor -%}
  {%- endfor -%}
</div>