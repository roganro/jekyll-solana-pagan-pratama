---
title: Firewall di Linux
author: aderana
date: 2010-04-25T17:43:33+07:00
layout: post
link: https://94nr0.wordpress.com/2010/04/26/firewall-di-linux/
category: teknologi
tags:
- firewall
- linux
teaser: Menggunakan linux sebagai firewall di dalam jaringan.
---

Linux memiliki fasilitas firewall di kernelnya. Hampir semua distribusi Linux mengkonfigurasikan kernelnya dengan fasilitas firewall. Firewall di Linux dikonfigurasi dengan menggunakan program "ipchains" pada kernel 2.2, "ipfwadm" pada kernel versi 2.0, dan "ipnatctl" serta "iptables" untuk kernel versi 2.3/2.4.

Ipchains berguna untuk memodifikasi tabel firewall di dalam kernel Linux. Kernel Linux kemudian akan menggunakan tabel tersebut sebagai instruksi untuk melakukan sesuatu terhadap paket <dfn>TCP/IP</dfn> yang masuk melalui komputer Linux yang bersangkutan.

Ada tiga macam firewall yang dapat dimodifikasi: input (menyatakan paket yang memasuki sistem Linux anda), output (menyatakan paket yang keluar dari Linux anda), dan forward (menyatakan paket yang melalui Linux anda).

> #### Contoh:
> 
> `ipchains -A input -p tcp –dport 21 -j REJECT`, akan memblokir koneksi ke port 21 (ftp)
> 
> `ipchains -A output -d 199.95.207.0/24 -j REJECT`, akan memblokir koneksi ke doubleclick.net dari sistem Linux anda. 
> 
> `ipchains -F`, ini akan menghapus seluruh aturan firewall yang telah ada sebelumnya,sebaiknya anda jalankan perintah ini sebelum mendefinisikan aturan-aturan firewall anda.

Ipchains adalah program yang cukup kompleks, jika anda ingin mendalaminya, bacalah <dfn>IPCHAINS-HOWTO</dfn> atau man page dari ipchains.

Melindungi Windows dari Serangan dari Internet
--------------------------------------

Versi-versi awal dari Microsoft Windows memiliki banyak kelemahan di subsistem <dfn>TCP/IP</dfn>-nya. Beberapa dari kelemahan-kelemahan ini telah diperbaiki di versi-versi berikutnya, namun Windows masih saja terlalu mudah untuk dibuat bertekuk lutut. Berapa kali anda mengalami kejadian komputer Windows anda tiba-tiba menjadi "biru-biru" ketika anda terhubung ke Internet? Salah satu cara untuk mengatasi kelemahan dari sistem <dfn>TCP/IP</dfn> milik Windows adalah dengan menggunakan firewall Linux sebagai penghubung ke Internet.

Jika komputer Windows anda digunakan sebagai client, cara terbaik untuk melindunginya adalah dengan tidak menghubungkannya secara langsung ke Internet. Anda dapat menggunakan fasilitas <dfn>IP-Masquerading/NAT</dfn> pada Linux, dan menempatkan komputer Windows anda di jaringan internal (dengan IP internal). Komputer Windows anda tidak akan bisa diakses dari Internet dan komputer Windows anda dapet mengakses Internet secara tidak langsung melalui gateway Linux anda. Hampir semua aktivitas sehari-hari yang berhubungan dengan Internet dapat dilakukan dengan konfigurasi seperti ini. Untuk melakukan hal ini gunakan perintah seperti ini:

`ipchains -A forward -s 192.168.0.0/255.255.255.0 -d 0.0.0.0/0 -j MASQ`

perintah tersebut akan melakukan masquerade paket yang datang dari jaringan internal 192.168.0.0/255.255.255.0 ke Internet. Perintah tersebut hanya berlaku jika gateway Linux anda memiliki dua buah interface jaringan, satu menuju jaringan internal anda (umumnya adalah ethernet), dan satu lagi menuju Internet (umumnya adalah link <dfn>PPP</dfn> dial-up atau dedicated). Lihatlah <dfn>IP-Masquerading HOWTO</dfn> untuk penjelasan lebih lanjut.Jika anda menggunakan Windows NT sebagai server, mungkin kasusnya akan lebih rumit. Anda tetap dapat menempatkan Linux box sebagai penghubung ke Internet. Alternatif pertama adalah dengan menggunakan Linux sebagai packet filtering firewall. Yang anda perlu lakukan adalah memblokir paket yang dapat mengkanvaskan sistem Windows anda.

`ipchains -A forward -s 0.0.0.0/0 -d 192.168.0.0/24 -p icmp -j DENY` akan memblokir paket <dfn>ICMP</dfn> yang menuju alamat network 192.168.0.0/24 (jaringan Windows anda), termasuk paket ping-of-death. Namun aturan ini tidak disarankan karena paket <dfn>ICMP</dfn> diperlukan untuk keperluan lain yang penting, jadi sebaiknya yang anda lakukan adalah memperbaiki sistem Windows anda.

Terkadang <dfn>SMB</dfn> server (server yang menangani Microsoft Networking) pada Windows anda tidak dalam keadaan aman. Hal ini dapat dicegah dengan memblokir port 137, 138 dan 139 dengan cara:

`ipchains -A forward -s 0.0.0.0/0 -d 192.168.0.0/24 -p tcp –dport 137:139 -j REJECT`

Namun cara terbaik untuk melindungi Windows adalah dengan memfilter seluruh paket kecuali paket yang diperlukan saja, misalnya jika Windows NT anda berfungsi sebagai web server, anda cukup mengizinkan paket <dfn>TCP</dfn> ke port 80 untuk lewat:

> `ipchains -P forward DENY`
>
> `ipchains -A forward -s 0.0.0.0/0 -d 192.168.0.0/24 -p tcp –dport 80 -j ALLOW`

Perkembangan lebih lanjut dari Linux bahkan mengizinkan server Windows untuk ditempatkan di jaringan internal, jadi tidak secara langsung berhubungan dengan Internet. Fasilitas ini (<dfn>RNAT</dfn>, reverse network address translation) masih dalam tahap pengembangan pada kernel 2.3, lihatlah situs [http://www.samba.org/netfilter/][smb] untuk informasi mengenai fasilitas netfilter pada kernel 2.3/2.4. Jika anda menggunakan kernel 2.0/2.2, lihatlah situs [http://www.suse.de/~mha/HyperNews/get/linux-ip-nat.html][suse] untuk informasi lebih lanjut.

[smb]: http://www.samba.org/netfilter
[suse]: http://www.suse.de/~mha/HyperNews/get/linux-ip-nat.html