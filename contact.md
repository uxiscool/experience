---
layout: default
title: Contact
permalink: /contact/
---

<div class="container">
  <!-- page-scoped styles: only affect this page -->
  <style>
    /* Блок страницы контактов — только здесь */
    #contact-page { 
      /* База, чтобы не было промаха до расчёта JS */
      min-height: 60vh; 
    }

    /* Список и общий цвет ссылок (можно менять одной переменной) */
    #contact-page .contacts-list {
      --contact-link-color: #e2e5e7;
      list-style: none;
      margin: 0;
      padding: 0;
      display: grid;
      gap: 14px;
    }

    /* Вся строка — кликабельная: и иконка, и текст */
    #contact-page .contact-block {
      display: grid;
      grid-template-columns: 32px 1fr;
      align-items: center;
      column-gap: 14px;
      color: var(--contact-link-color);
      text-decoration: none;
      border-radius: 8px; /* для фокуса */
      padding: 2px 0;     /* чтобы фокус-обводка не резала контент */
    }
    #contact-page .contact-block:visited,
    #contact-page .contact-block:hover,
    #contact-page .contact-block:active,
    #contact-page .contact-block:focus {
      color: var(--contact-link-color);
      text-decoration: none;
    }
    #contact-page .contact-block:focus-visible {
      outline: 2px solid #ff9900;
      outline-offset: 2px;
    }

    /* Иконки */
    #contact-page .ci,
    #contact-page .ci img,
    #contact-page .ci svg { width: 32px; height: 32px; display: block; }
    #contact-page .ci { display: inline-flex; align-items: center; justify-content: center; }

    /* Текстовая часть строки */
    #contact-page .contact-line { display: flex; flex-wrap: wrap; gap: 8px; align-items: baseline; }
    #contact-page .contact-title { font-weight: 500; }
    #contact-page .contact-hint { color: #b7c1cc; font-size: 0.95rem; opacity: .96; }

    /* "Coming soon" — приглушаем */
    #contact-page .contact-item.soon { opacity: .55; }
    #contact-page .contact-item.soon .soon-tag { font-size: .95rem; color: #b7c1cc; }

    /* Мобильные мелочи */
    @media (max-width: 700px) { #contact-page .contact-line { gap: 6px; } }
  </style>

  <section id="contact-page" class="contacts-section">
    <h2 class="subheading">Contacts</h2>

    <!-- Наследуем типографику как у .bio -->
    <div class="bio">
      <!-- Поменять цвет всех ссылок можно тут (e.g. #d6c083 / #ff9900) -->
      <ul class="contacts-list" style="--contact-link-color:#e2e5e7">

        <!-- 1) Email -->
        <li class="contact-item">
          <a class="contact-block" href="mailto:uxiscool@gmail.com" aria-label="Email: uxiscool@gmail.com">
            <span class="ci" aria-hidden="true">
              <img src="{{ site.baseurl }}/ui/apps_logo/contacts_gmail.svg" alt="">
            </span>
            <div class="contact-line">
              <span class="contact-title">Email</span>
              <span class="contact-hint">uxiscool@gmail.com</span>
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

      <div class="intro-divider"></div>
    </div>
  </section>
</div>

<!-- Only this page: JS подгоняет высоту секции так, чтобы футер прижимался к низу -->
<script>
  (function() {
    function fitContactPage() {
      var header = document.querySelector('header');
      var footer = document.querySelector('.site-footer');
      var section = document.getElementById('contact-page');
      if (!section) return;

      var vh = (window.visualViewport && window.visualViewport.height) || window.innerHeight;
      var headerH = header ? header.getBoundingClientRect().height : 0;
      var footerH = footer ? footer.getBoundingClientRect().height : 0;

      // Минимальная высота секции так, чтобы низ main совпал с низом окна
      var target = Math.max(0, vh - headerH - footerH);
      section.style.minHeight = target + 'px';
    }

    window.addEventListener('DOMContentLoaded', fitContactPage);
    window.addEventListener('resize', fitContactPage);
    window.addEventListener('orientationchange', fitContactPage);
  })();
</script>
