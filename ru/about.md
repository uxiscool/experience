---
layout: default
title: Обо мне
permalink: /ru/about/
lang: ru
alt_url: /about/
---

<div class="container">
  <!-- Блок биографии -->
  <section class="bio-section">
   <h2 class="subheading">Биография</h2>
    <div class="bio-columns">
      <!-- Левая колонка: текст -->
      <div class="bio">
        <p>
Интерес к&nbsp;поведению людей и&nbsp;когнитивным наукам привёл меня в&nbsp;UX/UI-дизайн, где&nbsp;я&nbsp;работаю уже более 14&nbsp;лет. Практика в&nbsp;рисунке и&nbsp;живописи помогли развить чувство формы, цвета и&nbsp;композиции. Мне близка «академическая атмосфера» —&nbsp;обмен идеями, обсуждения подходов, совместное обучение.</p><p>Открыт к&nbsp;сотрудничеству —&nbsp;буду рад обсудить ваш&nbsp;проект.</p>
      </div>
      <!-- Правая колонка достижения -->
   <div class="bio">
  <div class="achievements-grid">
    <figure class="laurel-badge" data-value="14+" data-label="лет опыта" style="
          --size:160px;
          --leaf:#d6c083;
          --text:#d6c083;
          --leaf-delay:.5s;   /* пауза перед стартом «строительства» венка */
          --leaf-gap:160ms;   /* шаг между парами листьев */
          --lift:-20%;        /* вертикальный подъём SVG листвы */
        "></figure>
    <figure class="laurel-badge" data-value="25+" data-label="значимых&nbsp;проектов" style="
          --size:160px;
          --leaf:#d6c083;
          --text:#d6c083;
          --leaf-delay:.5s;   /* пауза перед стартом «строительства» венка */
          --leaf-gap:160ms;   /* шаг между парами листьев */
          --lift:-20%;        /* вертикальный подъём SVG листвы */
        "></figure>
  </div>
</div>
    </div>
  </section>
  <!-- Блок скилов -->
  <section class="skills-section">
    <h2 class="subheading">Навыки</h2>
    <div class="skills-columns">
      <!-- Soft column -->
      <div class="skills-col">
        <h3 class="skills-title">Софт</h3>
        <div class="skills skills-grid">
{% for s in site.data.skills.soft %}
  {% assign label = s.name %}
  {% assign tip = s.note %}
  {% if page.lang == 'ru' %}
    {% if s.name_ru %}{% assign label = s.name_ru %}{% endif %}
    {% if s.note_ru %}{% assign tip = s.note_ru %}{% endif %}
  {% endif %}
  <span
    class="pill tilt mono tooltip slide-in-left"
    data-tip="{{ tip | default: '—' }}"
    style="animation-delay: {{ forloop.index0 | times: 80 }}ms"
  >{{ label }}</span>
{% endfor %}
        </div>
      </div>
      <!-- Hard column -->
      <div class="skills-col">
        <h3 class="skills-title">Хард</h3>
        <div class="skills skills-grid">
{% for s in site.data.skills.hard %}
  {% assign label = s.name %}
  {% assign tip = s.note %}
  {% if page.lang == 'ru' %}
    {% if s.name_ru %}{% assign label = s.name_ru %}{% endif %}
    {% if s.note_ru %}{% assign tip = s.note_ru %}{% endif %}
  {% endif %}
  <span
    class="pill tilt mono tooltip slide-in-right"
    data-tip="{{ tip | default: '—' }}"
    style="animation-delay: {{ forloop.index0 | times: 80 }}ms"
  >{{ label }}</span>
{% endfor %}
        </div>
      </div>
    </div>
  </section>
    <!-- блок мой инструментарий -->
<section class="tools-section">
  <h2 class="subheading">Мои инструменты</h2>
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
  <h2 class="subheading">Философия</h2>
  <div class="bio-columns">
    <!-- Левая колонка: текст -->
    <div class="bio">
      <p>
      Я убеждён, что&nbsp;лучшие решения создаются при&nbsp;гармонии структуры и&nbsp;креативности. Часто восстанавливаю силы и&nbsp;вдохновляюсь наблюдая за природой —&nbsp;она&nbsp;учит терпению, внимательности к&nbsp;деталям и&nbsp;красоте простоты.
      </p>
    </div>
    <!-- Правая колонка: фото -->
    <div class="bio">
    <img src="{{ site.baseurl }}/ui/photo.jpg"
     alt="Portrait of Vladimir"
     class="bio-photo"
     width="600" height="327"
     loading="lazy" decoding="async">
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

  // Делегирование событий безопасно для текстовых узлов и старых браузеров
document.addEventListener('mouseenter', (e) => {
  let t = e.target;
  if (t && t.nodeType === 3) t = t.parentElement; // если текстовый узел -> к родителю
  const el = t && typeof t.closest === 'function'
    ? t.closest('.tooltip')
    : (t && t.parentElement && typeof t.parentElement.closest === 'function'
        ? t.parentElement.closest('.tooltip')
        : null);
  if (el) showTip(el);
}, true);

document.addEventListener('mouseleave', (e) => {
  let t = e.target;
  if (t && t.nodeType === 3) t = t.parentElement;
  const el = t && typeof t.closest === 'function'
    ? t.closest('.tooltip')
    : (t && t.parentElement && typeof t.parentElement.closest === 'function'
        ? t.parentElement.closest('.tooltip')
        : null);
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
<script>
(function () {
  const tpl = (num, label) => `
  <svg viewBox="0 0 200 200" aria-hidden="true" focusable="false">
    <g transform="translate(100,100)">
      <!-- Левая ветвь (пары i=0..5: снизу вверх) -->
      <g transform="translate(-10,0) rotate(-15)">
        ${leafPath( -60,  45, 26, 0)}
        ${leafPath( -78,  18, 22, 1)}
        ${leafPath( -84, -12, 20, 2)}
        ${leafPath( -78, -38, 18, 3)}
        ${leafPath( -60, -60, 16, 4)}
        ${leafPath( -35, -76, 14, 5)}
      </g>
      <!-- Правая ветвь (зеркало, те же индексы — пары синхронны) -->
      <g transform="translate(10,0) rotate(15) scale(-1,1)">
        ${leafPath( -60,  45, 26, 0)}
        ${leafPath( -78,  18, 22, 1)}
        ${leafPath( -84, -12, 20, 2)}
        ${leafPath( -78, -38, 18, 3)}
        ${leafPath( -60, -60, 16, 4)}
        ${leafPath( -35, -76, 14, 5)}
      </g>
    </g>
  </svg>
  <div class="lb-text" aria-hidden="true">
    <div class="lb-number">${num}</div>
    <div class="lb-label">${label}</div>
  </div>`;

  function leafPath(x, y, r, i){
    const rx = r, ry = r*0.55, k = 0.65*r;
    return `
      <path class="lb-leaf" style="--i:${i}"
        d="
          M ${x} ${y}
          c ${k} ${-ry}, ${rx} ${-ry}, ${rx*2} 0
          c ${-k} ${ry}, ${-rx} ${ry}, ${-rx*2} 0
          Z
        " fill="currentColor"/>
    `;
  }

  document.querySelectorAll('.laurel-badge').forEach(el => {
    const num = el.getAttribute('data-value')  || '';
    const label = el.getAttribute('data-label') || '';
    // кол-во пар (для вычисления финальной задержки текста)
    el.style.setProperty('--pairs', '6');
    el.innerHTML = tpl(num, label);
  });
})();
</script>
