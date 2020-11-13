---
title: Solusi Lupa Password Pada Wordpress
author: aderana
date: 2010-04-25T17:50:14+07:00
layout: post
link: https://94nr0.wordpress.com/2010/04/26/solusi-lupa-password-pada-wordpress/
category: teknologi
tags:
- password
- phpmyadmin
- wordpress
teaser: Mengganti password CMS Wordpress melalui phpMyAdmin.
---

Beberapa hari yang lalu, saya sempat bingung karena saya lupa password blog saya. Saya mencoba menggunakan fasilitas lupa password yang diberikan wordpress, akan tetapi fasilitas itu tidak berfungsi, karena password barunya belum juga terkirim ke email saya. Akhirnya saya memutuskan untuk langsung mengganti password baru dari phpmyadmin.

Berikut ini adalah cara untuk mengganti password wordpress dari phpmyadmin :

![Database](https://94nr0.files.wordpress.com/2010/04/1.png){:class="image-wrapper"}

1. Bukalah phpmyadmin lalu carilah database wordpress anda
2. pada halaman daftar tabel yang ada pada database tersebut, perhatikan nama tabel wp_users. Klik ikon Browse yang ada disebelah kanan nama tablenya seperti gambar ilustrasi di bawah ini.
3. ![Table-wp_users](http://94nr0.files.wordpress.com/2010/04/2-300x19.png){:class="image-wrapper-left__list"}
4. pastikan user mana yang akan diubah username untuk login dan/atau password-nya. Jika sudah dipastikan, pada baris data user tersebut klik icon pensil seperti ditunjukkan gambar ilustrasi berikut ini.
5. ![Field-user](http://94nr0.files.wordpress.com/2010/04/3-300x25.png){:class="image-wrapper-left__list"}
6. pada baris user_pass, ini merupakan data password yang digunakan, namun di sini password disimpan dengan teknik pengkodean MD5 agar tidak terbaca secara kasat mata. Untuk mengubahnya, kita isikan dengan password baru yang akan digunakan, kita ketikkan apa adanya, namun pada pilihan Function-nya kita pilih MD5. Sesudah itu klik tombol Go untuk menyimpan perubahan data user tersebut.
7. ![Field-pass](http://94nr0.files.wordpress.com/2010/04/4-300x11.png){:class="image-wrapper-left__list"}

##### SELAMAT MENCOBA