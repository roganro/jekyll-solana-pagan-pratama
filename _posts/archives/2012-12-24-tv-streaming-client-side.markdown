---
title: Tv Streaming Client Side
author: Pagan
date: '2012-12-24 20:11:32 +0000'
layout: post
teaser: Tutorial untuk menonton tv streaming yang di broadcast oleh Unreal Media Server.
link: https://94nr0.wordpress.com/2012/12/25/tv-streaming-client-side/
category: teknologi
tags:
- unreal
- streaming
- lan
- windows
---

![TV][tv]{:class="image-wrapper"}


   Tahun 2010 saya pernah menulis artikel mengenai pembuatan [Tv Streaming][tvs], meskipun hanya dasarnya dan disisi Server saja. Saya pernah berjanji akan menulis artikel disisi Client, tetapi baru kali ini saya baru sempat untuk menulisnya.

   Karena sudah lama sekali tidak menggunakan Unreal Media Server dan Live Server, ketika mencoba mengunduh (download) dan menginstall untuk keperluan penulisan client side, cukup mengagetkan juga, karena cukup banyak perubahan dibagian encoding audio & video.

Artikel kali ini membahas client side, jadi kita tinggalkan saja mengenai perubahan Unreal Media Server dan Live Server.

Langsung saja ke pembahasan utamanya


### Alat yang dibutuhkan:

* 2 Buah device (bisa berupa 2 pc/2 laptop/1 pc & 1 laptop/1 pc atau laptop & smartphone),
* Sebuah koneksi (bisa berupa LAN berarti menggunakan kabel _UTP / WAN _yang menggunakan Wireless sebagai medianya).


### Client Side Software:

Streaming Media Player bisa diunduh → [di sini][mp]
	
* Tampilan awal Streaming Media Player setelah di install
   
   ![Streaming Media Player][smp]{:class="image-wrapper-left__list"}
	
* Klik Play, pilih Play live broadcast
   
   ![Play live broadcast][plb]{:class="image-wrapper-left__list"}
	
* Isi Media Server IP Address dengan IP Address yang telah dikonfigurasi pada sisi Server sebelumnya, pilih protocol nya seperti yang telah ditentukan sebelumnya pada konfigurasi Live Server dan Alias of live broadcast. Untuk port biarkan 5119 seperti defaultnya.

   ![Play live broadcast][plbc]{:class="image-wrapper-left__list"}
	
* Setelah diklik ok, maka akan muncul hasilnya

   ![hasil][hasil]{:class="image-wrapper-left__list"}


Pasti bakalan banyak yang nanya, `cara ganti channelnya gimana?`

itu bisa dilakukan jika kalian sudah mengembed Streaming Media Player ini ke web yang berbasis server IIS. Untuk sementara kalau mau pindah channel, request ke server.


### Add-Ons

Web application for remote TV channel control bisa diunduh (download) → [disini][disini]

Tapi ingat ini hanya bisa dipakai kalau servernya sudah menginstal IIS.


#### Awas jangan di tiru

Sebenarnya yang bikin penulisan ini baru keluar sekarang, itu karena banyak hal:

* Hardwarenya rusak (tv tunner internal dahulu kala),
* Perkuliahan yang belum kelar sampe sekarang, hahaha,
* Game online,
* Tidak ada ide untuk menulis & males buka blog.


[tv]: http://94nr0.files.wordpress.com/2012/12/tvicon.png
[tvs]: {% link _posts/archives/2010-04-25-tv-streaming.markdown %}
[mp]: http://www.umediaserver.net/bin/StreamingMediaPlayer.zip
[smp]: http://94nr0.files.wordpress.com/2012/12/untitled.png
[plb]: http://94nr0.files.wordpress.com/2012/12/untitled2.png
[plbc]: http://94nr0.files.wordpress.com/2012/12/untitled3.png
[hasil]: http://94nr0.files.wordpress.com/2012/12/untitled4.png
[disini]: http://www.umediaserver.net/bin/TVChannelChanger.zip
