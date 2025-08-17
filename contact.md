---
layout: default
title: Contact
permalink: /contact/
---

<div class="container">
  <!-- Page-scoped styles: только для этой страницы -->
  <style>
    /* Липкий футер только здесь (и fallback-класс ниже) */
    body:has(#contact-page) { min-height: 100dvh; display: flex; flex-direction: column; }
    body:has(#contact-page) > main { flex: 1 0 auto; }
    body.page-contact-flex { min-height: 100dvh; display: flex; flex-direction: column; }
    body.page-contact-flex > main { flex: 1 0 auto; }

    /* Список контактов — базовая сетка */
    #contact-page .contacts-list {
      --contact-link-color:#e2e5e7;
      --stagger: 90ms;                /* шаг задержки по элементам */
      list-style:none; margin:0; padding:0;
      display:grid; gap:14px;
    }
    #contact-page .contact-item {
      display:grid; grid-template-columns:32px 1fr; align-items:center; column-gap:14px;

      /* Анимация появления — в духе hero на index (та же кривая) */
      opacity:0; transform:translateY(8px); filter:blur(4px);
      animation: ci-in .6s cubic-bezier(.19,1,.22,1) both; /* как heroFadeIn на index */
    }
    @keyframes ci-in { to { opacity:1; transform:none; filter:none; } }

    /* Стагер по позициям (у нас до 7 пунктов; запасом — до 12) */
    #contact-page .contact-item:nth-child(1)  { animation-delay: calc(var(--stagger) * 0); }
    #contact-page .contact-item:nth-child(2)  { animation-delay: calc(var(--stagger) * 1); }
    #contact-page .contact-item:nth-child(3)  { animation-delay: calc(var(--stagger) * 2); }
    #contact-page .contact-item:nth-child(4)  { animation-delay: calc(var(--stagger) * 3); }
    #contact-page .contact-item:nth-child(5)  { animation-delay: calc(var(--stagger) * 4); }
    #contact-page .contact-item:nth-child(6)  { animation-delay: calc(var(--stagger) * 5); }
    #contact-page .contact-item:nth-child(7)  { animation-delay: calc(var(--stagger) * 6); }
    #contact-page .contact-item:nth-child(8)  { animation-delay: calc(var(--stagger) * 7); }
    #contact-page .contact-item:nth-child(9)  { animation-delay: calc(var(--stagger) * 8); }
    #contact-page .contact-item:nth-child(10) { animation-delay: calc(var(--stagger) * 9); }
    #contact-page .contact-item:nth-child(11) { animation-delay: calc(var(--stagger) * 10); }
    #contact-page .contact-item:nth-child(12) { animation-delay: calc(var(--stagger) * 11); }

    /* Кликабельно вся строка (иконка+текст) */
    #contact-page .contact-block {
      display: contents;                   /* <a> охватывает обе колонки */
      color: var(--contact-link-color); text-decoration: none;
    }
    #contact-page .contact-block:where(:hover,:focus,:active,:visited) {
      color: var(--contact-link-color); text-decoration: none;
    }
    #contact-page .contact-item:has(.contact-block:focus-visible) {
      outline:2px solid #ff9900; outline-offset:2px; border-radius:8px;
    }

    /* Иконки */
    #contact-page .ci, #contact-page .ci img, #contact-page .ci svg {
      width:32px; height:32px; display:block;
    }
    #contact-page .ci { display:inline-flex; align-items:center; justify-content:center; }

    /* Текст — без переносов на широких, с переносами на узких */
    #contact-page .contact-line { display:flex; align-items:baseline; gap:8px; flex-wrap:nowrap; min-width:0; }
    #contact-page .contact-title, #contact-page .contact-hint { white-space:nowrap; }
    #contact-page .contact-hint { color:#b7c1cc; font-size:.95rem; opacity:.96; }
    @media (max-width:640px){
      #contact-page .contact-line { flex-wrap:wrap; }
      #contact-page .contact-title, #contact-page .contact-hint { white-space:normal; }
    }

    /* Coming soon */
    #contact-page .contact-item.soon { opacity:.55; }
    #contact-page .contact-item.soon .soon-tag { font-size:.95rem; color:#b7c1cc; }

    /* Уважение к prefers-reduced-motion */
    @media (prefers-reduced-motion: reduce){
      #contact-page .contact-item { animation:none !important; opacity:1; transform:none; filter:none; }
    }
  </style>

  <section id="contact-page" class="contacts-section">
    <!-- Заголовок убран по твоей просьбе -->

    <div class="bio">
      <ul class="contacts-list">
        <!-- 1) Email (обфускация адреса) -->
        <li class="contact-item">
          <a id="email-link" class="contact-block" href="#"
             data-user="loocsixu" data-host="moc.liamg" aria-label="Email">
            <span class="ci" aria-hidden="true">
              <img src="{{ site.baseurl }}/ui/apps_logo/contacts_gmail.svg" alt="">
            </span>
            <div class="contact-line">
              <span class="contact-title">Email</span>
              <span class="contact-hint" id="email-text">[show email]</span>
            </div>
          </a>
        </li>

        <!-- 2) Telegram -->
        <li class="contact-item">
          <a class="contact-block" href="https://t.me/evil-cactus" target="_blank" rel="noopener" aria-label="Telegram: @evil-cactus">
            <span class="ci" aria-hidden="true">
              <img src="{{ site.baseurl }}/ui/apps_logo/contacts_telegram.svg" alt="">
            </span>
            <div class="contact-line">
              <span class="contact-title">Telegram</span>
              <span class="contact-hint">@evil-cactus</span>
            </div>
          </a>
        </li>

        <!-- 3) HeadHunter -->
        <li class="contact-item">
          <a class="contact-block" href="https://hh.ru/resume" target="_blank" rel="noopener" aria-label="HeadHunter profile">
            <span class="ci" aria-hidden="true">
              <img src="{{ site.baseurl }}/ui/apps_logo/contacts_hh.svg" alt="">
            </span>
            <div class="contact-line">
              <span class="contact-title">HeadHunter profile</span>
              <span class="contact-hint">hh.ru/resume/<em>your_id</em></span>
            </div>
          </a>
        </li>

        <!-- 4) LinkedIn -->
    <li class="contact-item">
      <a class="contact-block" href="https://www.linkedin.com/in/" target="_blank" rel="noopener" aria-label="LinkedIn profile">
        <span class="ci" aria-hidden="true">
          <img src="{{ site.baseurl }}/ui/apps_logo/contacts_linkedin.svg" alt="">
        </span>
        <div class="contact-line">
          <span class="contact-title">LinkedIn profile</span>
          <span class="contact-hint">linkedin.com/in/<em>your_slug</em></span>
        </div>
      </a>
    </li>

        <!-- 5) Behance (coming soon) -->
        <li class="contact-item soon" aria-disabled="true">
          <span class="ci" aria-hidden="true">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
              <rect x="3"  y="4"  width="7" height="7" rx="1"/>
              <rect x="14" y="4"  width="7" height="7" rx="1"/>
              <rect x="3"  y="13" width="7" height="7" rx="1"/>
              <rect x="14" y="13" width="7" height="7" rx="1"/>
            </svg>
          </span>
          <div class="contact-line">
            <span class="contact-title">Behance</span>
            <span class="soon-tag">(coming soon)</span>
          </div>
        </li>

        <!-- 6) Dribbble (coming soon) -->
        <li class="contact-item soon" aria-disabled="true">
          <span class="ci" aria-hidden="true">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
              <circle cx="12" cy="12" r="9"/>
              <path d="M3 12h18"/>
              <path d="M12 3c3 2 5 5 6 9-1 4-3 7-6 9-3-2-5-5-6-9 1-4 3-7 6-9z"/>
            </svg>
          </span>
          <div class="contact-line">
            <span class="contact-title">Dribbble</span>
            <span class="soon-tag">(coming soon)</span>
          </div>
        </li>

        <!-- 7) Habr (coming soon) -->
        <li class="contact-item soon" aria-disabled="true">
          <span class="ci" aria-hidden="true">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
              <rect x="4" y="3" width="16" height="18" rx="2"/>
              <path d="M8 7h8M8 11h8M8 15h8"/>
            </svg>
          </span>
          <div class="contact-line">
            <span class="contact-title">Habr</span>
            <span class="soon-tag">(coming soon)</span>
          </div>
        </li>
      </ul>

      <!-- email обфускация -->
      <script>
        (function () {
          var a = document.getElementById('email-link');
          if (!a) return;
          function rev(s){ return s.split('').reverse().join(''); }
          var addr = rev(a.dataset.user) + '@' + rev(a.dataset.host);
          a.href = 'mailto:' + addr;
          var t = document.getElementById('email-text');
          if (t) t.textContent = addr;
        })();
      </script>
      <noscript><p class="contact-hint">Email: uxiscool [at] gmail [dot] com</p></noscript>

      <div class="intro-divider"></div>
    </div>
  </section>
</div>

<!-- Fallback: если браузер не понимает :has(), добавим класс на body -->
<script>
  if (!CSS.supports('selector(body:has(#contact-page))')) {
    document.body.classList.add('page-contact-flex');
  }
</script>
