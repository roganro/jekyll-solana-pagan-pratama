---
title: Source Npc For Ragnarok
author: aderana
date: 2010-04-25T20:09:41+07:00
layout: post
link: https://94nr0.wordpress.com/2010/04/26/source-npc-for-ragnarok/
category: teknologi
tags:
- foss
- ragnarok
- eathena
- code
teaser: Beberapa contoh Source Code yang dibuat oleh member eAthena.
---

Saya ingin share beberapa npc buatan saya sendiri dan ada beberapa npc buatan eathena yang sudah saya modif, example:

> #### NPC Custom Shop
> 
> ![4_m_reidin_kurs__m_alche_b](/i/4_m_reidin_kurs__m_alche_b.png){:class="image-wrapper"}
> 
> `//===== eAthena Script =======================================`
> 
> `//= Shops`
> 
> `//===== By: ==================================================`
> 
> `//= Pagan`
> 
> `//=======================================================`
> 
> `// Prontera`
> 
> `//=======================================================`
> 
> `itemmall,173,85,4 shop Tukang Jualan Amunisi#prt 832,1750:-1,1751:-1,1752:-1,1753:-1,1754:-1,1755:-1,1756:-1,1757:-1,1758:-1,1759:-1,1760:-1,1761:-1,1762:-1,1763:-1,1764:-1,1765:-1,1766:-1,1767:-1,1768:-1,1769:-1,1770:-1,1771:-1,1772:-1,13200:-1,13201:-1,13202:-1,13203:-1,13204:-1,13205:-1,13206:-1,13207:-1,13250:-1,13251:-1,13252:-1,13253:-1,13254:-1,13255:-1,13256:-1,13257:-1,13258:-1,13259:-1`
> 
> `itemmall,186,85,4 shop Tukang Jualan Potion#prt 749,501:-1,502:-1,503:-1,504:-1,505:-1,506:-1,531:-1,532:-1,533:-1,534:-1,545:-1,546:-1,547:-1,645:-1,656:-1,657:-1,7135:20000,7136:10000,7137:5000,7139:30000,678:100000,7142:200000`


NPC Healer Son
----------------------------------------

![4_f_son.png](/i/4_f_son.png){:class="image-wrapper"}

``` 
//===== eAthena Script =======================================

//= Heal Npc
 
//===== By: ==================================================

//= Lotsa People (1.x)

//===== Current Version: =====================================

//= 3.1

//===== Compatible With: =====================================

//= eAthena 0.1+;

//===== Description: =========================================

//= Healer NPC Which Heals For Free

//===== Additional Comments: =================================

//= 2.0 Duplicates And Changed A Bit you can replace this script file by

//= heal_payment.txt if you want that players have to pay their healings. [Darkchild]

//= 3.0 Changed and edited the script added other warp points of maps. [massdriller]

//= 3.1 Optimized for the greater good. [Kisuka]

//============================================================

prontera,151,187,5 script Penyembuh#h1-1::Penyembuh 756,{
cutin “son”,2;
mes “[Penyembuh]“;
mes “Halo “+ strcharinfo(0) + “,”;
mes “Wah Kondisimu Buruk Sekali”;
mes “Kamu Terlihat Seperti Ingin Disembuhkan”;
mes “Ingin Disembuhkan ?”;
next;
if (select(“Heal:Tidak Terima Kasih”) == 2) {
mes “[Penyembuh]“;
mes “Jika Ingin Disembuhkan, Datanglah Kembali”;
cutin “son”,255;
close;
}

sc_start 29,9000000,10; //Angelus
sc_start 30,9000000,10; //Blessing
sc_start 32,9000000,10; //Inc Agi
sc_start 39,9000000,10; //Kyrie
sc_start 41,9000000,10; //Gloria
skilleffect 74,0; //Effect Magnificat
sc_start 40,9000000,10; //Magnificat
percentheal 100,100;

mes “[Penyembuh]“;
mes “Heal”;
mes “Oke, Sekarang Kamu Sudah Sembuh”;
cutin “son”,255;
close;
}

// ——— NPC Clones ———

morocc,159,96,5 duplicate(Penyembuh) Penyembuh#h1-2 756
ayothaya,155,111,5 duplicate(Penyembuh) Penyembuh#h1-3 756
geffen,121,61,5 duplicate(Penyembuh) Penyembuh#h1-4 756
umbala,94,162,5 duplicate(Penyembuh) Penyembuh#h1-5 756
payon,180,105,5 duplicate(Penyembuh) Penyembuh#h1-6 756
alberta,185,144,5 duplicate(Penyembuh) Penyembuh#h1-7 756
aldebaran,134,123,5 duplicate(Penyembuh) Penyembuh#h1-8 756
izlude,125,118,5 duplicate(Penyembuh) Penyembuh#h1-9 756
xmas,149,136,5 duplicate(Penyembuh) Penyembuh#h1-10 756
comodo,188,162,5 duplicate(Penyembuh) Penyembuh#h1-11 756
amatsu,200,80,5 duplicate(Penyembuh) Penyembuh#h1-12 756
gonryun,164,130,5 duplicate(Penyembuh) Penyembuh#h1-13 756
yuno,145,186,5 duplicate(Penyembuh) Penyembuh#h1-14 756
niflheim,188,180,5 duplicate(Penyembuh) Penyembuh#h1-15 756
louyang,225,103,5 duplicate(Penyembuh) Penyembuh#h1-16 756
einbroch,75,202,5 duplicate(Penyembuh) Penyembuh#h1-17 756
einbech,79,106,5 duplicate(Penyembuh) Penyembuh#h1-18 756
hugel,102,150,5 duplicate(Penyembuh) Penyembuh#h1-19 756
jawaii,138,196,5 duplicate(Penyembuh) Penyembuh#h1-20 756
lighthalzen,163,80,5 duplicate(Penyembuh) Penyembuh#h1-21 756
moscovia,217,199,5 duplicate(Penyembuh) Penyembuh#h1-22 756
rachel,120,146,5 duplicate(Penyembuh) Penyembuh#h1-23 756
veins,230,127,5 duplicate(Penyembuh) Penyembuh#h1-24 756
```


