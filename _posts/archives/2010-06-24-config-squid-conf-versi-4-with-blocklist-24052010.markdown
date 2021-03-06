---
title: 'Config Squid Conf Versi 4 with blocklist #24052010'
author: aderana
date: 2010-06-24T07:04:46+07:00
layout: post
link: https://94nr0.wordpress.com/2010/06/24/config-squid-conf-versi-4-with-blocklist-24052010/
category: teknologi
tags:
- squid
- proxy
- windows
- config
teaser: Mencoba fungsi blocklist pada Squid versi 3 Windows.
---

![squid](http://94nr0.files.wordpress.com/2010/06/images.jpg){:class="image-wrapper-left__list"}

Sebulan yang lalu kalau tidak salah ada teman yang nanya tentang blocklist di squid, dia mencoba squid versi 3 di Linux Centos, tetapi fungsi blocklistnya tidak berfungsi dengan baik, akhirnya dia balik lagi menggunakan squid versi 2.7

Saya penasaran, dan akhirnya saya mencoba squid versi 3 windows dengan menambahkan fungsi blocklist, ternyata squid berjalan dengan normal, berikut adalah config yang saya coba buat:

```
###########GanR0 Never Die#############
#file squid.conf

http_port 3128 transparent #ini saya buat untuk transparent proxy
icp_port 3130
forwarded_for On

acl youtube dstdomain .youtube.com
acl speedtest dstdomain .speedtest.net
cache allow youtube
cache allow speedtest

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
access_log C:\squid\var\logs\access.log squid
acl apache rep_header Server ^Apache

visible_hostname roganro.web44.net
hierarchy_stoplist cgi-bin ? .js .jsp
acl QUERY urlpath_regex cgi-bin \? .js .jsp
no_cache deny QUERY

request_header_max_size 200 KB
reply_header_max_size 200 KB
request_body_max_size 0 MB
cache_dir ufs C:\squid\var\cache 2000 16 256
redirect_rewrites_host_header off

acl blocklist url_regex -i "C:\squid\etc\blocklist.txt" #tempat file yang didalamnya terdapat nama web yang di block
http_access deny blocklist
deny_info #(nama web) blocklist #nantinya jika client membuka web yang namanya terdapat didalam file blocklist.txt, maka client akan diarahkan ke nama web tersebut

acl manager proto cache_object
acl localhost src #tentuin sendiri ya IP yang kamu suka
acl localnet src #nih buat client kamu
http_access allow localhost
http_access allow localnet
http_access allow manager localhost
http_access deny manager
acl SSL_ports port 443
acl Safe_ports port 80 443 563 280 488 591 777 210 119 70 21 1025-65535
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

dns_nameservers 8.8.8.8 8.8.4.4 #punyanya om google

negative_ttl 1 minutes
positive_dns_ttl 24 hours

quick_abort_min 0
quick_abort_max 0
quick_abort_pct 100

logfile_rotate 1
append_domain .localhost

memory_pools off
log_icp_queries off
icp_hit_stale on
query_icmp on
reload_into_ims on

pipeline_prefetch on
vary_ignore_expire on

cache_mgr #isi dengan nama sesuka hati anda

###########EOF################
#eof
```

contoh dari penggunaan deny_info
deny_info [http://www.roganro.web44.net/](http://www.roganro.web44.net/) blocklist

contoh nama web yang saya coba block di dalam file blocklist.txt saya

```
\.playboy\.com
\.3gp$
^http:\/\/ads[0-9]\.
^http:\/\/ads\.
penthouse.com
duniasex.com
17tahun.com
bangbros.com
porn.com
illegal.com
esek-esek.com
xxx.com
```

mohon maaf jika masih terdapat kesalahan didalam tulisan saya,
jika ada yang bisa menambahkan, penulis tidak keberatan untuk di kritik untuk saling sharing ilmu squid.