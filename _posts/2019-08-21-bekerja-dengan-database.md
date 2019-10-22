---
title: Bekerja dengan Database
author: Pagan
date: '2017-01-30 07:08:40 +0000'
layout: post
teaser: Di dalam aplikasi yang akan Anda buat, dibutuhkan database untuk menyimpan sumber data aplikasi.
link: http://javaonlinux.xyz/?p=32
category: teknologi
tags:
- java
- linux
- mysql
- ubuntu
- persiapan
- instalasi
---

Jika Anda termasuk programmer yang menyukai pemrograman database, bagian ini tentunya dapat Anda ikuti. Database yang akan kita manfaatkan dalam pembuatan aplikasi menggunakan Java adalah MySQL.

Di dalam aplikasi yang akan Anda buat, dibutuhkan database untuk menyimpan sumber data aplikasi. Versi terakhir dari paket program MySQL dapat di-download pada alamat [http://www.mysql.com/downloads][MySQL]{:target="_blank"}. Saat ini, MySQL dapat di-download secara gratis.

MySQL dipilih sebagai alternatif database karena ketersediannya yang mudah di Internet, di-*release* untuk berbagai sistem operasi (termasuk Linux), dan telah tersedia *connector* yang menghubungkan antara aplikasi Java dengan database MySQL.

Dalam instalasi MySQL pada Linux terutama Debian beserta turunannya termasuk Ubuntu, disarankan untuk menggunakan APT repository yang dapat Anda gunakan untuk instalasi server MySQL.

Untuk menjalankan instalasi standar (menggunakan program server dan client MySQL), jalankan:

`shell> sudo apt-get install mysql-server`

Pada saat proses instalasi, akan muncul 2 permintaan yaitu:

* Anda akan diminta untuk memasukkan password untuk user root MySQL.
 * Jika Anda ingin menginstal test database pilih "Ya" atau "Tidak" jika tidak ingin. Pemasangan test database tidak direkomendasikan untuk lingkungan produksi.

Setelah instalasi, periksa terlebih dahulu, apakah file daemon mysqld sudah berjalan dengan menggunakan perintah berikut:

`shell> sudo service mysql status`

Jika hasilnya seperti berikut:

![MySQL Status][status]{:class="image-wrapper"}

File daemon mysqld berarti sudah berjalan dan Anda sudah dapat menggunakan MySQL.

![MySQL][mysql>]{:class="image-wrapper"}

[MySQL]: http://www.mysql.com/downloads
[status]: https://farm1.staticflickr.com/347/32219991435_51815e7457_o_d.png
[mysql>]: https://farm1.staticflickr.com/622/31409725503_3a2e385e98_o_d.png
