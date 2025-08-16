---
layout: default
title: About
permalink: /about/
---

<div class="container">
  <!-- Блок биографии -->
  <section class="bio-section">
   <h2 class="subheading">Bio</h2>
    <div class="bio-columns">
      <!-- Левая колонка: текст -->
      <div class="bio">
        <p>
          Curiosity about human behavior and&nbsp;cognitive science led&nbsp;me&nbsp;intoUX/UI design, where I’ve&nbsp;worked for&nbsp;14+&nbsp;years. 
          My&nbsp;background in&nbsp;visual arts sharpened my&nbsp;sense of&nbsp;form, color, and&nbsp;composition. 
          I&nbsp;enjoy an&nbsp;academic vibe&nbsp;— sharing ideas, debating approaches, and&nbsp;learning from&nbsp;peers.</p>
          <p>I&nbsp;work with&nbsp;flexible methods and&nbsp;visual tools to&nbsp;align business goals with user needs, 
          and&nbsp;have designed internal tools, mobile/desktop apps, and&nbsp;ecosystem products.
        </p>
      </div>
      <!-- Правая колонка: пока пусто -->
      <div class="bio">
        15+ YoE, 100+ relised projects
      </div>
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
    <!-- блок мой инструментарий -->
<section class="tools-section">
  <h2 class="subheading">Apps & Tools</h2>
  <div class="tools-grid" style="--tools-delay-base: 800ms">
    {% for app in site.data.apps %}
      <a class="tool appear"
         href="{{ app.url }}" target="_blank" rel="noopener"
         aria-label="{{ app.name }}"
         style="--i: {{ forloop.index0 }}">
        <span class="tool-logo-wrap">
          <img
            src="{{ app.logo | relative_url }}"
            alt="{{ app.name }} logo"
            class="tool-logo"
            loading="lazy"
            decoding="async"
            fetchpriority="low">
        </span>
        <span class="tool-name sr-only">{{ app.name }}</span>
      </a>
    {% endfor %}
  </div>
   <div class="intro-divider"></div>
</section>
  <!-- Блок philosophy -->
<section class="philosophy-section">
  <h2 class="subheading">Philosophy</h2>
  <div class="bio-columns">
    <!-- Левая колонка: текст -->
    <div class="bio">
      <p>
        I&nbsp;believe that the&nbsp;best solutions grow from a&nbsp;balance of&nbsp;structure and&nbsp;creativity. I&nbsp;often recharge through hiking and&nbsp;observing nature — it&nbsp;teaches patience, attention to&nbsp;detail, and&nbsp;the&nbsp;beauty of&nbsp;simplicity. Always open to&nbsp;new collaborations&nbsp;— feel free to&nbsp;reach out.
      </p>
    </div>
    <!-- Правая колонка: фото -->
    <div class="bio">
    <img src="{{ site.baseurl }}/ui/photo_tmp.jpg"
     alt="Portrait of Vladimir"
     class="bio-photo"
     width="957" height="521">
    </div>
  </div>
</section>
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
<script>
document.addEventListener("DOMContentLoaded", () => {
  const tools = document.querySelectorAll(".tool.appear");

  if ("IntersectionObserver" in window) {
    const observer = new IntersectionObserver((entries, obs) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add("in-view");
          obs.unobserve(entry.target);
        }
      });
    }, { threshold: 0.1 }); // 10% видимости для срабатывания

    tools.forEach(el => observer.observe(el));
  } else {
    // Фолбэк — без анимации, если IntersectionObserver не поддерживается
    tools.forEach(el => el.classList.add("in-view"));
  }
});
</script>

