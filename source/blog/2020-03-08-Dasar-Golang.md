---
date: 2020-03-08
title: "Dasar Golang"
template: post
thumbnail: "../thumbnails/golang.jpg"
slug: dasar-golang
categories:
  - go
  - Programming
tags:
  - blog
  - blog
  - golang
  - basic
---

Bahasa go menjadi sangat populer di kalangan backend, selain mudahnya mempelejari go juga menjamin performa yang signifikan dibaging bahasa lainnya.

nah untuk pertmakali kita harus menginstall go dan bisa di lihat pada dokumen resminya yaitu golang.org

untuk membuat project pertama kali kita harus mendefinisikan package yang akan kita gunakan yaitu

```bash
package main

import (
	"fmt"
)
```

untuk menjalan kannya kalian bia menggunakan perintah **go run namafile.go**

untuk pertama kita belajar tipe data yaitu variable, hampir sama dengan bahasa pemrograman lain variable dapat di definisikan sebagai var

```bash

var pelajaran = "DART"
func main(){
	fmt.Println("Hallo devindo..."+ pelajaran + " " + pelajaran2);
}

```

yap untuk menjalankannya kita butuh fungsi main di setiap runnernya. nah enaknya lagi kita bisa mendefinisikan variable ini di dalam satu line contoh

```bash
var namadepan, namabelakang = "fiaz","luthfi"
```

nah di go juga kita bisa menganti var dengan **:=** tapi ini hanya bisa kita gunakan di dalam fungsi contoh

```bash
func main(){
    kampus := "Binus"
	fmt.Println("Hallo devindo..."+ kampus);
}
```
selain variable string seperti di atas ada juga numerik yaitu int atau integer, ada juga float yang bisanya di deteksi langsung ketika penulisannya menggunakan koma koma

```bash
func main(){
    kampus := "Binus"
    tanggal := 8
    berat := 55.5
	fmt.Println("Hallo devindo..."+ kampus);
	fmt.Println("Tanggal ", tanggal);
}
```

Kalo ngeformat integer ke string dan sebaliknya gimana?

```bash
import (
	"strconv"
)

func main(){
    tanggal := 8
    total := "10"
	fmt.Println("Tanggal " + strconv.itoa(tanggal));
	fmt.Println("Tanggal ",  strconv.itoa(total));
}
```

Kita mainan lebih dalam di fungsi ini, untuk pertama mengenai return

contoh

```bash
func printNumber() int{
    return 10
}

func main(){
    fmt.Println("Fungsi ini balikannya", printNumber())
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
