---
layout: default
title: About
permalink: /about/
---

<h1>About</h1>
<p>Здесь будет раздел «Обо мне».</p>
<br>

<div class="skills skills-grid">
  {% for s in site.data.skills.hard %}
    <span class="chip tooltip" data-tip="{{ s.note | default: '—' }}">{{ s.name }}</span>
  {% endfor %}
</div>
<br>
<div class="skills">
  <details open><summary><strong>Hard skills</strong></summary>
    <div class="skills-grid" style="margin-top:.6rem">
      {% for s in site.data.skills.hard %}<span class="chip">{{ s.name }}</span>{% endfor %}
    </div>
  </details>
  <details><summary><strong>Soft skills</strong></summary>
    <div class="skills-grid" style="margin-top:.6rem">
      {% for s in site.data.skills.soft %}<span class="chip outline">{{ s.name }}</span>{% endfor %}
    </div>
  </details>
</div>
<br>
<div class="skills">
  <input id="t1" type="radio" name="tab" checked hidden>
  <input id="t2" type="radio" name="tab" hidden>
  <div class="row" style="margin-bottom:.6rem">
    <label class="pill" for="t1">Hard</label>
    <label class="pill" for="t2">Soft</label>
  </div>
  <div style="display: none" class="hard">{% for s in site.data.skills.hard %}<span class="chip"> {{ s.name }}</span>{% endfor %}</div>
  <div style="display: none" class="soft">{% for s in site.data.skills.soft %}<span class="chip outline">{{ s.name }}</span>{% endfor %}</div>
  <style>
    #t1:checked ~ .hard { display:flex; gap:.6rem; flex-wrap:wrap }
    #t1:checked ~ .soft { display:none }
    #t2:checked ~ .hard { display:none }
    #t2:checked ~ .soft { display:flex; gap:.6rem; flex-wrap:wrap }
  </style>
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
<br>
<div class="skills row">
  {% for s in site.data.skills.hard %}<span class="pill tilt mono">{{ s.name }}</span>{% endfor %}
</div>
<br>
<div class="skills">
  {% for s in site.data.skills.hard %}
    <div class="card" style="display:inline-block; margin:.4rem">
      <div class="row"><strong>{{ s.name }}</strong><span class="small">L{{ s.level }}</span></div>
      <div class="small" style="max-height:0; overflow:hidden; transition:.2s">
        {{ s.note | default: " " }}
      </div>
    </div>
  {% endfor %}
</div>
<script>
document.querySelectorAll('.card').forEach(c=>{
  c.addEventListener('mouseenter',()=>c.lastElementChild.style.maxHeight='4rem');
  c.addEventListener('mouseleave',()=>c.lastElementChild.style.maxHeight='0');
});
</script>
<br>
<table class="skills table">
  <tbody>
    {% for s in site.data.skills.hard %}
      <tr><td>{{ s.name }}</td><td>
        <div class="meter" style="--w: {{ s.level | times: 20 }}%"></div>
      </td></tr>
    {% endfor %}
  </tbody>
</table>
<br>
<div class="skills row">
  <div>
    <div class="small">Core</div>
    <div class="skills-grid" style="margin-top:.4rem">
      {% for s in site.data.skills.hard %}
        {% if s.level >= 4 %}<span class="chip">{{ s.name }}</span>{% endif %}
      {% endfor %}
    </div>
  </div>
  <div>
    <div class="small">Also</div>
    <div class="skills-grid" style="margin-top:.4rem">
      {% for s in site.data.skills.hard %}
        {% if s.level < 4 %}<span class="chip outline">{{ s.name }}</span>{% endif %}
      {% endfor %}
    </div>
  </div>
</div>
<br>
<div class="skills row" style="flex-wrap:nowrap; overflow:auto">
  {% for s in site.data.skills.hard %}<span class="chip">{{ s.name }}</span>{% endfor %}
</div>
<br>
<div class="skills skills-grid">
  {% for s in site.data.skills.soft %}
    <div class="card" style="padding:.6rem .8rem">
      <div class="row"><strong>{{ s.name }}</strong><span class="badge">L{{ s.level }}</span></div>
    </div>
  {% endfor %}
</div>
<br>
<div class="skills">
  {% for s in site.data.skills.hard %}
    <div class="mono" style="display:flex; justify-content:space-between; border-bottom:1px dashed #222; padding:.3rem 0">
      <span>{{ s.name }}</span><span>L{{ s.level }}/5</span>
    </div>
  {% endfor %}
</div>
<br>
<svg viewBox="0 0 100 100" width="220" height="220" class="skills" style="display:block">
  <!-- оси -->
  {% assign axes = site.data.skills.hard | slice: 0, 5 %}
  {% assign n = axes | size %}
  {% for s in axes %}
    {% assign i = forloop.index0 %}
    {% assign ang = 6.283185307 | times: i | divided_by: n %}
    {% assign x = 50 | plus: 40 | times: 0 %}<!-- placeholder -->
  {% endfor %}
  <!-- для простоты: отрисуем регулярный пятиугольник по уровню -->
  {% capture points %}{% endcapture %}
  {% assign R = 40 %}
  {% for s in axes %}
    {% assign i = forloop.index0 %}
    {% assign ang = 6.283185307 | times: i | divided_by: n %}
    {% assign r = R | times: s.level | divided_by: 5.0 %}
    {% assign x = 50 | plus: r | times: 0 %}{% endfor %}
  <!-- Упростим: декоративное кольцо -->
  <circle cx="50" cy="50" r="40" fill="none" stroke="#222"/>
  <text x="50" y="50" text-anchor="middle" dy=".35em" class="small">Top-5 hard</text>
</svg>
<br>
<div class="skills" style="font-size:.95rem">
  <div class="small">Hard</div>
  <div style="columns:2; column-gap:1.5rem; margin:.4rem 0 1rem">
    {% for s in site.data.skills.hard %}<div>• {{ s.name }} — L{{ s.level }}</div>{% endfor %}
  </div>
  <div class="small">Soft</div>
  <div style="columns:2; column-gap:1.5rem">
    {% for s in site.data.skills.soft %}<div>• {{ s.name }} — L{{ s.level }}</div>{% endfor %}
  </div>
</div>
<br>
