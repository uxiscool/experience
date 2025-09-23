---
order: 2
title: Image compressor
title_ru: Image compressor
subtitle: JPEG compression and&nbsp;image scale normalization for&nbsp;Figma layouts.
subtitle_ru: JPEG-сжатие и нормализация масштаба изображений в макетах Figma.
desc: "This plugin optimizes images directly in&nbsp;Figma, eliminating exports or&nbsp;manual replacements. It&nbsp;compresses frame images to&nbsp;JPEG with&nbsp;adjustable compression, detects nested images, and&nbsp;normalizes their scale (e.g., when visually smaller but&nbsp;larger in&nbsp;data). Built to&nbsp;address unsuitable existing plugins, it&nbsp;reduces Figma mockup size for&nbsp;PDF export."
desc_ru: "Мой плагин оптимизирует изображения прямо в Figma, без экспорта и ручных замен. Он сжимает изображения во фреймах в JPEG с настраиваемым уровнем компрессии, находит вложенные картинки и нормализует их масштаб (например, когда они визуально меньше, но &laquo;весят&raquo; больше). Плагин создан как альтернатива неподходящим решениям и помогает уменьшить размер макета Figma перед экспортом в PDF."
icon: /assets/pix/pet/fgm_compress/icon.svg
kind: Plugin for Figma
kind_ru: Плагин Figma

# Базовый префикс для картинок галереи
images_base: /assets/pix/pet/fgm_compress/

# Стор/где посмотреть проект
store_url: https://www.figma.com/community/plugin/1509229645333597690/image-compressor-free
store_icon: /ui/stores/figma.svg
store_alt: "Figma"
store_alt_ru: "Figma"

# Галерея изображений (первая используется в левой колонке плитки)
gallery:
  - file: scr1.png
    caption: "The&nbsp;main screen of&nbsp;the&nbsp;plugin, the&nbsp;results of&nbsp;compression are&nbsp;visible -&nbsp;the&nbsp;gain in&nbsp;file size is&nbsp;highlighted."
    caption_ru: "Главный экран: видно, сколько места удалось сэкономить."
    thumb: true
  - file: scr2.png
    caption: "Various localization options available."
    caption_ru: "Видны варианты локализации."
  - file: scr3.png
    caption: "If&nbsp;there is&nbsp;no gain in&nbsp;image weight after&nbsp;the&nbsp;compression procedure, the&nbsp;process is&nbsp;not&nbsp;applied and&nbsp;a&nbsp;corresponding message is&nbsp;displayed."
    caption_ru: "Если сжатие не даёт выгоды, оно не применяется, а пользователю показывается сообщение."

---
