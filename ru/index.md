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
    Я Владимир, UX/UI-дизайнер из Москвы.<br><br>
    Я сторонник системного подхода к пользовательскому опыту. Уверен, что настоящая ценность продукта или отдельных его функций выявляется на discovery-этапе и благодаря чётко продуманной логике user flow.<br><br>
    Больше всего люблю работать со сложными веб-сервисами: многослойная структура, таблицы, связи, роли. Быстро погружаюсь в новые домены и адаптирую свой опыт в разных фреймворках под конкретные новые продукты и даже команды.<br><br>
    За годы работы был и единственным исполнителем, и ключевым участником команды. У меня хорошо получается соотносить бизнес-задачи с потребностями пользователей, находить структуру в хаосе и делать цифровые продукты удобными и полезными для людей.<br>Открыт к совместной работе и всегда за новые вызовы.</p>
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
