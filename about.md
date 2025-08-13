---
layout: default
title: About
permalink: /about/
---

<div class="container">
  <!-- Блок биографии -->
   <h2 class="subheading">Skills</h2>
  <section class="bio-section">
      <!-- Левая колонка: текст -->
      <div class="bio">
        <p>
          Curiosity about human behavior and cognitive science led me into UX/UI design, where I’ve worked for 14+ years. 
          My background in visual arts sharpened my sense of form, color, and composition. 
          I enjoy an academic vibe — sharing ideas, debating approaches, and learning from peers. 
          I work with flexible methods and visual tools to align business goals with user needs, 
          and have designed internal tools, mobile/desktop apps, and ecosystem products. 
          Always open to new collaborations — feel free to reach out.
        </p>
      </div>
      <!-- Правая колонка: пока пусто -->
      <div class="bio">
        <!-- Здесь позже появится фото -->
      </div>
  </section>

  <!-- Блок скилов -->
  <section class="skills-section">
    <h2 class="subheading">Skills</h2>
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

  <!-- Градиентный разделитель -->
  <div class="intro-divider"></div>
</div>

<!-- ===== Tooltip logic: один bubble на весь сайт, без зависимостей ===== -->
<script>
(function () {
  const SAFE_PAD = 12;               // отступ от краёв экрана
  const GAP = 8;                     // отступ от элемента
  const bubble = document.createElement('div');
  bubble.id = 'tooltip-bubble';
  document.body.appendChild(bubble);

  let currentEl = null;
  let hideTimer = null;

  function positionBubble(el) {
    if (!el) return;
    const text = el.getAttribute('data-tip');
    if (!text) return;

    // Подготовка к измерению
    bubble.textContent = text;
    bubble.style.display = 'block';
    bubble.classList.remove('show');
    bubble.style.left = '0px';
    bubble.style.top = '0px';

    // Замеры
    const br = bubble.getBoundingClientRect();
    const er = el.getBoundingClientRect();
    const vw = window.innerWidth;
    const vh = window.innerHeight;

    // Центрируем по X и ограничиваем в пределах экрана
    let x = er.left + (er.width / 2) - (br.width / 2);
    if (x < SAFE_PAD) x = SAFE_PAD;
    if (x + br.width > vw - SAFE_PAD) x = vw - SAFE_PAD - br.width;

    // Предпочтительно показываем над элементом, иначе — под элементом
    let y = er.top - GAP - br.height;
    if (y < SAFE_PAD) y = er.bottom + GAP;
    if (y + br.height > vh - SAFE_PAD) y = vh - SAFE_PAD - br.height;

    bubble.style.left = Math.round(x) + 'px';
    bubble.style.top  = Math.round(y) + 'px';

    // Плавное появление
    requestAnimationFrame(() => bubble.classList.add('show'));
  }

  function showTip(el) {
    currentEl = el;
    clearTimeout(hideTimer);
    positionBubble(el);
    window.addEventListener('scroll', onMove, { passive: true });
    window.addEventListener('resize', onMove);
    window.addEventListener('orientationchange', onMove);
  }

  function hideTip() {
    bubble.classList.remove('show');
    clearTimeout(hideTimer);
    hideTimer = setTimeout(() => {
      bubble.style.display = 'none';
      currentEl = null;
      window.removeEventListener('scroll', onMove);
      window.removeEventListener('resize', onMove);
      window.removeEventListener('orientationchange', onMove);
    }, 180); // длительность совпадает с transition
  }

  function onMove() {
    if (currentEl) positionBubble(currentEl);
  }

  // Делегирование событий
  document.addEventListener('mouseenter', (e) => {
    const el = e.target.closest('.tooltip');
    if (el) showTip(el);
  }, true);

  document.addEventListener('mouseleave', (e) => {
    const el = e.target.closest('.tooltip');
    if (el) hideTip();
  }, true);
})();
</script>
