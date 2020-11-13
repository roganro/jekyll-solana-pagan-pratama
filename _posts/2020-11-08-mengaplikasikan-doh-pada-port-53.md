---
title: Mengaplikasikan DOH Pada Port 53 
author: Pagan
date: 2020-11-08T19:18:00+07:00
layout: post
teaser: Membuat servis otomatis Cloudflared binary untuk Raspbian 32-bit.
category: teknologi
tags:
- linux
- raspberry
- systemd
- config
- instalasi
- network
---

### Pengertian, Fungsi, serta Perbedaan

DOH merupakan singkatan dari DNS-Over-HTTPS yang berarti DNS atau disebut Domain Name System memakai jalur HTTP atau HTTP/2 melalui port HTTPS yaitu 443 untuk komunikasi trafik antara device dengan DNS Resolver. Selain DOH ada juga DOT (Domain-Over-TLS), keduanya mempunyai fungsi yang sama untuk mengenkripsi lalu lintas data yang diminta oleh device ke mesin DNS Resolver.

Meskipun mempunyai fungsi yang sama, terdapat perbedaan antara DOH dengan DOT, jika DOH memakai port 443 dengan protokol TCP, sedangkan DOT memakai protokol UDP pada port 853. Setelah mengetahui arti, fungsi serta perbedaannya, kali ini saya akan membahas konfigurasi DOH yang menggunakan port standar DNS yaitu 53, dikarenakan dhcpd tidak mendukung untuk menggunakan port lain.

### Konfigurasi DNS-Over-HTTPS pada Raspbian 32-bit

#### Instalasi Cloudflared

**armhf architecture (32-bit Raspberry Pi)**

Unduh cloudflared binary yang telah dikompilasi dan salin ke direktori **/usr/local/bin/** agar dapat dijalankan oleh akun cloudflared atau akun lainnya yang akan dibuat khusus untuk menjalankan program ini. Gunakan flag -v saat menjalankan cloudflared binary untuk memeriksa versi yang dijalankan:

```sh
wget https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-arm.tgz
tar -xvzf cloudflared-stable-linux-arm.tgz
sudo cp ./cloudflared /usr/local/bin
sudo chmod +x /usr/local/bin/cloudflared
cloudflared -v
```

![Cloudflared](/i/cloudflared_version.png){:class="image-wrapper-left__list"}

#### Membuat Servis Otomatis

Setelah semuanya berjalan dengan baik, saatnya membuat sebuah servis otomatis pada systemd agar setiap mesin dinyalakan, program langsung berjalan dan aktif.

Buatlah akun dengan nama cloudflared atau nama lainnya:

`sudo useradd -s /usr/sbin/nologin -r -M cloudflared`

Selanjutnya buat konfigurasi untuk cloudflared binary:

`sudo nano /etc/default/cloudflared`

Karena kita akan membuat program ini berjalan pada port standar DNS yaitu 53, isi konfignya seperti berikut:

```
# Commandline args for cloudflared, using Cloudflare DNS
CLOUDFLARED_OPTS=--upstream https://1.1.1.1/dns-query --upstream https://1.0.0.1/dns-query
```

Jika ingin menggunakan port lain, tambahkan flag --port:

```
# Commandline args for cloudflared, using Cloudflare DNS
CLOUDFLARED_OPTS=--port 5353 --upstream https://1.1.1.1/dns-query --upstream https://1.0.0.1/dns-query
```

Atur hak akses akun yang dibuat sebelumnya untuk cloudflared binary dan berkas konfigurasinya:

```sh
sudo chown cloudflared:cloudflared /etc/default/cloudflared
sudo chown cloudflared:cloudflared /usr/local/bin/cloudflared
sudo setcap CAP_NET_BIND_SERVICE=+eip /usr/local/bin/cloudflared
```

Kenapa menggunakan **setcap**? karena di linux, port di bawah 1024 dianggap "memiliki hak istimewa" dan hanya dapat diikat dengan pengguna yang sama-sama memiliki hak istimewa (baca: root).

Semua port di atas 1024 termasuk 1024 sendiri "bebas digunakan" oleh siapa pun.

Karena disini saya ingin menggunakan port 53 untuk DNS, maka saya menggunakan setcap, tetapi tolong untuk diperhatikan, karena setcap memberikan hak akses root permanen terhadap suatu akun, kecuali jika kamu ingin memakai port lain seperti contoh konfigurasi diatas yang memakai port 5353, jadi penggunaan setcap tidak diperlukan.

`Sebenarnya ada cara lain selain menggunakan setcap, tetapi tidak akan saya bahas pada kali ini.`

Selanjutnya kita membuat sebuah skrip untuk systemd agar program dapat berjalan otomatis pada saat mesin dinyalakan:

`sudo nano /etc/systemd/system/cloudflared.service`

```
[Unit]
Description=cloudflared DNS over HTTPS proxy
After=syslog.target network-online.target

[Service]
Type=simple
User=cloudflared
EnvironmentFile=/etc/default/cloudflared
ExecStart=/usr/local/bin/cloudflared proxy-dns $CLOUDFLARED_OPTS
Restart=on-failure
RestartSec=10
KillMode=process

[Install]
WantedBy=multi-user.target
```

Aktifkan serta jalankan skrip yang kita buat untuk systemd, dan terakhir cek statusnya:

```sh
sudo systemctl enable cloudflared
sudo systemctl start cloudflared
sudo systemctl status cloudflared
```

![Cloudflared_Status](/i/cloudflared_status.png){:class="image-wrapper-left__list"}

Jika statusnya seperti gambar diatas, berarti program telah sukses aktif dan berjalan.

#### Konfigurasi DNS pada Sistem

Akhirnya masuk tahapan yang terakhir, yaitu merubah Domain Name Server menggunakan ip localhost. Karena menggunakan port 53, jadi ubah saja langsung konfigurasi resolvernya:

`nano /etc/resolv.conf`

Kemudian tambahkan ip localhost ke dalam baris, jangan lupa untuk memberikan tanda **#** terhadap nameserver lainya, agar resolvernya hanya menggunakan localhost sebagai nameserver:

```
nameserver 127.0.0.1
#nameserver  ip.lain.1
#nameserver ip.lain.2
```

Terakhir, gunakan perintah dig untuk melihat hasilnya:

`dig google.com`

Jika hasilnya seperti gambar dibawah, melalui **SERVER** 127.0.0.1, itu tandanya sudah berhasil.

![cek_dig](/i/dig_google.png){:class="image-wrapper-left__list"}