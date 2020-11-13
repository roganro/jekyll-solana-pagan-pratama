---
title: Bikin Proxy Server Di Windows
author: Pagan
date: 2010-04-25T19:30:08+07:00
layout: post
teaser: Membuat proxy server dengan menggunakan Squid pada sistem operasi Windows.
link: https://94nr0.wordpress.com/2010/04/26/bikin-proxy-server-di-windows/
category: teknologi
tags:
- squid
- windows
- proxy
- config
---

![squid cache][gambar]{:class="image-wrapper"}

Sebelumnya saya akan sedikit membahas apa sih sebenarnya proxy itu, ***Proxy server*** (peladen proxy) adalah sebuah [komputer server][ks]{:target="_blank"} atau [program komputer][pk]{:target="_blank"} yang dapat bertindak sebagai [komputer][pc]{:target="_blank"} lainnya untuk melakukan *request* terhadap content dari [Internet][inter]{:target="_blank"} atau [intranet][intra]{:target="_blank"}. Selanjutnya saya akan memberikan sedikit tutorial untuk membuat proxy server dengan squid.

Berikut merupakan langkah-langkah untuk membuat proxy server:

* Unduh squid terbaru di [http://squid.acmeconsulting.it/][squid]{:target="_blank"},
* Ekstrak di drive mana saja (saya memakai **drive C**),
* Buat file _squid.conf_, dan _mime.conf_,
* Sesudah itu, buka file _squid.conf_, isikan konfigurasi kamu. (saya akan memberi contoh konfigurasi file _squid.conf_ milik saya):

~~~
#file squid.conf
http_port 8080
forwarded_for On
icp_port 0
 
append_domain .itvps.net
cache_mem 128 MB
maximum_object_size 16384 KB
minimum_object_size 4 KB
maximum_object_size_in_memory 2048 KB
fqdncache_size 1024
cache_replacement_policy heap GDSF
memory_replacement_policy heap GDSF
access_log c:/squid/var/logs/access.log squid
acl apache rep_header Server ^Apache
 
visible_hostname roganro.web44.net
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
 
cache_dir ufs c:/squid/var/cache 4500 16 256
redirect_rewrites_host_header off
 
refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern . 0 20% 4320
negative_ttl 1 minutes
 
acl manager proto cache_object
acl server src 192.168.10.112 #ip saya
acl client src 192.168.10.122 #ip client**
http_access allow server
http_access allow client
acl Safe_ports port 80 443 210 119 70 21 1025-65535
acl CONNECT method CONNECT
 
#baris dibawah ini adalah settingan delay pool
acl limited src 192.168.10.112
acl download url_regex -i \.exe$ \.mp3$ \.mp4$ \.tar.gz$ \.gz$ \.tar.bz2$ \.rpm$ \.zip$ \.rar$
acl download url_regex -i \.avi$ \.mpg$ \.mpeg$ \.rm$ \.iso$ \.wav$ \.mov$ \.dat$ \.mpe$ \.mid$
acl download url_regex -i \.midi$ \.rmi$ \.wma$ \.wmv$ \.ogg$ \.ogm$ \.m1v$ \.mp2$ \.mpa$ \.wax$
acl download url_regex -i \.m3u$ \.asx$ \.wpl$ \.wmx$ \.dvr-ms$ \.snd$ \.au$ \.aif$ \.asf$ \.m2v$
acl download url_regex -i \.m2p$ \.ts$ \.tp$ \.trp$ \.div$ \.divx$ \.mod$ \.vob$ \.aob$ \.dts$
acl download url_regex -i \.ac3$ \.cda$ \.vro$ \.deb$ \.spl$ \.swf$
acl youtube dstdomain .youtube.com .googlevideo.com .video.google.com .video.google.com.au
acl youtubeip dst 74.125.15.0/24
acl youtubeip dst 74.125.96.0/24
acl youtubeip dst 64.15.0.0/16
acl youtubeip dst 208.117.253.0/24
cache allow youtube
cache allow youtubeip
cache allow server
 
acl ym dstdomain .messenger.yahoo.com .psq.yahoo.com
acl ym dstdomain .us.il.yimg.com .msg.yahoo.com .pager.yahoo.com
acl ym dstdomain .rareedge.com .ytunnelpro.com .chat.yahoo.com
acl ym dstdomain .voice.yahoo.com
acl ymregex url_regex yupdater.yim ymsgr myspaceim
acl ym dstdomain .skype.com .imvu.com
 
acl store_rewrite_list1 dstdomain mt.google.com mt0.google.com mt1.google.com mt2.google.com
acl store_rewrite_list1 dstdomain mt3.google.com
acl store_rewrite_list1 dstdomain kh.google.com kh0.google.com kh1.google.com kh2.google.com
acl store_rewrite_list1 dstdomain kh3.google.com
acl store_rewrite_list1 dstdomain khm.google.com khm0.google.com khm1.google.com khm2.google.com
acl store_rewrite_list1 dstdomain khm3.google.com
acl store_rewrite_list1 dstdomain kh.google.com.au kh0.google.com.au kh1.google.com.au
acl store_rewrite_list1 dstdomain kh2.google.com.au kh3.google.com.au
 
acl store_rewrite_list dstdomain .youtube.com
 
acl store_rewrite_list2 url_regex ^http://(.*?)/get_video\?
acl store_rewrite_list2 url_regex ^http://(.*?)/videodownload\?
 
refresh_pattern -i \.gz$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.xls$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.doc$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.deb$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.rpm$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.wmp$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.dat$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.msi$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.cab$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.mov$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.bzip2$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.tar.gz$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.zip$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.exe$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.avi$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.asf$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.qtm$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.mid$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.wav$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.viv$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.mpg$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.gif$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.jpg$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.png$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.jpeg$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.dmg$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.rar$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.swf$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.mpeg$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.pdf$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.bmp$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.ad$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.3gp$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.js$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.psf$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.html$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.msi$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.htm$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.css$ 10080 90% 9999 override-expire override-lastmod reload-into-ims ignore-reload
 
cache_mgr roganro@gmail.com
 
#eof
~~~

* Lalu save file tersebut,
* Langkah selanjutnya, yaitu membuka command prompt,
* Klik **start → run → ketik** `cmd`
* **Ketik cd.. → ketik cd.. → ketik** `cd squid/sbin` [^1]
* Ketik `squid.exe -D -z`
* Ketik `squid.exe -i`
* Sehabis itu, **klik start → klik run → ketik** `services.msc`
* Cari yang namanya squid, **klik kanan → klik start**
* Selesai atau Finish.

Untuk konfigurasi proxy di sisi client akan saya bahas pada tutorial selanjutnya, selamat mencoba.

[^1]:
    Saya menaruh folder squidnya di drive C

[ks]: http://id.wikipedia.org/wiki/Server
[pk]: http://id.wikipedia.org/wiki/Program_komputer
[pc]: http://id.wikipedia.org/wiki/Komputer
[inter]: http://id.wikipedia.org/wiki/Internet
[intra]: http://id.wikipedia.org/wiki/Intranet
[squid]: http://squid.acmeconsulting.it/
[gambar]: http://94nr0.files.wordpress.com/2010/04/squid-cache_logo.jpg

