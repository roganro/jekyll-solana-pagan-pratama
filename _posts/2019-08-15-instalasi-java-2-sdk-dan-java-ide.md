---
title: Instalasi Java 2 SDK dan Java IDE
author: Pagan
date: '2017-01-30 16:57:02 +0000'
layout: post
teaser: Langkah-langkah untuk menginstall Java (SDK tentunya) pada Linux.
link: http://javaonlinux.xyz/?p=15
category: teknologi
tags:
- linux
- java
- sdk
- ide
- ubuntu
- persiapan
- instalasi
---

Jika hanya untuk kepentingan mengoperasikan Java bytecode, Anda hanya cukup menginstal _Java Runtime Environment_ (JRE). Namun, dengan hanya mengandalkan JRE, Anda tidak dapat membuat program dalam bahasa Java. Dibutuhkan lebih dari sekedar JRE, yaitu SDK (_Software Development Kit_) yang mempunyai compiler didalamnya, selain JRE. Berikut ini langkah-langkah untuk menginstall Java (SDK tentunya) pada Linux.

1. Dapatkan file instalasi Java 2 SDK dengan cara download di website Oracle melalui [http://www.oracle.com/technetwork/java/javase/downloads/index.html][j2sdk]{:target="_blank"}.
2. Pilih NetBeans with JDK 8 (Pada saat saya mendownload, versi yang dianjurkan adalah JDK 8u111 with NetBeans 8.2).
3. Klik Accept License Agreement.
4. Pilih file instalasi yang sesuai dengan arsitektur sistem operasi Linux yang anda gunakan (Saat ini saya menggunakan Ubuntu 16.10 x64, oleh karena itu saya mendownload file untuk Linux x64).
5. Setelah download, file yang Anda peroleh masih berupa file shell script (jdk-8u111-nb-8_2-linux-x64.sh) yang belum dapat dieksekusi. Untuk itu ubah mode file tersebut di direktorinya agar dapat dieksekusi dengan cara:

   `shell> chmod +x jdk-8u111-nb-8_2-linux-x64.sh`

6. Kemudian, eksekusi file tersebut di direktorinya melalui:

   `shell> ./jdk-8u111-nb-8_2-linux-x64.sh`

7. Selanjutnya, akan ditampilkan halaman instalasi, klik tombol next dan anda akan dihadapkan di direktori mana anda akan menginstall JDK (contoh punya saya ada di /home/pagan/jdk1.8.0_111). Lalu dihalaman selanjutnya anda akan ditanya untuk di direktori mana anda akan menginstall NetBeans IDE (contoh kepunyaan saya ada di /home/pagan/netbeans-8.2) dan direktori JDK yang akan dipakai oleh NetBeans.

Setelah instalasi selesai, langkah terakhir adalah memodifikasi PATH dan CLASSPATH, dengan cara (disini saya menggunakan ubuntu 16.10, tiap linux mempunyai cara pengaturan yang berbeda, tetapi prinsipnya tetap sama, jadi disesuaikan saja):

1. Masuklah ke console
2. Ketiklah

   `shell> nano .bashrc`

3. Pada akhir baris, ketiklah:

   `export JAVA_HOME=/home/pagan/jdk1.8.0_111`

   `export PATH=$JAVA_HOME/bin:$PATH`

   `export CLASSPATH=./:$CLASSPATH`

   /home/pagan/jdk1.8.0_111 merupakan direktori Java2 SDK yang tadi kita install, ini bisa dirubah sesuai di direktori mana anda menginstall Java2 SDK. Direktori _bin_ merupakan lokasi file executable dari berbagai program Java, antara lain _javac_ (untuk compiler kode java) dan _java_ (untuk menjalankan file class dari hasil compiler). Sedangkan untuk CLASSPATH digunakan untuk menempatkan direktori kerja sebagai salah satu lokasi pencarian file class.

4. Pencet tombol Ctrl+X, Y, dan Enter.
5. Keluarlah dari console dengan cara mengetik exit, buka console baru dan ketiklah $JAVA_HOME. Jika sudah benar hasilnya akan seperti ini:

   `bash: /home/pagan/jdk1.8.0_111: Is a directory`

6. Dan perintah _java_ dan _javac_ sudah bisa digunakan.

Sekian dulu untuk tutor kali ini, kalau ada yang membingungkan, tanyakan saja di thread ini langsung atau bisa contact saya lewat pm atau email.

[j2sdk]: http://www.oracle.com/technetwork/java/javase/downloads/index.html
