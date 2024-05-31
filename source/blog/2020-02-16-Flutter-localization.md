---
date: 2020-02-16
title: "Flutter Localization dengan Flappy Translator"
template: post
thumbnail: "../thumbnails/translate.png"
slug: flutter-localization-flappy-translator
categories:
  - Flutter
  - Programming
tags:
  - blog
  - flutter
  - translate
---

Ketika kita bikin aplikasi pasti utamanya adalah di pakai untuk kalangan sendiri, tp kan pengen juga aplikasi ini di pahami orang luar, terutama yang mau kita targetin seperti orang yang hariannya pake bahasa inggris atau china atau bahkan bahasa spanyol

Nah untuk mengatasi itu kita bisa pakai localization di flutter. Tapi ada ribetnya ketika kita harus menterjemahkannya satu persatu. Nah ini kita bisa mengatasinya dengan plugin flappy translator.

Yuk lah langsung kita bahasa aja untuk pertama. Kita bisa menyediakan dulu file yang akan kita translate, kita bisa mengunakan google sheet untuk mempermudahnya untuk di convert menjadi csv

| keys | fr | en | es | de_CH |
| ---- | -- | -- | -- | ----- |
| appTitle | Ma super application | My awesome application | Mi gran application | Meine tolle App |
| subtitle | Un sous titre | A subtitle | Un subtitulò | Ein Untertitel |
| description | Un texte avec une variable : %1$s | Text with a variable: %1$s | Un texto con una variable : %1$s | Text mit einer Variable: %1$s |
| littleTest | "Voici, pour l'exemple, ""un test"" avec la variable %age$d" | "Here is, for the example, ""a test"" with the variable %age$d" | "Aqui esta, por ejemplo, ""una prueba"" con la variable %age$d" | "Hier ist, zum Beispiel, ""ein Test"" mit der Variable %age$d" |

nah contoh di atas bisa kita permudah dengan bantuan google translate di google sheet dengan cara

```bash
  =GOOGLETRANSLATE(<Posisi Kolom>;"en";"fr")
```

kalo udah tinggal di download sebagai csv.

Selanjutnya kita setup untuk depedency di flutternya.

Jadi di sini saya anggap semua udah bisa install flutter jadi tinggal tambahin depedency


```bash
    dependencies:
        flutter_localizations:
        sdk: flutter
        flappy_translator: 
```

untuk versi flappy bisa di cek [disini](https://pub.dev/packages/flappy_translator#-readme-tab-)

kalo udah di setup depedency nya lakukan

```bash
    flutter pub get
    flutter pub run flappy_translator <nama_file.csv>
```

otomatis nanti akan di generate menjadi i18.dart

Selanjutnya tinggal kita implement pada main.dart kita

```bash
  class MyApp extends StatelessWidget {
    @override
        Widget build(BuildContext context) {
            return MaterialApp(
            localizationsDelegates: [
                const I18nDelegate(),
                GlobalMaterialLocalizations.delegate,
                GlobalWidgetsLocalizations.delegate,
            ],
            supportedLocales: I18nDelegate.supportedLocals,
            home: Home(),
            );
        }
    }
```

Udah beres tinggal cara pemakainnya, gampang sih, pada text tinggal kita panggil sesuai keynya contoh

```bash
   Text(I18n.of(context).appTitle),
```

taraaa udah beres sangat mudah bukan

Kalo masih kurang jelas silahkan tonton video youtube saya ya [devindo](https://youtube.com/devindo)

Semoga bermanfaat
