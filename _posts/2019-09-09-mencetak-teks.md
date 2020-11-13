---
title: Mencetak Teks
author: Pagan
date: 2017-01-30T19:32:53+07:00
layout: post
teaser: Pembahasan dengan membuat program untuk menulis teks di atas layar dengan
  Java.
link: http://javaonlinux.xyz/?p=43
category: teknologi
tags:
- java
- linux
- ubuntu
- code
---

Kita akan memulai pembahasan ini dengan membuat program untuk menulis teks di atas layar dengan Java.

> #### praktek01.java
> ![praktek01][praktek01.java]{:class="image-wrapper-left__list"}

Seperti yang telah dibahas sebelumnya, System.out.println digunakan untuk mencetak teks dalam bahasa Java. Anda cukup menulis kalimat demi kalimat di dalam tanda kurung dengan diawali dan diakhiri tanda petik dua (***double-quotes***). Jangan lupa untuk menutup perintah dengan tanda titik-koma (***semicollon***).

Sebenarnya, System.out.println() terdiri atas tiga bagian utama. Output yang dihasilkan sebenarnya berasal dari metode println() yang telah tersedia di dalam Java (***built-in***). Sedangkan System merupakan class yang menyediakan fasilitas akses ke dalam system. Dan yang terakhir, keyword ***out***, adalah output stream yang menghubungkan dengan console.

Seperti yang Anda duga, jika ketiganya dibaca akan memperlihatkan langkah-langkah yang dilakukan Java dalam menghasilkan cetakan di layar.

Selanjutnya, kita akan melanjutkan mencetak teks di atas layar dengan isi yang lebih kompleks.

> #### praktek02.java
> ![praktek02][praktek02.java]{:class="image-wrapper-left__list"}

Program praktek02.java merupakan pengembangan dari program sebelumnya, yang hanya menambah jumlah baris perintah menjadi lebih dari satu baris. Eksekusi program di atas akan menghasilkan output seperti di bawah ini:

![output][output]{:class="image-wrapper-left__list"}

[praktek01.java]: https://farm1.staticflickr.com/529/31847060430_4d0a7caaaa_o_d.png
[praktek02.java]: https://farm1.staticflickr.com/654/31852361510_6fc2d99351_o_d.png
[output]: https://farm1.staticflickr.com/296/31417825173_4c815d6e8a_o_d.png