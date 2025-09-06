---
order: 2
title: Image compressor
subtitle: JPEG compression and&nbsp;image scale normalization for&nbsp;Figma layouts.
desc: "This plugin optimizes images directly in&nbsp;Figma, eliminating exports or&nbsp;manual replacements. It&nbsp;compresses frame images to&nbsp;JPEG with&nbsp;adjustable compression, detects nested images, and&nbsp;normalizes their scale (e.g., when visually smaller but&nbsp;larger in&nbsp;data). Built to&nbsp;address unsuitable existing plugins, it&nbsp;reduces Figma mockup size for&nbsp;PDF export."
icon: /assets/pix/pet/fgm_compress/icon.svg
kind: Plugin for Figma

# Базовый префикс для картинок галереи
images_base: /assets/pix/pet/fgm_compress/

# Стор/где посмотреть проект
store_url: https://www.figma.com/community/plugin/1509229645333597690/image-compressor-free
store_icon: /ui/stores/figma.svg
store_alt: "Figma"

# Галерея изображений (первая используется в левой колонке плитки)
gallery:
  - file: scr1.png
    caption: "The&nbsp;main screen of&nbsp;the&nbsp;plugin, the&nbsp;results of&nbsp;compression are&nbsp;visible -&nbsp;the&nbsp;gain in&nbsp;file size is&nbsp;highlighted."
    thumb: true
  - file: scr2.png
    caption: "Various localization options available."
  - file: scr3.png
    caption: "If&nbsp;there is&nbsp;no gain in&nbsp;image weight after&nbsp;the&nbsp;compression procedure, the&nbsp;process is&nbsp;not&nbsp;applied and&nbsp;a&nbsp;corresponding message is&nbsp;displayed."

---
