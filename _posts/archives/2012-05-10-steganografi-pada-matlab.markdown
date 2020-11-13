---
title: Steganografi pada MATLAB
author: Pagan
date: 2012-05-10T13:15:35+07:00
layout: post
teaser: Steganografi tidak mengubah pesan menjadi kode-kode tertentu melainkan menyisipkan
  pesan pada suatu objek, dimana objek yang telah disisipi pesan tidak akan mengalami
  perubahan fisik secara kasat mata.
link: https://94nr0.wordpress.com/2012/05/10/steganografi-pada-matlab/
category: teknologi
tags:
- matlab
- steganografi
- kriftografi
- linux
- windows
---

![Steganografi][stegano]{:class="image-wrapper"}


   Kriptografi adalah cara yang paling umum untuk penyampaian pesan rahasia dari pihak pertama ke pihak ke dua, meskipun kekuatan keamanannya tergantung algoritme kriptografi apa yang digunakan. Meskipun kriptografi memiliki kekuatan keamanan tertentu dalam menyampaikan pesan rahasia namun hal tersebut mampu menimbulkan kecurigaan dari pihak yang tidak lain yang juga ingin mengetahui isi pesan tersebut. Hal ini disebabkan karena secara umum prinsip kriptografi adalah mengubah suatu pesan yang bisa dipahami secara langsung menjadi kode-kode yang tidak bisa dipahami secara langsung, sehingga pihak lain yang melihat adanya pengiriman kode-kode tersebut akan mencurigai bahwa kode-kode tersebut adalah suatu pesan rahasia. Mereka akan berusaha dengan segala cara untuk mengetahui isi dari pesan tersebut.

   Steganografi adalah jawaban terhadap tantangan di atas. Steganografi tidak mengubah pesan menjadi kode-kode tertentu melainkan menyisipkan pesan pada suatu objek, dimana objek yang telah disisipi pesan tidak akan mengalami perubahan fisik secara kasat mata. Hal ini menguntungkan karena tidak akan menimbulkan kecurigaan pihak lain.

   Setelah proses perancangan dan _coding_ program selesai, selanjutnya adalah pengimplementasian dan ujicoba program aplikasi. Di bawah ini merupakan tampilan output aplikasi Steganografi yang dibuat menggunakan MATLAB:
	
* Struktur Navigasi
--------------------------------------

   ![Struktur Navigasi][sn]{:class="image-wrapper-left__list"}

* Tampilan Menu Steganografi
--------------------------------------

   ![Menu](/i/menu.png){:class="image-wrapper-left__list"}
	 
	 ![Menu](/i/menu-2.png){:class="image-wrapper-left__list"}
	
* Tampilan Proses Kerja Program Encode
--------------------------------------

   ![Encode](/i/encode-1.png){:class="image-wrapper-left__list"}

   ![Encode](/i/encode-2.png){:class="image-wrapper-left__list"}

   ![Encode](/i/encode-3.png){:class="image-wrapper-left__list"}

   ![Encode](/i/encode-4.png){:class="image-wrapper-left__list"}

   ![Encode](/i/encode-5.png){:class="image-wrapper-left__list"}

* Tampilan Proses Kerja Program Decode
--------------------------------------

   ![Decode](/i/decode-1.png){:class="image-wrapper-left__list"}

   ![Decode](/i/decode-2.png){:class="image-wrapper-left__list"}

   ![Decode](/i/decode-3.png){:class="image-wrapper-left__list"}


#### Referensi

[1] Habes, Alkhraisat (2006),”Information Hiding in BMP image Implementation, Analysis and Evaluating ”, _Information Transmition in Computer Network_, Saint Petersburg Institute for Informatics and Automation, Russian Academy of Sciences, Saint Petersburg, Russia.

[stegano]: http://94nr0.files.wordpress.com/2012/05/tts.png
[sn]: https://94nr0.files.wordpress.com/2012/05/untitled12121.png