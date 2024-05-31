---
date: 2019-12-02
title: "Panduan Singkat Git"
template: post
thumbnail: "../thumbnails/git.png"
slug: panduan-singkat-git
categories:
  - Git
  - Programming
tags:
  - blog
  - git
  - gitlab
  - github
---

Sering kali saya tidak ingat untuk perintah perintah sederhana di git, ini sebenernya karena tidak tiap saat pake perintah aja, kayak bikin branch delete atau perintah yang jarang kita pake pasti banyak sedikitnya lupa, nah biar enak saya dokumentasiin aja di sini biar kalo lupa tinggal buka duende

1. Mengecek list branch

```bash
  git branch -a
```

2. Pindah-pindah branch

```bash
  git checkout nama_branch
```

3. Membuat branch baru di lokal

```bash
  git checkout -b nama_branch_baru
```

4. Push branch baru

```bash
  git push origin nama_branch_baru
```

5. Delete branch

```bash
  git push origin :nama_branch_baru
```

5. Update branch kalau dari official/master repo ada update

```bash
  git fetc nama_branch_official
```

nah itu dulu aja paling, karena ini bersifat dokumentasi ya ini bermanfaat buat saya, dan semoga buat anda juga

Jangan lupa subscribe youtube saya yah [devindo](https://youtube.com/devindo)

Semoga bermanfaat
