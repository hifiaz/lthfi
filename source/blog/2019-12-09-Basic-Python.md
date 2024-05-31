---
date: 2019-12-09
title: "Basic Python"
template: post
thumbnail: "../thumbnails/phyton.png"
slug: basic-python
categories:
  - Python
  - Programming
tags:
  - blog
  - basic
---

Sesekali dapat project machine learning dengan python, karena nilainya sangat tinggi, iyain aja padahal sebelumnya belum pernah belajar sekalipun, nah sekalian belajar di dokumentasiin aja

Variable dan type, enaknya di python tidak harus di definisiin satu satu jadi kompailernya udah bisa ngenalin sendiri setiap typenya

```bash
  nama = "fiaz"
  tingkat = 2
  berat = 55,2
  print(nama)
  print(tingkat)
  print(berat)
```

Selanjutnya list, ini hampir sama kayak pemrograman lain tinggal di kasih kurung bracket udah di identifikasi sebai list

```bash
    nomor = []
    string = ['erik','wisnu','nadiem']
    nomor.append(1)
```

nah di atas adalah contoh untuk validasi ketika si value kurang dari 2 maka muncul notif validasi 'Lebih panjang lagi dong'

ini berlaku juga untuk validasi lainnya, kayak validasi untuk nomor atau email bisa juga tinggal pakai

Validasi Email

```bash
  validator: (val) {
    Pattern pattern =
                      r'^(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$';
    RegExp regex = new RegExp(pattern);
    return (!regex.hasMatch(val))
        ? 'Masukin email yg bener'
        : null;
    },
```

Validasi Nomor

```bash
  validator: (value) {
    Pattern patttern = r'(^(?:[+0]6)?[0-9]{10,12}$)';
    RegExp regExp = new RegExp(patttern);
    return (!regExp.hasMatch(value))
        ? 'Nomor aja jangan yg lain'
        : null;
    },
```

Nah kalo kita mau lanjut ke next step, validasi untuk buttonnya contohnya

```bash
   FlatButton(
        child: Text('Lanjut'),
            onPressed: () {
            if (_formKey.currentState.validate()) {
                // Lakukan sesuatu
            }
    })
```

Kalo masih kurang jelas silahkan tonton video youtube saya ya [devindo](https://youtube.com/devindo)

Semoga bermanfaat
