---
layout: default
title: Contact
permalink: /contact/
---

<div class="container">
  <section class="contacts-section">
    <h2 class="subheading">Контакты</h2>
    <div class="bio">
      <!-- Цвет всех ссылок правится одной переменной -->
      <ul class="contacts-list" style="--contact-link-color:#e2e5e7">
        <!-- 1) Email -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <img src="{{ site.baseurl }}/ui/apps_logo/contacts_gmail.svg" alt="Gmail" width="32" height="32">
          </span>
          <div class="contact-line">
            <a class="contact-link" href="mailto:uxiscool@gmail.com">Email</a>
            <span class="contact-hint">uxiscool@gmail.com</span>
          </div>
        </li>
        <!-- 2) Telegram -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <img src="{{ site.baseurl }}/ui/apps_logo/contacts_telegram.svg" alt="Telegram" width="32" height="32">
          </span>
          <div class="contact-line">
            <a class="contact-link" href="https://t.me/evil-cactus" target="_blank" rel="noopener">Написать в Telegram</a>
            <span class="contact-hint">@evil-cactus</span>
          </div>
        </li>
        <!-- 3) HeadHunter -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <img src="{{ site.baseurl }}/ui/apps_logo/contacts_hh.svg" alt="HeadHunter" width="32" height="32">
          </span>
          <div class="contact-line">
            <a class="contact-link" href="https://hh.ru/resume" target="_blank" rel="noopener">Профиль на HeadHunter</a>
            <span class="contact-hint">hh.ru/resume/<em>твой_id</em></span>
          </div>
        </li>
        <!-- 4) LinkedIn -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <img src="{{ site.baseurl }}/ui/apps_logo/contacts_linkedin.svg" alt="LinkedIn" width="32" height="32">
          </span>
          <div class="contact-line">
            <a class="contact-link" href="https://www.linkedin.com/in/" target="_blank" rel="noopener">Мой профиль LinkedIn</a>
            <span class="contact-hint">linkedin.com/in/<em>твой_slug</em></span>
          </div>
        </li>
        <!-- 5) Behance (coming soon) -->
        <li class="contact-item soon">
          <span class="ci" aria-hidden="true">
            <!-- простая одноцветная «сетка-портфолио» -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3"  y="4"  width="7" height="7" rx="1"/>
              <rect x="14" y="4"  width="7" height="7" rx="1"/>
              <rect x="3"  y="13" width="7" height="7" rx="1"/>
              <rect x="14" y="13" width="7" height="7" rx="1"/>
            </svg>
          </span>
          <div class="contact-line">
            <span>Мой профиль на Behance</span>
            <span class="soon-tag">(coming soon)</span>
          </div>
        </li>
        <!-- 6) Dribbble (coming soon) -->
        <li class="contact-item soon">
          <span class="ci" aria-hidden="true">
            <!-- одноцветный «мяч» -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <circle cx="12" cy="12" r="9"/>
              <path d="M3 12h18"/>
              <path d="M12 3c3 2 5 5 6 9-1 4-3 7-6 9-3-2-5-5-6-9 1-4 3-7 6-9z"/>
            </svg>
          </span>
          <div class="contact-line">
            <span>Мой профиль на Dribbble</span>
            <span class="soon-tag">(coming soon)</span>
          </div>
        </li>
        <!-- 7) Хабр (coming soon) -->
        <li class="contact-item soon">
          <span class="ci" aria-hidden="true">
            <!-- одноцветный «лист статьи» -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <rect x="4" y="3" width="16" height="18" rx="2"/>
              <path d="M8 7h8M8 11h8M8 15h8"/>
            </svg>
          </span>
          <div class="contact-line">
            <span>Профиль на Хабре</span>
            <span class="soon-tag">(coming soon)</span>
          </div>
        </li>
      </ul>
      <div class="intro-divider"></div>
    </div>
  </section>
</div>
