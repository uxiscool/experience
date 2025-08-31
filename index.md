---
layout: default
title: Works
---

<div class="container">
  <div class="intro-hero">
    <p id="intro-line" class="intro-line">
    I’m Vladimir — UX&nbsp;enthusiast and&nbsp;interaction architect based in&nbsp;Moscow, Russia.<br><br>
    I’m&nbsp;passionate about a&nbsp;systematic approach to&nbsp;design and&nbsp;believe that real product value starts with well-thought-out user journeys.<br>I&nbsp;love working on&nbsp;a&nbsp;wide variety of&nbsp;interfaces, with a&nbsp;special passion for&nbsp;internal tools and&nbsp;complex B2B web&nbsp;services.<br><br>
    My&nbsp;experience covers different project roles: from solo contributor to&nbsp;core team member. I&nbsp;enjoy tackling business tasks, building structure out&nbsp;of&nbsp;chaos, and&nbsp;making digital products truly useful and&nbsp;delightful for&nbsp;people.<br><br>
    Open to&nbsp;collaboration and&nbsp;always excited to&nbsp;solve new&nbsp;challenges.
    </p>
    <!-- Градиентный разделитель -->
    <div class="intro-divider"></div>
  </div>
</div>
<!-- Главные кейсы -->
<div class="featured-cases">
  {% assign featured = site.cases | where: "featured", true %}
  {% for case in featured %}
    {% assign case_index = 0 %}
    {% for c in site.cases %}
      {% if c.url == case.url %}
        {% assign case_index = forloop.index0 %}
        {% break %}
      {% endif %}
    {% endfor %}
    <div class="case-block">
      <div class="case-meta2">
        <div class="case-title-row">
          <a href="{{ case.url }}" class="case-title2">{{ case.title }}</a>
        </div>
        <div class="case-meta2-inline">
          {{ case.year }}
          {% if case.company %} · {{ case.company }}{% endif %}
          {% if case.type %} · {{ case.type }}{% endif %}
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
  <div class="case-img-wrap">
    <div class="img-skel" aria-hidden="true"></div>
    <img
      class="case-thumb2 lazy-img"
      loading="lazy" decoding="async"
      data-src="{{ site.baseurl }}{{ img_src }}"
      alt="{{ img.caption | escape }}"
      onclick="openHomeGallery({{ case_index }}, {{ idx }})">
    <noscript>
      <img class="case-thumb2"
           src="{{ site.baseurl }}{{ img_src }}"
           alt="{{ img.caption | escape }}">
    </noscript>
  </div>
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
  <div class="case-img-wrap">
    <div class="img-skel" aria-hidden="true"></div>
    <img
      class="case-thumb2 lazy-img"
      loading="lazy" decoding="async"
      data-src="{{ site.baseurl }}{{ img.src }}"
      alt="{{ img.caption | escape }}"
      onclick="openHomeGallery({{ case_index }}, {{ forloop.index0 }})">
    <noscript>
      <img class="case-thumb2"
           src="{{ site.baseurl }}{{ img.src }}"
           alt="{{ img.caption | escape }}">
    </noscript>
  </div>
  {% if img.caption %}<div class="case-thumb-caption">{{ img.caption }}</div>{% endif %}
</div>
      {% endunless %}
    {% endfor %}
  {% endif %}
</div>
    </div>
  {% endfor %}
</div>
<!-- Лайтбокс (один для всех проектов) -->
<div id="lightbox" class="lightbox" style="display:none;">
  <div class="lightbox-bg" onclick="closeLightbox()"></div>
  <div class="lightbox-content">
    <button class="lightbox-close" onclick="closeLightbox()" aria-label="Close">
      <img src="{{ site.baseurl }}/ui/lightbox_close.svg" width="36" height="36" alt="Close">
    </button>
    <button class="lightbox-arrow left" onclick="lightboxPrev()" aria-label="Previous">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_left.svg" width="36" height="36" alt="Prev">
    </button>
    <div class="lightbox-stage">
  <img id="lightbox-img" class="lightbox-img" src="">
    {% include lightbox_loader.html %}
</div>
    <button class="lightbox-arrow right" onclick="lightboxNext()" aria-label="Next">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_right.svg" width="36" height="36" alt="Next">
    </button>
    <div id="lightbox-caption" class="lightbox-caption"></div>
    <div id="lightbox-thumbs" class="lightbox-thumbs-wrap" aria-label="Gallery thumbnails">
  <div class="lightbox-thumbs" id="lightbox-thumbs-row"></div>
</div>
  </div>
</div>
<script>
(function(){
  // Локальное время пользователя
  var h = new Date().getHours();
  var greet = (h < 5)  ? 'Late night greetings'
            : (h < 12) ? 'Good morning'
            : (h < 18) ? 'Hello there'
            :            'Good evening';

  var el = document.getElementById('intro-line');
  if (!el) return;

  // Не ломаем существующую типографику — просто префикс с тире
  var text = el.innerHTML;
  el.innerHTML = '<span class="greet">'+greet+'</span> 🖖 ' + text;
})();
</script>
