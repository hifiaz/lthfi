---
date: 2019-04-16
title: 'Crawling Instagram Gempi'
template: post
thumbnail: '../thumbnails/crawling.png'
slug: crawling-instagram-gempi
categories:
  - crawling
  - nodejs
  - Programming
tags:
  - blog
  - gempi
  - instagram
---

Cwaling data merupakan suatu hal yang mungkin kita butuhkan untuk menganalisa sesuatu, data ini kita bisa dapet dari website atau social media, tapi ga semua social media bisa open datanya contoh kayak facebook banyak sekali akses yang di tutup sehingga susah untuk crawling datanya.

Nah masih seperusahaan sama facebook instagram sebagian datanya masih bisa di buka sehingga mudah untuk mendapatkan datanya, salah satu kita bisa ambil berdasarkan hastag. `https://www.instagram.com/explore/tags/gempi/`

nah untuk mendapatkan jsonnya kita tinggal tambahin `?__a=1` langsung deh kita dapet file jsonnya, nah dari sini kita mulai untuk bikin scrappernya dan kali ini pake nodejs langsung saja ikuti

```bash
mkdir instagram-crawling
cd instagram-crawling
npm init -y
npm i axios
touch index.js
```

Kalo udah buka folder/index.js dengan program editor kalian. nah selanjutnya kita coba ambil json ini dengan axios

```bash
const axios = require('axios');

function getIG() {
  axios.get("https://www.instagram.com/explore/tags/gempi/?__a=1").then(res =>
    console.log(res.data)
  );
}

getIG();
```

nah udah dapetkan jsonnya kalo mau ngambil mentah itu bisa langsung ambil kita export ke file json kita pake fs
```bash
const axios = require("axios");
const fs = require("fs");

function getIG() {
  axios.get("https://www.instagram.com/explore/tags/gempi/?__a=1").then(res => {
    fs.writeFile("instagram.json", JSON.stringify(res.data, null, 4), res =>
      console.log("Success Writen")
    );
  });
}

getIG();
```
nah nanti otomatis akan nulisin file json yang kita kasih judul instagram kayak di atas itu, kalo di lihat json.stringify ada null dan 4 itu untuk merapikan file jsonnya.

Coba kita detailin lagi, jadi maksudnya kalo itu kan json mentah nah kalo mau ngambil yang topnya aja gimana? tinggal kita bikin fungsi looping untuk node yang kita pilih disini saya contohin node top

```bash
function topIG() {
  axios.get("https://www.instagram.com/explore/tags/gempi/?__a=1").then(res => {
    const item = res.data.graphql.hashtag.edge_hashtag_to_top_posts.edges;
    fs.writeFile("topinstagram.json", JSON.stringify(item, null, 4), res =>
      console.log("Success Writen")
    );
  });
}
```
nah bedanya di responnya itu kita detailin ke item edge_hastag_to_top_posts kalo kalian lihat jsonnya pasti untuk detail di top post dapet jumlah like dan lainnya, nah kalo kalian mau download photo-photonya tinggal di foreach lalu di ambil deh itu

Semoga bermanfaat
NB. jangan di manfaatkan untuk hal yang tidak berguna yah

