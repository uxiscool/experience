---
layout: default
title: Contact
permalink: /contact/
---

<div class="container">
  <section class="contacts-section">
    <!-- Наследуем типографику как у bio -->
    <div class="bio">
      <!-- Поменять цвет всех ссылок можно тут:
           варианты: #e2e5e7 (нейтрально), #d6c083 (в тон венкам), #ff9900 (акцентно) -->
      <ul class="contacts-list" style="--contact-link-color:#e2e5e7">
        <!-- LinkedIn -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <!-- link-иконка -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <path d="M10.5 13.5l3-3"/>
              <path d="M7.8 16.2a4.8 4.8 0 010-6.8l.2-.2a4.8 4.8 0 016.8 0"/>
              <path d="M16.2 7.8a4.8 4.8 0 010 6.8l-.2.2a4.8 4.8 0 01-6.8 0"/>
            </svg>
          </span>
          <div class="contact-line">
            <a class="contact-link" href="https://www.linkedin.com/in/" target="_blank" rel="noopener">Мой профиль LinkedIn</a>
            <span class="contact-hint">— добавь свой slug после <code>/in/</code></span>
          </div>
        </li>
        <!-- Telegram -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <!-- самолётик -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <path d="M21 3L3 10.5l6.6 2.4M21 3l-7.5 19-3.9-9.1M9.6 12.9l5.7-5.7"/>
            </svg>
          </span>
          <div class="contact-line">
            <a class="contact-link" href="https://t.me/evil-cactus" target="_blank" rel="noopener">Написать в Telegram</a>
            <span class="contact-hint">@evil-cactus</span>
          </div>
        </li>
        <!-- Email -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <!-- конверт -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3" y="5" width="18" height="14" rx="2" ry="2"/>
              <path d="M3 7l9 6 9-6"/>
            </svg>
          </span>
          <div class="contact-line">
            <a class="contact-link" href="mailto:uxiscool@gmail.com">Email</a>
            <span class="contact-hint">uxiscool@gmail.com</span>
          </div>
        </li>
        <!-- GitHub -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <!-- { } как нейтральная «код»-иконка -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <path d="M9 6c-3 0-3 2-3 6s0 6 3 6M15 6c3 0 3 2 3 6s0 6-3 6"/>
              <path d="M13 4l-2 16"/>
            </svg>
          </span>
          <div class="contact-line">
            <a class="contact-link" href="https://github.com/uxiscool" target="_blank" rel="noopener">GitHub</a>
            <span class="contact-hint">github.com/uxiscool</span>
          </div>
        </li>
        <!-- Behance -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <!-- портфолио-сетка -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3"  y="4"  width="7" height="7" rx="1"/>
              <rect x="14" y="4"  width="7" height="7" rx="1"/>
              <rect x="3"  y="13" width="7" height="7" rx="1"/>
              <rect x="14" y="13" width="7" height="7" rx="1"/>
            </svg>
          </span>
          <div class="contact-line">
            <a class="contact-link" href="https://www.behance.net/" target="_blank" rel="noopener">Мой профиль на Behance</a>
            <span class="contact-hint">behance.net/<em>твой_ник</em></span>
          </div>
        </li>
        <!-- Dribbble -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <!-- баскетбольный мяч -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <circle cx="12" cy="12" r="9"/>
              <path d="M3 12h18"/>
              <path d="M12 3c3 2 5 5 6 9-1 4-3 7-6 9-3-2-5-5-6-9 1-4 3-7 6-9z"/>
            </svg>
          </span>
          <div class="contact-line">
            <a class="contact-link" href="https://dribbble.com/" target="_blank" rel="noopener">Мой профиль на Dribbble</a>
            <span class="contact-hint">dribbble.com/<em>твой_ник</em></span>
          </div>
        </li>
        <!-- Хабр -->
        <li class="contact-item">
          <span class="ci" aria-hidden="true">
            <!-- документ/статья -->
            <svg viewBox="0 0 24 24" width="32" height="32" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <rect x="4" y="3" width="16" height="18" rx="2"/>
              <path d="M8 7h8M8 11h8M8 15h8"/>
            </svg>
          </span>
          <div class="contact-line">
            <a class="contact-link" href="https://habr.com/ru/users/" target="_blank" rel="noopener">Профиль на Хабре</a>
            <span class="contact-hint">habr.com/ru/users/<em>твой_ник</em></span>
          </div>
        </li>
      </ul>
      <div class="intro-divider"></div>
    </div>
  </section>
</div>
