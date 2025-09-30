---
layout: default
title: Кейсы
permalink: /ru/cases/
lang: ru
alt_url: /cases/
---

<div class="featured-cases">
  {%- assign sorted = site.cases | sort: "year" | reverse -%}
  {%- assign groups = sorted | group_by: "year" -%}
  {%- for g in groups -%}
    {%- assign items_by_order = g.items | sort: "order" -%}

    {%- for c in items_by_order -%}{% if c.order %}
      <div class="case-block">
        <div class="case-year-rail">{{ c.year }}</div>

        <div class="case-meta2">
          <div class="case-title-row">
            <h2 class="case-title3">{{ c.title_ru | default: c.title }}</h2>
          </div>

          <div class="case-meta2-inline">
            {% if c.year %}<span class="case-year-inline">{{ c.year }}</span>{% endif %}
            {% if c.company %}<span class="case-company">{{ c.company }}</span>{% endif %}
            {% assign _type = c.type_ru | default: c.type %}
            {% if _type %}<span class="case-type">{{ _type }}</span>{% endif %}
          </div>

          <div class="case-summary2">{{ c.summary_ru | default: c.summary }}</div>
        </div>

        {% if c.stages %}
          {% for st in c.stages %}
            {% assign stage_desc = st.desc_ru | default: st.desc %}
            {% if stage_desc %}
              <div class="stage-summary">{{ stage_desc }}</div>
            {% endif %}

            <div class="case-gallery">
              {% for img in st.images %}
{% assign _ru = img.file_ru | to_s | strip %}
{% if _ru != '' %}
  {% assign _src = (c.images_base_ru | default: c.images_base) | append: _ru %}
{% else %}
  {% assign _src = c.images_base | append: img.file %}
{% endif %}
{% assign _cap = img.caption_ru | default: img.caption %}
                <div class="case-gallery-item">
                  <img class="case-thumb2 lazy-img" data-src="{{ site.baseurl }}{{ _src }}" alt="">
                  {% if _cap %}<div class="case-thumb-caption" title="{{ _cap | strip }}">
  {{ _cap | strip_html | replace: '&nbsp;', ' ' | strip }}
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
            <h2 class="case-title3">{{ c.title_ru | default: c.title }}</h2>
          </div>

          <div class="case-meta2-inline">
            {% if c.year %}<span class="case-year-inline">{{ c.year }}</span>{% endif %}
            {% if c.company %}<span class="case-company">{{ c.company }}</span>{% endif %}
            {% assign _type = c.type_ru | default: c.type %}
            {% if _type %}<span class="case-type">{{ _type }}</span>{% endif %}
          </div>

          <div class="case-summary2">{{ c.summary_ru | default: c.summary }}</div>
        </div>

        {% if c.stages %}
          {% for st in c.stages %}
            {% assign stage_desc = st.desc_ru | default: st.desc %}
            {% if stage_desc %}
              <div class="stage-summary">{{ stage_desc }}</div>
            {% endif %}

            <div class="case-gallery">
              {% for img in st.images %}
              {% assign _ru = img.file_ru | to_s | strip %}
{% if _ru != '' %}
  {% assign _src = (c.images_base_ru | default: c.images_base) | append: _ru %}
{% else %}
  {% assign _src = c.images_base | append: img.file %}
{% endif %}
{% assign _cap = img.caption_ru | default: img.caption %}
                <div class="case-gallery-item">
                  <img class="case-thumb2 lazy-img" data-src="{{ site.baseurl }}{{ _src }}" alt="">
                  {% if _cap %}<div class="case-thumb-caption" title="{{ _cap | strip }}">
  {{ _cap | strip_html | replace: '&nbsp;', ' ' | strip }}
</div>
              {% endfor %}
            </div>
          {% endfor %}
        {% endif %}
      </div>
    {% endunless %}{%- endfor -%}
  {%- endfor -%}
</div>
