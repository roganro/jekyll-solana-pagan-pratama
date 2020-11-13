---
title: Codec Buat Nyetel rmvb di Ubuntu Jaunty
layout: post
teaser: Cara Memainkan File RMVB Pada Sistem Operasi Ubuntu Jaunty.
category: teknologi
tags:
- linux
- ubuntu
- multimedia
- video
author: aderana
date: 2010-04-25T05:59:59+07:00
link: https://94nr0.wordpress.com/2010/04/25/hello-world/
---

Caranya mudah. Yang perlu anda lakukan adalah menginstall paket w32codecs. Sebelumnya buat atau tambahkan dulu repo Medibuntu di sources.list anda.

```bash
echo "deb http://packages.medibuntu.org/ jaunty free non-free" >> /etc/apt/sources.list

apt-get update

apt-get install w32codecs
```

Nah, seharusnya sekarang anda sudah bisa menjalankan file .rmvb (biasanya anime atau film-film yang didownload dari internet). Tentunya dengan syarat anda sudah memiliki player yang sudah terinstall. Misalnya, mplayer, totem atau vlc.