---
layout: default
title: Работы
permalink: /ru/
lang: ru
alt_url: /
---

<div class="container">
  <div class="intro-hero">
    <p id="intro-line" class="intro-line">
    На связи Владимир, UX/UI-дизайнер из&nbsp;Москвы.<br>Здесь я&nbsp;делюсь примерами своих проектов, которые лучше всего показывают мой подход к&nbsp;дизайну и&nbsp;опыту пользователя.<br><br>
   Мне нравится, когда интерфейсы работают честно и&nbsp;без&nbsp;лишнего шума. Я&nbsp;ценю простоту, ясность и&nbsp;ощущение, что&nbsp;продукт сделан для&nbsp;людей.<br><br>
Люблю, когда сложные сервисы становятся простыми и&nbsp;понятными. Интересно искать структуру в&nbsp;хаосе и&nbsp;находить решения, которые одновременно помогают бизнесу и&nbsp;радуют пользователей.<br><br>Для&nbsp;меня дизайн — это не&nbsp;только про&nbsp;интерфейсы, но&nbsp;и&nbsp;про&nbsp;отношения. Я&nbsp;ценю сотрудничество в&nbsp;командах, интересуюсь наукой и&nbsp;технологиями, люблю смотреть на&nbsp;вещи под&nbsp;разными углами и&nbsp;находить новые связи.<br><br>Открыт к&nbsp;совместной работе и&nbsp;всегда рад новым вызовам.</p>
    <!-- Градиентный разделитель -->
    <div class="intro-divider"></div>
  </div>
</div>
<!-- Главные кейсы -->
<div class="featured-cases">
  {% assign featured = site.cases | where: "featured", true %}
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
{% assign _title = case.title_ru | default: case.title %}
<a href="{{ site.baseurl }}/ru/cases/#case-{{ case_anchor }}" class="case-title2">{{ _title }}</a>
          </div>
          <!-- Мета: каждая часть в своем span; год для мобильной версии -->
          <div class="case-meta2-inline">
            <span class="case-year-inline">{{ case.year }}</span>
            {% if case.company %}<span class="case-company">{{ case.company }}</span>{% endif %}
            {% if page.lang == 'ru' %}
  {% assign _type = case.type_ru | default: case.type %}
{% else %}
  {% assign _type = case.type %}
{% endif %}
{% if _type %}<span class="case-type">{{ _type }}</span>{% endif %}
          </div>
          {% assign _summary = case.summary_ru | default: case.summary %}
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
    {% assign img_src = img.src | default: img.file | prepend: case.images_base | default: img.src %}
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
  var greet = (h < 5)  ? 'Доброй ночи'
            : (h < 12) ? 'Доброго утра'
            : (h < 18) ? 'Привет'
            :            'Хорошего вечера';

  var el = document.getElementById('intro-line');
  if (!el) return;
  var text = el.innerHTML;
  el.innerHTML = '<span class="greet">'+greet+'</span> 🖖 ' + text;
})();
</script>
