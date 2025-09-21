---
layout: default
title: Works
lang: en
alt_url: /ru/
---

<div class="container">
  <div class="intro-hero">
    <p id="intro-line" class="intro-line">
    I’m Vladimir — UX&nbsp;enthusiast and&nbsp;UX/UI designer from&nbsp;Moscow.<br>Here I&nbsp;share selected projects that&nbsp;best reflect my&nbsp;approach to&nbsp;design and&nbsp;user experience.<br><br>
    I like when&nbsp;interfaces feel honest and&nbsp;free of&nbsp;clutter. I&nbsp;value simplicity, clarity, and&nbsp;the&nbsp;sense that&nbsp;a&nbsp;product is&nbsp;truly made for&nbsp;people.<br><br>
I&nbsp;enjoy turning complex services into&nbsp;something clear and&nbsp;approachable. Finding structure in&nbsp;chaos and&nbsp;shaping solutions that&nbsp;help businesses while delighting users is&nbsp;what motivates me&nbsp;most.<br><br>
For me, design is&nbsp;not&nbsp;only about interfaces but&nbsp;also about relationships. I&nbsp;value teamwork, stay curious about science and&nbsp;technology, and&nbsp;like looking at&nbsp;things from&nbsp;different angles to&nbsp;discover new connections.<br><br>
Open to&nbsp;collaboration and&nbsp;always excited for&nbsp;new challenges.
    </p>
    <!-- Градиентный разделитель -->
    <div class="intro-divider"></div>
  </div>
</div>

<!-- Главные кейсы -->
<div class="featured-cases">
  {% assign featured = site.cases | where: "featured", true %}
  {%- comment -%}
    Сортировка:
    1) Группируем по году; группы сортируем по 'name' (год) по убыванию.
    2) Внутри каждого года сначала элементы с заданным 'order' (по возрастанию),
       затем без 'order' в исходном порядке.
  {%- endcomment -%}
  {% assign groups = featured | group_by: "year" %}
  {% assign groups_sorted = groups | sort: "name" | reverse %}

  {% for g in groups_sorted %}
    {% assign group_items = g.items %}
    {% assign with_order = group_items | where_exp: "it", "it.order" %}
    {% assign without_order = group_items | where_exp: "it", "it.order == nil" %}
    {% assign with_order_sorted = with_order | sort: "order" %}
    {% assign items_sorted = with_order_sorted | concat: without_order %}
    {% for case in items_sorted %}
      {% assign case_index = 0 %}
      {% for c in site.cases %}
        {% if c.url == case.url %}
          {% assign case_index = forloop.index0 %}
          {% break %}
        {% endif %}
      {% endfor %}
      <div class="case-block">
        <div class="case-year-rail">{{ case.year }}</div>
        <div class="case-meta2">
          <div class="case-title-row">
          {% assign case_anchor = case.url | replace:'/cases/','' | replace:'/','' | downcase %}
<a href="{{ site.baseurl }}{% if page.lang == 'ru' %}/ru{% endif %}/cases/#case-{{ case_anchor }}" class="case-title2">{{ case.title }}</a>
          </div>
          <div class="case-meta2-inline">
            <span class="case-year-inline">{{ case.year }}</span>
            {% if case.company %}<span class="case-company">{{ case.company }}</span>{% endif %}
            {% assign _type = case.type %}
{% if _type %}<span class="case-type">{{ _type }}</span>{% endif %}
          </div>
          {% assign _summary = case.summary %}
<div class="case-summary2">{{ _summary }}</div>
        </div>
        <div class="case-gallery">
          {% assign idx = 0 %}
          {% if case.stages %}
            {% for st in case.stages %}
              {% for img in st.images %}
                {% unless img.home == false %}
                  {% assign img_src = img.src | default: img.file | prepend: case.images_base | default: img.src %}
                  <div class="case-gallery-item">
                    <img
                      class="case-thumb2 lazy-img"
                      data-src="{{ site.baseurl }}{{ img_src }}"
                      alt="{{ img.caption | escape }}"
                      decoding="async"
                      onclick="openHomeGallery({{ case_index }}, {{ idx }})">
                    <noscript><img src="{{ site.baseurl }}{{ img_src }}" alt="{{ img.caption | escape }}"></noscript>
                    {% if img.caption %}<div class="case-thumb-caption">{{ img.caption }}</div>{% endif %}
                  </div>
                  {% assign idx = idx | plus: 1 %}
                {% endunless %}
              {% endfor %}
            {% endfor %}
          {% else %}
            {% for img in case.images %}
              {% unless img.home == false %}
                <div class="case-gallery-item">
                  <img
                    class="case-thumb2 lazy-img"
                    data-src="{{ site.baseurl }}{{ img_src }}"
                    alt="{{ img.caption | escape }}"
                    decoding="async"
                    onclick="openHomeGallery({{ case_index }}, {{ forloop.index0 }})">
                  <noscript><img src="{{ site.baseurl }}{{ img_src }}" alt="{{ img.caption | escape }}"></noscript>
                  {% if img.caption %}<div class="case-thumb-caption">{{ img.caption }}</div>{% endif %}
                </div>
              {% endunless %}
            {% endfor %}
          {% endif %}
        </div>
      </div>
    {% endfor %}
  {% endfor %}
</div>

<script>
(function(){
  var h = new Date().getHours();
  var greet = (h < 5)  ? 'Late night greetings'
            : (h < 12) ? 'Good morning'
            : (h < 18) ? 'Hello there'
            :            'Good evening';

  var el = document.getElementById('intro-line');
  if (!el) return;
  var text = el.innerHTML;
  el.innerHTML = '<span class="greet">'+greet+'</span> 🖖 ' + text;
})();
</script>
