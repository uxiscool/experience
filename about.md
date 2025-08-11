---
layout: default
title: About
permalink: /about/
---

<h1>About</h1>
<p>Здесь будет раздел «Обо мне».</p>
<br>
<div class="skills skills-grid">
<!-- вариант1 -->
  {% for s in site.data.skills.hard %}
    <span class="chip tooltip" data-tip="{{ s.note | default: '—' }}">{{ s.name }}</span>
  {% endfor %}
</div>
<br>
<div class="skills">
  {% for s in site.data.skills.hard %}
    <div class="kv fadein" style="animation-delay: {{ forloop.index0 | times: 80 }}ms">
      <div>{{ s.name }}</div><div class="small">L{{ s.level }}</div>
      <div class="bar" style="grid-column:1/-1"><i style="--w: {{ s.level | times: 20 }}%"></i></div>
    </div>
  {% endfor %}
</div>
<br>
<div class="skills hscroll">
  {% for s in site.data.skills.hard %}<span class="chip">{{ s.name }}</span>{% endfor %}
  {% for s in site.data.skills.soft %}<span class="chip outline">{{ s.name }}</span>{% endfor %}
</div>
<br>
<div class="skills" style="columns: 2; column-gap: 2rem">
  {% for s in site.data.skills.hard %}
    <div class="check"><span>✓</span><span>{{ s.name }}</span></div>
  {% endfor %}
</div>
