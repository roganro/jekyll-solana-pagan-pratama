---
title: Instalasi Connector antara Java dan MySQL
author: Pagan
date: '2017-01-30 07:02:22 +0000'
layout: post
teaser: Satu komponen lagi yang harus Anda instal adalah driver JDBC untuk MySQL. Driver ini akan kita perlukan dalam mempelajari koneksi antara database MySQL dengan Java.
link: http://javaonlinux.xyz/?p=34
category: teknologi
tags:
- java
- connector
- mysql
- persiapan
- instalasi
---

Satu komponen lagi yang harus Anda instal adalah driver JDBC untuk MySQL. Driver ini akan kita perlukan dalam mempelajari koneksi antara database MySQL dengan Java. Database MySQL merupakan database relasional yang paling banyak digunakan di Linux dan Windows. Dengan demikian, akan banyak berguna bagi aplikasi yang sengaja dibangun untuk berjalan di berbagai platform.

Pada post sebelumnya yang berjudul [Instalasi Java 2 SDK dan Java IDE][nisi]{:target="_blank"}, dijelaskan cara menginstall JDK dan IDE, dan IDE yang di instal adalah NetBeans. Di dalam NetBeans sudah terdapat driver JDBC, jika ingin menggunakannya klik menu Window>Services atau tekan Ctrl+5. Pilih Databases>Drivers> klik kanan MySQL(Connector/J driver) dan pilih Connect Using

![Connector][connector]{:class="image-wrapper"}

Jika semua langkah instalasi sudah dilengkapi, tentunya kita dapat melangkah ke tahap selanjutnya dengan tenang. Semua kebutuhan untuk pengembangan aplikasi Java sudah dipersiapkan sebelumnya.

[nisi]: {% link _posts/2019-08-15-instalasi-java-2-sdk-dan-java-ide.md %}
[connector]: https://farm1.staticflickr.com/275/31411927043_3e3ccc9a91_o_d.png
