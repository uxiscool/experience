---
layout: default
title: Works
---

<div class="container">
  <div class="intro-hero">
    <p>_01_
    I’m Vladimir — UX enthusiast and interaction architect based in Moscow, Russia.<br><br>
    I’m passionate about a systematic approach to design and believe that real product value starts with well-thought-out user journeys. I love working on a wide variety of interfaces, with a special passion for internal tools and complex B2B web services.<br><br>
    My experience covers different project roles: from solo contributor to core team member. I enjoy tackling business tasks, building structure out of chaos, and making digital products truly useful and delightful for people.<br><br>
    Open to collaboration and always excited to solve new challenges.
    </p>
  </div>
</div>
<div class="intro-divider"></div>
<!-- Главные кейсы -->
<div class="featured-cases">
  {% assign featured = site.cases | where: "featured", true %}
  {% for case in featured %}
    <div class="case-card">
      <div class="case-img-wrap">
   <img
  class="case-thumb"
  src="{{ site.baseurl }}{{ case.cover }}"
  alt="{{ case.title }} preview"
  data-images='{{ case.images | jsonify }}'
  data-index="0"
  onclick="openLightbox(this)"
>
      </div>
      <div class="case-meta">
        <a href="{{ case.url }}" class="case-title">{{ case.title }}</a>
        <div class="case-year">{{ case.year }} · {{ case.type }}</div>
        <div class="case-summary">{{ case.summary }}</div>
      </div>
    </div>
  {% endfor %}
</div>
<!-- Лайтбокс -->
<div id="lightbox" class="lightbox" style="display:none;">
  <div class="lightbox-bg" onclick="closeLightbox()"></div>
  <div class="lightbox-content">
    <button class="lightbox-close" onclick="closeLightbox()">&times;</button>
    <button class="lightbox-arrow left" onclick="lightboxPrev()">&larr;</button>
    <img id="lightbox-img" class="lightbox-img" src="">
    <button class="lightbox-arrow right" onclick="lightboxNext()">&rarr;</button>
    <div id="lightbox-caption" class="lightbox-caption"></div>
  </div>
</div>
