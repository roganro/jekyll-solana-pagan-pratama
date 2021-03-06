---
title: 'Config Squid Conf Versi 3 #29042010'
author: aderana
date: 2010-05-10T14:12:08+07:00
layout: post
link: https://94nr0.wordpress.com/2010/05/10/config-squid-conf-versi-3-29042010/
category: teknologi
tags:
- squid
- windows
- proxy
- config
teaser: Berisi conf squid yang menurut saya cukuplah untuk 2 PC.
---

Saya sempat mengutak-atik conf squid saya yang lama, karena saya merasa kurang puas dengan conf squid saya yang lama. Akhirnya saya menemukan conf squid yang menurut saya cukuplah untuk 2 PC. Untuk lebih lengkapnya, baca penjelasan saya langsung di dalam conf squid dibawah ini.

```
###########GanR0 Never Die#############
#file squid.conf

http_port #isi port yang kamu mau
icp_port #isi port yang kamu suka
forwarded_for On

append_domain .itvps.net
cache_mem 8 MB
cache_swap_low 98%
cache_swap_high 99%
maximum_object_size 16 MB
minimum_object_size 4 KB
maximum_object_size_in_memory 64 KB
ipcache_size 4096
ipcache_low 98%
ipcache_high 99%
fqdncache_size 16384
offline_mode off
cache_replacement_policy heap GDSF
memory_replacement_policy heap GDSF
access_log C:\squid\var\logs\access.log squid #tempat file access log berada
acl apache rep_header Server ^Apache

visible_hostname roganro.web44.net #isi sesuka kamu
hierarchy_stoplist cgi-bin ? .js .jsp
acl QUERY urlpath_regex cgi-bin \? .js .jsp
no_cache deny QUERY

request_header_max_size 200 KB
reply_header_max_size 200 KB
request_body_max_size 0 MB
cache_dir ufs C:\squid\var\cache 1000 16 256 #maksud dari 1000 adalah saya memberi batasan 1GB untuk cache, 16 itu subfolder dari folder cache, 256 itu subfolder dari subfolder yang berisi 16 folder
redirect_rewrites_host_header off

acl manager proto cache_object
acl localhost src #tentuin sendiri ya IP yang kamu suka
acl localnet src #nih buat client kamu
http_access allow localhost
http_access allow localnet
http_access allow manager localhost
http_access deny manager
acl SSL_ports port 443
acl Safe_ports port 80 #http
acl Safe_ports port 21 #ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
http_access allow Safe_ports
http_access deny CONNECT

refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i \.(class|css|js|gif|jpg)$ 10080 100% 43200 override-expire
refresh_pattern -i \.(jpe|jpeg|png|bmp|tif)$ 10080 100% 43200 override-expire
refresh_pattern -i \.(tiff|mov|avi|qt|mpeg)$ 10080 100% 43200 override-expire
refresh_pattern -i \.(mpg|mpe|wav|au|mid)$ 10080 100% 43200 override-expire
refresh_pattern -i \.(zip|gz|arj|lha|lzh)$ 10080 100% 43200 override-expire
refresh_pattern -i \.(rar|tgz|tar|exe|bin)$ 10080 100% 43200 override-expire
refresh_pattern -i \.(hqx|pdf|rtf|doc|swf)$ 10080 100% 43200 override-expire
refresh_pattern -i \.(inc|cab|ad|txt|dll)$ 10080 100% 43200 override-expire
refresh_pattern -i \.(asp|acgi|pl|shtml|php3|php)$ 2 20% 4320 reload-into-ims
refresh_pattern -i \.google\.co\.id$ 1440 100% 3500 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.co\.id$ 1440 100% 3500 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \.mail\.yahoo$ 1440 100% 3500 override-expire override-lastmod reload-into-ims ignore-reload
refresh_pattern -i \? 2 20% 4320 reload-into-ims
refresh_pattern -i cgi-bin 2 20% 4320 reload-into-ims
refresh_pattern . 960 90% 43200 reload-into-ims

dns_nameservers 8.8.8.8 8.8.4.4 #pake punyanya mbah google

cache_mgr roganro@gmail.com

###########EOF################
#eof
```

Mohon maaf kalo penjelasannya kurang lengkap, conf squid ini saya gunakan pada squid untuk Windows yang digunakan hanya untuk 2 PC. Untuk penjelasan menginstall Squid, baca tulisan saya terdahulu disini ->

### [Bikin Proxy Server Di Windows](http://localhost:4000/archives/teknologi/p-116/bikin-proxy-server-di-windows)