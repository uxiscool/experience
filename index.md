---
layout: default
title: Works
---

<div class="container">
  <div class="intro-hero">
    <p>
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
        {% for img in case.images %}
        {% unless img.home == false %}
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
          {% endunless %}
        {% endfor %}
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
    <img id="lightbox-img" class="lightbox-img" src="">
    <button class="lightbox-arrow right" onclick="lightboxNext()" aria-label="Next">
      <img src="{{ site.baseurl }}/ui/lightbox_arrow_right.svg" width="36" height="36" alt="Next">
    </button>
    <div id="lightbox-caption" class="lightbox-caption"></div>
  </div>
</div>
