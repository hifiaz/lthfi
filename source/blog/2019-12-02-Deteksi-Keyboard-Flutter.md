---
date: 2019-12-02
title: 'Deteksi Keyboard Flutter'
template: post
thumbnail: '../thumbnails/keyboard.png'
slug: deteksi-keyboard-flutter
categories:
  - Flutter
  - Popular
  - Programming
tags:
  - blog
  - keyboard
  - visibility
---

Suatu saat aplikasi grab saya ter-logout otomatis, entah kenapa mungkin memang ada pembaruan di sistemnya, dan pas mau login lagi loh kok ini unik ya, keyboard muncul button bawah hilang dan ada button baru, bisa ga sih di implementasi di flutter?

jadi idenya cuma deteksi keyboard ini mah harusnya gampang. nah untuk deteksi keyboard gimana caranya?

ya betul kita manfaatin media query, media query bisa ngedeteksi lebar atau luas layar kita. biasanya kalo kita mainan responsivenya cuma deteksi size witdth atau height. nah kita deteksi kalo ada inset di bottomnya 

```bash
  MediaQuery.of(context).viewInsets.bottom
```
nah dari sini kita dapaet nih apakah di bottom layar ada tambahan, dimana kalo enggak kan defaultnya di 0.

Udah deh beres idenya, ini udah bisa kita implement untuk deteksi open atau close.

kita contohin untuk kasus yang grab tadi caranya, kita bikin fungsi boolean untuk deteksi apakah di default 0 atau enggak

```bash
  bool _keyboardIsVisible() {
    return !(MediaQuery.of(context).viewInsets.bottom == 0.0);
  }
```

Implementasi di codenya gimana? ya tinggal manfaatin if if gitu, lebih lengkapnya bisa tonton video saya di youtube [devindo](https://youtube.com/devindo) ya, dan sourcodenya ada di bawah video

Semoga bermanfaat

