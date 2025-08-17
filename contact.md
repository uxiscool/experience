---
layout: default
title: Contact
permalink: /contact/
---

<div class="container">
  <!-- Page-scoped styles. Работают только здесь. -->
  <style>
    /* 1) Липкий футер только на странице контактов (без глобальных правок) */
    body:has(#contact-page) { min-height: 100dvh; display: flex; flex-direction: column; }
    body:has(#contact-page) > main { flex: 1 0 auto; }
    /* Fallback для старых браузеров без :has() — добавим класс скриптом ниже */
    body.page-contact-flex { min-height: 100dvh; display: flex; flex-direction: column; }
    body.page-contact-flex > main { flex: 1 0 auto; }
    /* 2) Контент контактов — единая колонка; ссылка — на всю строку (иконка+текст) */
    #contact-page .contacts-list {
      --contact-link-color: #e2e5e7;
      list-style: none; margin: 0; padding: 0;
      display: grid; gap: 14px;
    }
    #contact-page .contact-item { display: grid; grid-template-columns: 32px 1fr; align-items: center; column-gap: 14px; }
    #contact-page .contact-block {
      display: contents; /* чтобы <a> охватывала и иконку, и текст, но без доп. обёртки */
      color: var(--contact-link-color); text-decoration: none;
    }
    #contact-page .contact-block:where(:hover,:focus,:active,:visited) { color: var(--contact-link-color); text-decoration: none; }
    /* Иконки */
    #contact-page .ci, #contact-page .ci img, #contact-page .ci svg { width: 32px; height: 32px; display: block; }
    #contact-page .ci { display: inline-flex; align-items: center; justify-content: center; }
    /* Текст строки: не переносим на широких экранах */
    #contact-page .contact-line { display: flex; align-items: baseline; gap: 8px; flex-wrap: nowrap; min-width: 0; }
    #contact-page .contact-title, #contact-page .contact-hint { white-space: nowrap; }
    #contact-page .contact-hint { color: #b7c1cc; font-size: .95rem; opacity: .96; }
    /* На узких — разрешаем перенос, чтобы не было горизонтального скролла */
    @media (max-width: 640px) {
      #contact-page .contact-line { flex-wrap: wrap; }
      #contact-page .contact-title, #contact-page .contact-hint { white-space: normal; }
    }
    /* Фокус по клавиатуре на всю строку */
    #contact-page .contact-item:has(.contact-block:focus-visible) { outline: 2px solid #ff9900; outline-offset: 2px; border-radius: 8px; }
    /* "Coming soon" — приглушаем */
    #contact-page .contact-item.soon { opacity: .55; }
    #contact-page .contact-item.soon .soon-tag { font-size: .95rem; color: #b7c1cc; }
  </style>
  <section id="contact-page" class="contacts-section">
    <h2 class="subheading">Contacts</h2>
    <div class="bio">
      <ul class="contacts-list" style="--contact-link-color:#e2e5e7">
        <!-- 1) Email -->
   <li class="contact-item">
  <a id="email-link"
     class="contact-block"
     href="#"
     data-user="loocsixu"
     data-host="moc.liamg"
     aria-label="Email">
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
      <script>
  (function () {
  var a = document.getElementById('email-link');
  if (!a) return;
  function rev(s){ return s.split('').reverse().join(''); }
  var addr = rev(a.dataset.user) + '@' + rev(a.dataset.host);

  // Покажем текст и сделаем кликабельным
  a.href = 'mailto:' + addr;
  var t = document.getElementById('email-text');
  if (t) t.textContent = addr;
})();
</script>
<noscript>
  <p class="contact-hint">Email: uxiscool [at] gmail [dot] com</p>
</noscript>
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
