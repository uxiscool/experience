---
layout: default
title: Works
lang: en
alt_url: /ru/
---

<div class="container">
  <div class="intro-hero">
    <p id="intro-line" class="intro-line">
    I’m Vladimir — UX&nbsp;enthusiast and&nbsp;UX/UI designer from Moscow.<br>Here I share selected projects that best reflect my approach to design and user experience.<br><br>
    I like when interfaces feel honest and free of clutter. I value simplicity, clarity, and the sense that a product is truly made for people.<br><br>
I enjoy turning complex services into something clear and approachable. Finding structure in chaos and shaping solutions that help businesses while delighting users is what motivates me most.<br><br>
For me, design is not only about interfaces but also about relationships. I value teamwork, stay curious about science and technology, and like looking at things from different angles to discover new connections.<br><br>
Open to collaboration and always excited for new challenges.
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
            <a href="{{ site.baseurl }}/cases/#case-{{ case_anchor }}" class="case-title2">{{ case.title }}</a>
          </div>

          <!-- Мета: каждая часть в своем span; год для мобильной версии -->
          <div class="case-meta2-inline">
            <span class="case-year-inline">{{ case.year }}</span>
            {% if case.company %}<span class="case-company">{{ case.company }}</span>{% endif %}
            {% if case.type %}<span class="case-type">{{ case.type }}</span>{% endif %}
          </div>
          <div class="case-summary2">{{ case.summary }}</div>
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
