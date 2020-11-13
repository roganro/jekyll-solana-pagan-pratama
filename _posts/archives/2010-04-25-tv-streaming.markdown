---
title: Tv Streaming Server Side
author: aderana
date: 2010-04-25T19:16:17+07:00
layout: post
link: https://94nr0.wordpress.com/2010/04/26/tv-streaming/
category: teknologi
tags:
- unreal
- streaming
- lan
- windows
teaser: Membuat server tv stream menggunakan unreal untuk jaringan lokal.
---

Saya ingin menunjukkan bagaimana cara membuat tv streaming di jaringan, tapi sebelumnya, saya ingin menjelaskan terlebih dahulu apa itu *tv streaming* ? 

<dfn>Televisi internet</dfn> (juga dikenal dengan <dfn>Televisi daring</dfn> (TV Online) adalah situs yang memiliki tayangan video yang terkonsep, selalu diperbaharui terus-menerus, tidak statis, mengikuti perkembangan peristiwa yang terjadi di lingkungan sekitar, dan bisa diakses oleh publik secara bebas, dengan berbagai macam bentuk pendistribusiannya. 

Untuk dapat mengaksesnya, kita hanya perlu menguhubungkan ke [komputer pribadi][kp] kita dengan koneksi internet [broadband][bro] berlangganan. oke, setelah saya menjelaskan apa itu tv streaming, sekarang saya akan langsung membahas bagaimana cara membuatnya.

#### Alat-alat yang dibutuhkan:

* CPU
* Antena Tv
* Tv Tunner Internal
* Koneksi Jaringan (tidak mesti selalu internet, pakai jaringan lokal)

Saya berasumsi bahwa anda telah selesai memasang tv tunner internal tersebut di pc, langsung saja saya ke pembahasan tentang membuat agar tv yang telah bisa di tonton di tv anda bisa di tonton juga oleh orang lain yang berada dalam satu jaringan dengan anda.

Saya disini menggunakan software untuk Windows Xp, kalau buat Linux belum ketemu caranya.

#### Server Side Software (sisi server)

* Download [Unreal Media Server][ums]
* Download [Unreal Live Server][uls]

Setelah selesai anda download dan di install kedalam pc anda, sekarang saya akan memberikan illustrasi gambar untuk menyettingnya :

1. buka Live Server Configurator → klik File → add media source

   ![add media source](/i/1.png){:class="image-wrapper-left__list"}

2. Ceklist add video channel → pilih tv tunner internal anda

   ![add video provider](/i/2.png){:class="image-wrapper-left__list"}

3. pilihlah Apply Software Compression

   ![select capture media type](/i/3.png){:class="image-wrapper-left__list"}

4. pilih video tunner in pada box input

   ![set video provider parameters](/i/4.png){:class="image-wrapper-left__list"}

5. Selanjutnya next, ceklist add audio channel, pilih sound card kamu

   ![add audio provider](/i/5.png){:class="image-wrapper-left__list"}

6. pilihlah Apply Software Compression

   ![select capture media type](/i/6.png){:class="image-wrapper-left__list"}

7. pilih Line In pada box input

   ![set audio provider parameters](/i/7.png){:class="image-wrapper-left__list"}

8. Selanjtunya pilih Buffer dan LAN

   ![choose encoding profile](/i/8.png){:class="image-wrapper-left__list"}

9. Next, ingat source id yang tertera dan deskripsikan tv streamingmu

   ![source info](/i/9.png){:class="image-wrapper-left__list"}

10. Finish


Nah settingan diatas digunakan di Live Server Configurator, selanjutnya saya akan memberikan contoh settingan Media Server Configurator :

1. buka Media Server Configurator → klik File → New Live Broadcast
2. Pilih Dynamic Live Broadcast
3. Isi Alias dengan nama yang telah dideskripsikan di Live Server Configurator
4. Klik set password untuk mengeset password → contoh pass : 12345
5. Klik ok


Sekarang Buka Live Server Configurator, klik kanan pada Live Source yang telah dibuat, klik connect to media server

isi password dengan password yang telah di isi di media server configurator

klik connect

Untuk [Client Side][cs], saya akan menjelaskannya pada sesi [selanjutnya][cs]

[kp]: http://id.wikipedia.org/wiki/Komputer_pribadi
[bro]: http://id.wikipedia.org/wiki/Broadband
[ums]: http://www.umediaserver.net/bin/UMediaServer.zip
[uls]: http://www.umediaserver.net/bin/ULiveServer.zip
[cs]: {%link _posts/archives/2012-12-24-tv-streaming-client-side.markdown %}