NPC Anti Bot
----------------------------------------

```
scriptANTIBOT-1,{
OnPCLoginEvent:
if(getgmlevel() < 10)
initnpctimer “timer_npc”, getcharid(3);
mes “[•Gan-Ro ANTIBOT•]“;
mes “Hallo ^4233F4″+strcharinfo(0)+”^000000″;
mes “symbol ••••• ini akan berubah warna”;
mes “dan saya akan menunjukkan bagaimana caranya”;
mes “jawablah apa yang akan terjadi”;
mes “Warna symbol ••••• ini”;
mes “akan menjadi jawabanmu”;
setoption 0×1;
setoption 0×40;
atcommand “@noask”;
atcommand “@mute 2 “+strcharinfo(0);
sc_start SC_FREEZE,3200000,0;
pcblockmove getcharid(3),1;
//
percentheal 100,100;
next;
mes “[•Gan-Ro ANTIBOT•]“;
mes “tolong tulis nomor”;
mes “yang sama warnanya dengan warna symbol •••••••••••••••••••• ini”;
next;
setarray .@number, rand (101,200), rand (201,300), rand (301,400), rand (401,500), rand (501,600), rand (601,700);
setarray .@colors$, “^08088A”, “^7401DF”, “DF0101″, “^0B610B”, “^FF8000″;
set .@col, rand(5);
mes “[•Gan-Ro ANTIBOT•]“;
mes “Tulis Nomor Yang Warnanya Sama Dengan Warna Titik Dibawah Ini”;
mes .@colors$[.@col]+”•••••••••••••••••••••••••^000000″;
mes “^DF0101 “+.@number[0]+”^000000″ + “^0B610B “+.@number[1]+”^000000″ + “^08088A “+.@number[2]+”^000000″ + “^FF8000 “+.@number[3]+”^000000″ + “^7401DF “+.@number[4]+” ^000000″;
next;
input .@number2;
next;
if(.@number2 == .@number[@col])
{
mes “[•Gan-Ro ANTIBOT•]“;
mes “Jhancok!! Salah Nomor LU.”;
mes “Kamu Bot…”;
next;
atcommand “@kick ” + strcharinfo(0);
end;
}
mes “[•Gan-Ro ANTIBOT•]“;
mes “Selamat!! ^4233F4″+strcharinfo(0)+”^000000″;
mes “Kamu Bukan Bot”;
mes “Selamat Bersenang-senang di Gan-Ro”;
mes “Tolong Jangan Lupa Memberikan Votting”;
setoption 0×1,0;
setoption 0×40,0;
pcblockmove getcharid(3),0;
sc_end SC_FREEZE;
//
percentheal 100,100;
atcommand “@noask”;
atcommand “@unmute “+strcharinfo(0);
set stop, 1;
close;
}
scripttimer_npc-1,{
OnInit:
set .blocktime_m, 2;
set .blocktime_s, 0;
function SF_Time;
end;
OnTimer1:
announce “You have “+((.block_time_m<10)?”0″:”")+.blocktime_m+” minutes and “+((.block_time_s<10)?”0″:”")+.block_time_s+” seconds left!”, bc_blue|bc_self;
sleep2 999;
SF_Time();
end;
function SF_Time {
set .@minutes, .blocktime_m;
if(!.blocktime_s) set .@seconds, 59;
else set .@seconds, .blocktime_s-1;
do
{
announce “You have “+((.@minutes<10)?”0″:”")+.@minutes+” minutes and “+((.@seconds<10)?”0″:”")+.@seconds+” seconds left!”, bc_blue|bc_self ;
sleep2 1000;
if(!.@seconds && .@minutes)
{
set .@minutes, .@minutes-1;
set .@seconds, 59;
}
else if(.@seconds) set .@seconds, .@seconds-1;
else break;
} while(!stop);
if(!stop)
{
dispbottom “Thats was too slow… cyalater u BOT!”;
atcommand “@kick ” + strcharinfo(0);
}
set stop, 0;
}
}
```