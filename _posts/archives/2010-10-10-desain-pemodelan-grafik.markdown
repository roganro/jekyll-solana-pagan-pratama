---
title: Desain Pemodelan Grafik
author: aderana
date: '2010-10-10 16:42:56 +0000'
layout: post
link: https://94nr0.wordpress.com/2010/10/10/desain-pemodelan-grafik/
category: teknologi
tags:
- grafik
- model
teaser: Desain pemodelan grafik sangat berkaitan dengan grafik komputer.
---

Desain pemodelan grafik sangat berkaitan dengan grafik komputer. Berikut adalah kegiatan yang berkaitan dengan grafik komputer:

1. Pemodelan geometris: menciptakan model matematika dari objek-objek 2D dan 3D.
2. Rendering: memproduksi citra yang lebih solid dari model yang telah dibentuk.
3. Animasi: Menetapkan/menampilkan kembali tingkah laku behaviour objek bergantung waktu.


Kerangka Grafik Komputer

1. Graphics Library/package (contoh : OpenGL) adalah perantara aplikasi dan display hardware(Graphics System)
2. Application program memetakan objek aplikasi ketampilan/citra dengan memanggil graphics library
3. Hasil dari interaksi user menghasilkan/modifikasi citra
4. Citra merupakan hasil akhir dari sintesa, disain, manufaktur, visualisasi dll.


Pemodelan Geometris
Transformasi dari suatu konsep (atau suatu benda nyata) ke suatu model geometris yang bisa ditampilkan pada suatu komputer:
	
* Shape/bentuk
* Posisi
* Orientasi  (cara pandang)
* Surface Properties / Ciri-ciri Permukaan (warna, tekstur)
* Volumetric Properties / Ciri-ciri volumetric (ketebalan/pejal, penyebaran cahaya)
* Lights/cahaya (tingkat terang, jenis warna)
* Dan lain-lain …


Pemodelan Geometris yang lebih rumit:
	
* Jala-Jala segi banyak: suatu koleksi yang besar dari segi bersudut banyak, dihubungkan satu sama lain.
* Bentuk permukaan bebas: menggunakan fungsi polynomial tingkat rendah.
* CSG: membangun suatu bentuk dengan menerapkan operasi boolean pada bentuk yang primitif.


Elemen-elemen pembentuk Grafik Geometri

Pemrosesan Citra Untuk Ditampilkan di Layar

Hardware Display Grafik: Vektor
	
1. Vetor (calligraphic, stroke, random-scan)
2. Arsitektur Vektor


Hardware Display Grafik: Raster
	
1. Raster (TV, bitmap, pixmap), digunakan dalam layar dan laser printer
2. Arsitektur Raster


Ref:




[http://blog.ukmhg.co.cc/view.php?id=50](http://blog.ukmhg.co.cc/view.php?id=50)