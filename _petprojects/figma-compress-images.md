---
title: Image compressor
subtitle: JPEG compression and&nbsp;image scale normalization inside figma layout
desc: "I&nbsp;made this&nbsp;plugin myself, because the&nbsp;existing ones didn't suit&nbsp;me. The&nbsp;plugin can&nbsp;compress specific or&nbsp;all&nbsp;images of&nbsp;a&nbsp;frame into jpeg with&nbsp;a&nbsp;specified compression level, finds nested images, normalizes their scale (if&nbsp;they were scaled&nbsp;to&nbsp;a&nbsp;smaller visible size and&nbsp;in&nbsp;fact they&nbsp;are&nbsp;larger). Useful for&nbsp;reducing the&nbsp;weight of&nbsp;figma mockups and&nbsp;before exporting to&nbsp;pdf."
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
    caption: "The main screen of the plugin, the results of compression are visible - the gain in file size is highlighted."
    thumb: true
  - file: scr2.png
    caption: "Various localization options available."
  - file: scr3.png
    caption: "If there is no gain in image weight after the compression procedure, the process is not applied and a corresponding message is displayed."

---
