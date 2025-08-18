---
layout: default
title: Contact
permalink: /contact/
body_class: page-contact
---

<div class="container">
  <section class="contacts-section">
    <div class="bio">
      <ul class="contacts-list" style="--contact-link-color:#e2e5e7">
        <!-- 1) Email (обфускация) -->
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
          <a class="contact-block" href="https://t.me/zloi-cactus" target="_blank" rel="noopener" aria-label="Telegram: @zloi-cactus">
            <span class="ci" aria-hidden="true">
              <img src="{{ site.baseurl }}/ui/apps_logo/contacts_telegram.svg" alt="">
            </span>
            <div class="contact-line">
              <span class="contact-title">Telegram</span>
              <span class="contact-hint">@zloi-cactus</span>
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
        <li class="contact-item disabled-text" aria-disabled="true">
          <span class="ci" aria-hidden="true">
            <img src="{{ site.baseurl }}/ui/apps_logo/contacts_behance.svg" alt="">
          </span>
          <div class="contact-line">
            <span class="contact-title">Behance</span>
            <span class="soon-tag">(coming somewhen)</span>
          </div>
        </li>

        <!-- 6) Dribbble (coming soon) -->
        <li class="contact-item disabled-text" aria-disabled="true">
          <span class="ci" aria-hidden="true">
            <img src="{{ site.baseurl }}/ui/apps_logo/contacts_dribbble.svg" alt="">
          </span>
          <div class="contact-line">
            <span class="contact-title">Dribbble</span>
            <span class="soon-tag">(coming somewhen)</span>
          </div>
        </li>

        <!-- 7) Habr (coming soon) -->
        <li class="contact-item disabled-text" aria-disabled="true">
          <span class="ci" aria-hidden="true">
            <img src="{{ site.baseurl }}/ui/apps_logo/contacts_habr.svg" alt="">
          </span>
          <div class="contact-line">
            <span class="contact-title">Habr</span>
            <span class="soon-tag">(coming somewhen)</span>
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
