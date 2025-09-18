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
    {%- comment -%}
      GitHub Pages-safe: избегаем where_exp. Просто сортируем внутри года по "order".
      Элементы без order окажутся первыми; если хочешь — можно вывести их вторым циклом.
    {%- endcomment -%}
    {% assign items_sorted = g.items | sort: "order" %}
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

        {# ——— Stages ——— #}
        {% if c.stages %}
          {% for st in c.stages %}

            {% if st.name or st.desc or st.desc_ru %}
              <div class="stage-header">
                {% comment %} st.name один на обе локали {% endcomment %}
                {% if st.name %}<h3 class="case-title2">{{ st.name }}</h3>{% endif %}
                {% if page.lang == 'ru' and st.desc_ru %}
                  <div class="stage-summary">{{ st.desc_ru }}</div>
                {% elsif st.desc %}
                  <div class="stage-summary">{{ st.desc }}</div>
                {% endif %}
              </div>
            {% endif %}

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

      </div> <!-- /.case-block -->
    {% endfor %}
  {% endfor %}
</div> <!-- /.featured-cases -->