---
date: 2020-02-22
title: "Flutter Navigation dan Routing"
template: post
thumbnail: "../thumbnails/routing.png"
slug: flutter-navigation-and-routing
categories:
  - Flutter
  - Programming
tags:
  - blog
  - flutter
  - navigation
  - routing
---

Kali ini kita akan belajar basic flutter mengenai navigasi dan routing. Yap ini sebenernya basic banget tapi ini paling sering kita pakai untuk pergi ke halaman atau balik lagi di layar yang kita pengenin, nah kali ini kita akan fokus bahas:

1. push
2. pushNamed
3. pop
4. popUntil

Kenapa 4 saja? kare ini ini paling basic banget yang bisa kita gunain untuk seluruh project di flutter. Langsung aja pertama kita bikin project flutter

```bash
  create flutter routing
```
selanjutnya di file **main.dart** hapus komentar dan element yang ga kita pake, jadinya kayak gini

```bash
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Routing',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Routing dan Navigasi'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'Siap untuk implementasi routing dan navigasi?',
            ),
          ],
        ),
      ),
    );
  }
}
```

selanjutnya biar mudah dan rapi kita bikin folder **routes** di folder **lib** dan bikin file namanya **routing_a.dart**

isinkan standar stateless seperti ini

```bash
import 'package:flutter/material.dart';

class RouteA extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text("Welcome to Route A"),
          ],
        ),
      ),
    );
  }
}
```

Setelah itu kita balik lagi ke **main.dart** dan bikin button untuk kita navigasiin ke **Route A**

```bash
FlatButton(
    onPressed: () {},
    child: Text('Bawa Ke Halaman A'),
)
```

Nah kita sekarang implementasi untuk routingnya, di taruh di onpress, di situ kita bisa menggunakan **push** maupun **pushNamed** bedanya kalo push kita harus mendefinisikan routenya, kalo pushNamed tinggal kita panggil nama yang udah di definisiin. oke langsung kita coba aja definisiin **routingA** ini ke **main.dart** pada **MaterialApp**

```bash
    return MaterialApp(
      title: 'Flutter Routing',
      routes: {
        'routeA':(context) => RouteA()
      },
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Routing dan Navigasi'),
    );
```

Implementasinya

```bash
RaisedButton(
    onPressed: () {
        Navigator.of(context).pushNamed('routeA');
    },
    child: Text('Bawa Ke Halaman A'),
)
```
Nah kalo push aja gimana caranya hampir sama, kita contohin seperti di atas, kita bikin dulu file baru dengan nama **routing_b.dart** dengan isi standar juga dan definisikan button di halaman **main.dart**


```bash
RaisedButton(
    onPressed: () {
        Navigator.push(
            context,
            MaterialPageRoute(
                builder: (context) => RouteB(),
            ),
        );
    },
    child: Text('Bawa Ke Halaman B'),
)
```

Nah selanjutnya kita masuk pada pembahasan **pop** dan **popUntil**, sederhananya pop adalah balik ke halaman sebelumnya

Ini sangat sederhana, kita masuk ke file **routing_a.dart** dan bikin standar flat button dan definisikan navigator pop seperti ini

```bash
RaisedButton(
    child: Text("Back to home"),
    onPressed: () {
        Navigator.pop(context);
    },
),
```

nah selanjutnya **popUntil** kapan digunakan, ketika kita ingin balik ke halaman semula atau halaman yang awal banget contoh kita dari route **a** ke **b**, kalo pake **pop** dari **b** pasti balik ke **a** tp kalo pake **popUntil** kita bisa balik ke halaman awal nah kita contohin aja, tp sebelum itu sekalian kita bikin button di **route a** biar ga bolak balik

```bash
RaisedButton(
    child: Text("route B from A"),
    onPressed: () {
        Navigator.push(
            context,
            MaterialPageRoute(builder: (context) => RouteB()),
        );
    },
)
```
cara pakainya kita bikin button di halaman **b** kayak gini

```bash
RaisedButton(
    child: Text("Go back all the way to home"),
    onPressed: () {
        Navigator.popUntil(context, ModalRoute.withName(Navigator.defaultRouteName));
    },
)
```

taraaa udah beres sangat mudah bukan, sourcodenya bisa dilihat di github saya yah, nah sebagai penutup kita definisin juga ketika ga nemuin routingnya caranya

```bash
return MaterialApp(
      title: 'Flutter Demo',
      onUnknownRoute: (RouteSettings setting) {
        return new MaterialPageRoute(
                    builder: (context) => NotFoundPage()
        );
      },
....
..
```

Kalo masih kurang jelas silahkan tonton video youtube saya ya [devindo](https://youtube.com/devindo)

Semoga bermanfaat
