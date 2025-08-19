---
layout: default
title: Cases
permalink: /cases/
---

<!-- Все кейсы подряд в том же лейауте, что и на главной -->
<div class="featured-cases">
  {% assign allcases = site.cases | sort: 'year' | reverse %}
  {% for case in allcases %}
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
{% if case.stages %}
  {% for st in case.stages %}
    {% if st.desc %}
      <div class="case-summary2">{{ st.desc }}</div>
    {% endif %}
    <div class="case-gallery">
      {% for img in st.images %}
        <div class="case-gallery-item">
          <img
            class="case-thumb2"
            src="{{ site.baseurl }}{{ img.src }}"
            alt="{{ img.caption | escape }}"
            loading="lazy"
            decoding="async"
            onclick="openCaseGallery({{ forloop.parentloop.index0 }}, {{ img.index | default: forloop.index0 }})"
          >
          {% if img.caption %}
            <div class="case-thumb-caption">{{ img.caption }}</div>
          {% endif %}
        </div>
      {% endfor %}
    </div>
  {% endfor %}
{% else %}
  <div class="case-gallery">
    {% for img in case.images %}
      <div class="case-gallery-item">
        <img
          class="case-thumb2"
          src="{{ site.baseurl }}{{ img.src }}"
          alt="{{ img.caption | escape }}"
          loading="lazy"
          decoding="async"
          onclick="openCaseGallery({{ forloop.parentloop.index0 }}, {{ forloop.index0 }})"
        >
        {% if img.caption %}
          <div class="case-thumb-caption">{{ img.caption }}</div>
        {% endif %}
      </div>
    {% endfor %}
  </div>
{% endif %}

    </div>
  {% endfor %}
</div>
<!-- Лайтбокс (тот же, что на index) -->
<div id="lightbox" class="lightbox" style="display:none;">
  <div class="lightbox-bg" onclick="closeLightbox()"></div>
  <div class="lightbox-content">
    <button class="lightbox-close" onclick="closeLightbox()" aria-label="Close">
      <img src="{{ site.baseurl }}/ui/lightbox_close.svg" width="36" height="36" alt="Close">
    </button>
    <button class="lightbox-arrow left" onclick="lightboxPrev()" aria-label="Previous">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_left.svg" width="36" height="36" alt="Prev">
    </button>
    <img id="lightbox-img" class="lightbox-img" src="">
    <button class="lightbox-arrow right" onclick="lightboxNext()" aria-label="Next">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_right.svg" width="36" height="36" alt="Next">
    </button>
    <div id="lightbox-caption" class="lightbox-caption"></div>
  </div>
</div>
