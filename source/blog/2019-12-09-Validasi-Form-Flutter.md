---
date: 2019-12-09
title: "Validasi Form Flutter"
template: post
thumbnail: "../thumbnails/valid.png"
slug: validasi-form-flutter
categories:
  - Flutter
  - Programming
tags:
  - blog
  - flutter
  - form
  - validasi
---

Validasi form sebelum lanjut ke tahap berikutnya sangat penting buat aplikasi kita, apalagi kalo ada requirement harus di isi, nah ini wajib banget kita implement di setiap form, untuk itu kita harus menginisiasi Global key untuk form state di dalam statefull widget kita

```bash
  GlobalKey<FormState> _formKey = GlobalKey<FormState>();
```

nah kalo udah di inisiasi tinggal kita warp si textform kita dengan form dan key nya set dengan global key yg di atur di atas contoh

```bash
    Form(
        key: _formKey,
        child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              TextFormField(
                validator: (value) {
                  if (value.length < 2) {
                    return 'Lebih panjang lagi dong';
                  }
                },
              )
            ],
        ),
    ),
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
