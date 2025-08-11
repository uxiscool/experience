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
