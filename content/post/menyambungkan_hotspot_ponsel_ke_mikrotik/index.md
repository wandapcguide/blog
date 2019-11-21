---
title: "Menyambungkan hotspot ponsel ke mikrotik"
date: 2018-01-16T13:48:32+07:00
draft: false
---

hi guys, gimana kabar nya semoga sehat ya. kali ini saya akan membagikan tips untuk kalian semua yang punya routerboard mikrotik dirumah tapi ndak ada ISP, bisa loh pakai hotspot HP android. baik itu root ataupun tidak sama saja. oke mari kita simak cara menyambungkan hotspot ponsel android menjadi input Mikrotik.

bahan-bahan

1. ponsel android yang sudah support hotspot dan terinstal aplikasi termux yang bisa kalian download disini

2. routerboard mikrotik

3. kuota internet

4. pc untuk ngeremot router beserta winbox


langkah-langkah:


A. pada ponsel Android

1. jika sudah di install aplikasi yang anda download tadi dan buka aplikasinya dalam keadaan data seluler hidup

2. tunggu installasi paket termux nya selesai

3. lalu hidupkan hotspot nya

4. ketikan ifconfig di termux nya dan lihat ip di interface wlan0 seperti ini gambar ini

<center><img class="special-img-class" src="/hotspot2mikrotik/1.png" height="1000" width="500" /></center>

<p>5. jika sudah tahu, ingat ingat ya ip hotspot nya. </p>


tahap android sudah selesai, intinya kita hidupkan hotspot dan mencari tahu alamat ip dari hotspot kita


B. pada konfigurasi router

1. input melalui wlan1 maka sepert ini

a. enable wlan1 di interface

b. lalu ke wireless yg berada pada bawah menu interface dan klik pada security profiles

c. klik add (+) lalu ikuti langkah ini

- name : basing

- authenticaition type : (tergantung keamanan wifi nya kalo misal WPA2 PSK ya centang WPA2 PSK saja)

- WPA2 Pre-shared key: isikan password wifi nya

- lalu klik apply dan oke

d. kembali ke interface double klik wlan1

e. lalu ikut langkah ini

- di tab wireless mode : station

- klik scan....

- klik start tunggu hingga muncul nama nama wifinya

- jika muncul, klik nama wifi yng ingin anda ambil untuk jadiin input lalu klik connect

- lalu jika sudah pada security profile pilih yg telah anda buat tadi

- jika sudah klik apply dan oke

f. lalu ke terminal ketikan ini

ip address add address=ip sesuai alamat wifi / hotspot misal hotspot saya 192.168.43.2/24 interface=wlan1

ip address add address=ip buat kita misal 10.10.10.1/30 interface=ether2

ip firewall nat add chain=srcnat out-interface=interface ISP disini kita menggunkanan wlan1 maka isilah wlan1 action=masquerade

ip dns set server=8.8.8.8,8.8.4.4. allow-remote-request=yes

ip route add gateway=ip hotspot td misal 192.168.43.1 (cara ngecek nya dari android pakek termux terus ketik ifconfig dan liat bagian wlan0)

dan untuk hasil nya seperti ini
<center><img class="special-img-class" src="/hotspot2mikrotik/2.png" /></center>

gimana guys, mudah kan  ? dari pada router nganggur mending lanjut oprek aja kasian dianggurin hehe. oke apabila ada salah salah kata mohon maaf, yang ingin ditanyakan silakan berkomentar dibawah ini.  sekian terimakasih. semoga bermanfaat
