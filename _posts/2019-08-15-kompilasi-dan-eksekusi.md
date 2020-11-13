---
title: Kompilasi dan Eksekusi
author: Pagan
date: 2017-01-30T15:16:08+07:00
layout: post
teaser: Pada Java, program tidak dikompilasi langsung pada hardware masing-masing.
link: http://javaonlinux.xyz/?p=29
category: teknologi
tags:
- java
- linux
- ubuntu
- code
- persiapan
- instalasi
---

Setelah PATH dan CLASSPATH untuk Java 2 SDK diaktifkan, Anda sudah dapat membuat program Java dengan menulis kodenya di text editor pilihan, kemudian mengkompilasinya untuk kemudian menjalankannya.

Dalam menulis program, pemberian nama file Java sebaiknya disamakan dengan nama class utama dalam program. Hal ini akan banyak membantu Anda mengingat file class yang tercipta dari proses kompilasi dan bermanfaat jika Anda menggunakan tool yang akan dibahas pada tutor setelah ini. Contohnya dapat dilihat pada listing sederhana di bawah ini.

Listing **ProgramPertama.java**

```java
class ProgramPertama
{
 public static void main(String[] args)
 {
  System.out.printl("Membuat program dengan Java");
 }
}
```

> #### Pembuatan file ProgramPertama.java dengan nano editor
> 
> ![ProgramPertama][nano]{:class="image-wrapper-left__list"}
> 
> ![ProgramPertamaSource][source]{:class="image-wrapper-left__list"}

Dapat Anda perhatikan dalam contoh di atas, nama file yang digunakan sama dengan nama class utama di dalamnya, baik huruf besar maupun kecilnya.

Sedangkan untuk proses kompilasi bisa dilakukan dengan baiksetelah source-code Java selesai dibuat. Perintah untuk kompilasi adalah sebagai berikut:[^1] 

`shell> javac namafile.java`

Hasil yang Anda peroleh dari perintah di atas adalah file .class yang dapat dieksekusi dengan hanya menggunakan Java Runtime Environment. Perintah untuk menjalankan file .class tersebut adalah sebagai berikut:[^2]

`shell> java namafile`

> Hasil kompilasi file ProgramPertama.java menjadi .class dan output dari program yang dibuat
> 
> ![hasil][hasil]{:class="image-wrapper-left__list"}

Pada Java, program tidak dikompilasi langsung pada hardware masing-masing. Bytecode yang dihasilkan dari compiler (javac), harus diterjemahkan lebih dahulu melalui interpreter (java) sebelum dijalankan pada masing-masing hardware. Jika dilihat dari sisi yang menguntungkan, bytecode dapat dijalankan di semua hardware (yang sudah mempunyai interpreter). Namun, jika dilihat dari sisi yang tidak menguntungkan, proses berjalan lebih lambat dari aplikasi non-Java. Aplikasi non-Java langsung dapat langsung dieksekusi pada masing-masing hardware, namun tidak akan jalan di platform yang lain.

[^1]:
    Oleh karena Anda bekerja di lingkungan Linux, huruf besar dan huruf kecil sangat mempengaruhi (case-sensitive). Jadi, perhatikan huruf-huruf dari nama file yang akan dikompilasi. Jangan lupa menyertakan ekstensi .java (*dot* java) dalam menuliskan nama file yang akan dikompilasi.
    
[^2]:
    Berbeda dengan proses kompilasi yang mengharuskan Anda menyertakan ekstension .java, dalam eksekusi file class dari Java Anda tidak perlu menulis ekstensi .class (*dot* class) di belakang nama file yang akan dieksekusi.

[nano]: https://farm1.staticflickr.com/760/32059089132_57e13e8b5d_o_d.png
[source]: https://farm1.staticflickr.com/589/31397621763_1f77708253_o_d.png
[hasil]: https://farm1.staticflickr.com/759/31397621353_bb0108bd11_o_d.png