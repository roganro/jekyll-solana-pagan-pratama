---
title: Membuat Repository Ubuntu 9.04 Dari File Iso
author: aderana
comments: true
date: '2010-04-25 19:57:24 +0000'
layout: post
link: https://94nr0.wordpress.com/2010/04/26/membuat-repository-ubuntu-9-04-dari-file-iso/
category: teknologi
tags:
- linux
- repositori
- ubuntu
- foss
teaser: Langkah untuk membuat repositori dari file ISO untuk distro linux Ubuntu.
---

Langsung saja ya, tidak perlu basa-basi lagi.

**First Step**

1. unduh atau download file iso nya dari sini nih → [ftp://kambing.ui.ac.id/iso/ubuntu-repository/9.04][kambing]
2. kalau sudah selesai, buka terminal or shell ketik → `user$ sudo mount <tempat dimana file isonya berada> <tempat buat menaruh file hasil mountnya> -o loop`

> #### example:
> 
> `user$ sudo mount /media/disk-5/repo/ubuntu-cd1.iso /home/user/dokumen/data/1 -o loop`

**Second Step**

1. buka terminal or shell ketik → `user$ sudo nautilus`
2. buka file source.lst dengan editor apa aja sesuai keinginan anda (file ini letaknya di /etc/apt/source.lst)
3. kalau komputer anda terhubung dengan internet, biarkan saja repo yang sudah ada. tetapi jika komputer anda tidak terhubung dengan internet, berikan tanda # kepada repository yang menunjukkan alamat http
4. ketik 
   `deb <tempat dimana file hasil mount berada>`
	 `deb-src <tempat dimana file hasil mount berada>`

> #### example:
>     
> `deb file:///home/user/dokumen/data/1 jaunty main universe`
> `deb-src file:///home/user/dokumen/data/1 jaunty main universe`

**Third Step**

1. save file source.lst tadi yang sudah di edit, sekarang buka aplikasi synpatic
2. klik refresh
3. finish
4. Selamat Menginstall Ria ^_^

[kambing]: ftp://kambing.ui.ac.id/iso/ubuntu-repository/9.04