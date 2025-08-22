---
title: Image compressor
subtitle: Quick batch renaming for Figma
icon: /assets/pix/pet/fgm_compress/icon.svg
kind: Плагин для Figma
images_base: /assets/pix/pet/fgm_compress/
bg_colors: ["#2c3d64", "#0c2240", "#1b1f2e"]   # если есть bg_image — не нужно
# bg_image: /assets/pix/pet/fgm_compress/bg.jpg

# Показываем картинку внутри плитки? (берём первую из gallery, если thumb:true)
overlay: true

stores:
  appstore:
  play:
# для плагина можно добавить отдельный блок ссылок, если захочешь

gallery:
  - file: scr1.png
    caption: "Full description of the plugin and the main screen."
    thumb: true   # эту же картинку покажем маленьким превью в плитке
  - file: scr2.png
    caption: "Secondary flow."
  - file: scr3.png
    caption: "Another state."
---
