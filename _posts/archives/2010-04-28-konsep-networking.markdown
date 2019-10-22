---
title: Konsep Networking
author: aderana
date: '2010-04-28 13:32:02 +0000'
layout: post
link: https://94nr0.wordpress.com/2010/04/28/konsep-networking/
category: teknologi
tags:
- lan
- switch
- network
teaser: Penjelasan mengenai switch yang rusak tetapi masih dapat mengirim paket.
---

Misalkan ada switch yang rusak kesamber petir, 1 switch itu dapat mengakibatkan gangguan terhadap jaringan lainnya. Contohnya:

> #### nih ada 4 pc:
> 
> `pc 1 reply ke pc 2`
> `pc 1 rto ke pc 3`
> `pc 1 rto  ke pc 4`
> 
> `pc 2 reply ke pc 1`
> `pc 2 rto ke pc 3`
> `pc 2 reply ke pc 4`
> 
> `pc 3 rto ke pc 4`
> `pc 3 rto ke pc 1`
> `pc 3 rto ke pc 2`
> 
> `pc 4 rto ke pc  1`
> `pc 4 rto ke pc 2`
> `pc 4 rto ke pc 3`

yg bikin gw bingung itu, rto tapi masih ada pc yg bisa chattingan, tapi  ga bisa ngambil share, tapi bisa buka webserver di pc yg rto itu. zzz,  jng kan begitu, yang lebih aneh lagi ada pc yg rto ke pc yang masang  squid tapi bisa pake proxy pc yg masang squid itu. zzz

Sebenarnya masalah ini sudah lama, cuman baru kali ini saya dapat menuliskannya ke blog.  dan sudah dijawab oleh [5ynL0rd](http://depredac0de.net/discussion/memberlist.php?mode=viewprofile&u=2)

klo switch rusak masalah yg paling sering paling elconya jebol (ini  jelas ngaruh, gampang RTO & switching sering terganggu), biasanya  panas berlebih di switch, atau masalah cache switch yg penuh (byk yg mac  flooding atau ada worm yg tindakannya mac flooding jg), kalo tu cache  penuh:

* switch jadi revert ke hub untuk alamat hardware yang  tidak dapat diterima cache. Performa switch bakal menurun, tapi traffic  akan terus berjalan untuk mengantarkan paket.
* switch bisa membagi  ke buffer dan menerima data baru. Paket akan dikirim ke hub sampai  switch mempelajari penempatan port dari host (switch2 sekarang)

masalah  diatas kalo memang hardwarenya udah baik, bisa lari ke:
* firewall
* worm
* salah konfigurasi

![network](http://94nr0.files.wordpress.com/2010/04/code.jpg){:class="image-wrapper"}

switch B anggap  rusak, maka:
* client A masih bisa terhubung ke Internet, Client B  Jelas tidak bisa.
* Client A tidak bisa berkomunikasi ke B, tetapi  bisa berkomunikasi ke C, begitu juga dengan C, bisa berkomunikasi ke A  tetapi tidak bisa berkomunikasi ke B

kalo nentuin switch mana yg  rusak simpel, bangun koneksi sama host2 yg berhubungan langsun ma tu  switch, misal switch A rusak, otomatis client B ga bisa komunikasi ke A,  C bahkan ke Internet (karena router terhubung langsung ke switch A).

itu  asumsi kalo switch benar2 ga bisa berfungsi sm sekali (parahnya ga  nyala sm sekali), kalo switch yg bermasalah sama kinerja (panas)  biasanya sekedar bangun koneksi masih bisa, tapi kalo udah tes througput  bakal buruk, cara paling sederhana transfer data dgn jumlah cukup besar  atau uji keseimbangan downstream n upstreamnya sama aplikasi2 yg butuh  latency tinggi (misal game).

nb: membangun koneksi macem2 caranya,  bisa cuma sekedar 3 way handshake ke port yg diyakini terbuka, bisa  pake ICMP (ping, traceroute), ato manfaatin service jaringan yg ada di  host tujuan

nih diskusi yang lebih legkapnya -> [sumber](http://depredac0de.net/discussion/viewtopic.php?f=112&t=217&start=20)