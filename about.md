---
layout: default
title: About
permalink: /about/
---

<h1>About</h1>
<p>Здесь будет раздел «Обо мне».</p>
<br>

<!-- ===== Skills Section ===== -->
<section class="skills-section">
  <h2 class="skills-heading">Skills</h2>

  <div class="skills-columns">
    <!-- Soft column -->
    <div class="skills-col">
      <h3 class="skills-title">Soft</h3>
      <div class="skills skills-grid">
        {% for s in site.data.skills.soft %}
          <span
            class="pill tilt mono tooltip slide-in-left"
            data-tip="{{ s.note | default: '—' }}"
            style="animation-delay: {{ forloop.index0 | times: 80 }}ms"
          >{{ s.name }}</span>
        {% endfor %}
      </div>
    </div>

    <!-- Hard column -->
    <div class="skills-col">
      <h3 class="skills-title">Hard</h3>
      <div class="skills skills-grid">
        {% for s in site.data.skills.hard %}
          <span
            class="pill tilt mono tooltip slide-in-right"
            data-tip="{{ s.note | default: '—' }}"
            style="animation-delay: {{ forloop.index0 | times: 80 }}ms"
          >{{ s.name }}</span>
        {% endfor %}
      </div>
    </div>
  </div>
</section>
