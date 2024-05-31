---
date: 2019-03-23
title: 'Deploy page atau static web di gitlab dan cara seting domain sendiri'
template: post
thumbnail: '../thumbnails/gitlab.png'
slug: deploy-page-atau-static-web-di-gitlab-dan-cara-seting-domain-sendiri
categories:
  - Git
  - Popular
  - Programming
tags:
  - blog
  - gatsby
  - website
  - pages
---

Ketika budget client kecil dan satu sisi kita pengen ngehemat, dengan maksud karena biasanya kalo client budget kecilkan kalo ga ribet banyak maunya ya pokoknya jadi

Nah sebenernya saya punya hosting yang ya lumayan gede untuk ngedeploy web-web static, tapi kan kalo banyak pasti ribet juga apalagi kalo mainan pake node, udah siap siap bengkak aja tuh hosting

nah kali ini saya mau nulis cara deploy page website pake gatsby, kalian bisa aja pake hugo, vuepress atau yang lain gitu.

Nah mungkin saya asumsikan kalian udah bikin web di gatsby yah, atau kalo belum kalian bisa clone themplate yang di sediain, dengan itu kalian bisa mengikutin tutorial ini

```bash
npm install -g gatsby-cli
gatsby new gatsby-site
cd gatsby-site
gatsby develop
```
Dengan mengikuti shell di atas saya rasa kalian langsung bisa yah, dan gampang itu tinggal pake atau edit edit, untuk selengkapnya kalian bisa baca tutorial membuat website dengan gatsby [disini](https://www.gatsbyjs.org/docs/)

Nah berarti udah punya kodingan yang siap kita deploy di gitlab pages, dan untuk kali ini juga saya menganggap kalian udah punya akun di [gitlab](http://gitlab.com) dan bisa ngepush kodingan disana

Nah kalo udah ini sebernya gampang banget untuk ngedeploynya pertama atur dulu untuk path directorynya, jadi kalo kalian buka link gitlab kalian tepat di projectnya akan jadi contoh kayak gini `https://gitlab.com/hifiaz/infohondamalang`

nah di sini yang saya maksud path adalah `infohondamalang` path ini kita atur di dalam file namanya `gatsby-config.js` langsung aja tambahin modulnya

```bash
module.exports = {
  pathPrefix: `/infohondamalang`,
}
```

nah selanjutnya kita bikin gitlab ci, atau sederhananya perintah otomatis yang kita buat ketika kita ngepush ke gitlab. Eh ngertikan maksudnya, jadi kalo kalian mainan gatsby kan biasnaya harus gatsby develop, nah trus milih pathnya dan lain lain lah, nah ini kita bikin otomatis dengan bantuan gitlab ci.

Caranya kita bikin file baru dengan nama `.gitlab-ci.yml` bisa manual bisa juga kayak gini

```bash
touch .gitlab-ci.yml
```

nah di dalamnya kita isi kayak gini

```bash
image: node:latest

cache:
  paths:
    - node_modules/

pages:
  script:
    - npm install
    - ./node_modules/.bin/gatsby build --prefix-paths
  artifacts:
    paths:
      - public
  only:
    - master
```

Perlu penjelasan ga?
pasti perlu lah ya, intinya barus paling atas itu untuk definisiin akan node paling terbaru. Selanjutnya cache, nah kalo udah install npm kan biasanya jarang banget ada update mending di cache biar ga ngabisin resource, jadi intinya cache, apa ya bahasa indonesianya, pokonya biar inget ga instal-instal lagi gitulah. Pages, nah pertama itu biasa sama kayak `npm install` gitu, directory node modulesnya, trus artifact ini adalah halaman yang di akses jadi kalo di gatsby build kan jadinya ada folder public nah folder ini yang di akses, selanjutnya `only: - master` itu adalah branch yang akan di deploy.

Kalo udah kalian bisa pergi ke menu `Settings->Pages` kalo udah ada **Access pages** berarti udah berhasil

![](../images/screenshot-gitlab01.png)

Selanjutnya gimana cara ngatur domain tinggal masuk ke menu new domain, lalu isikan domain kalian, iya lagi-lagi saya anggap kalian sudah punya, contoh disini saya pakai `infohondamalang.id` lalu klik create new domain, untuk certificate dan key kosongin aja lebih dulu. Nah kalo ada eror https gitu, uncheck _Force HTTPS_ menu sebelumya tadi

Lebih detailnya lagi atau lengkapnya untuk domain ini bisa tontoh video tutorial di youtube saya yah [devindo](https://youtube.com/devindo)


Semoga bermanfaat

