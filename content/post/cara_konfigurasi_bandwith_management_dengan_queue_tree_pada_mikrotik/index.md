---
title: "Cara konfigurasi bandwith management dengan queue tree pada mikrotik"
date: 2018-03-02T14:12:18+07:00
draft: false
---

hi guys, gimana kabar nya ? sehat semua ya pastinya, kali ini saya akan membagi kan cara konfigurasi bandwith management dengan queue tree. kalo anak smk bilang cara setting atau konfigurasi queue tree, hal ini berguna untuk melimit paket supaya pemakain bandwith merata dan bagi yang mau hemat kuota bagi yang input nya melalui dari hotspot atau modem bisa juga :D

jangan lupa baca juga : cara menyambungkan hotspot androi menjadi input mikrotik

bagi anak smk konfigurasi ini adalah salah satu point penting saat penilain kejuruan, makanya saya men-share tips konfigurasi ini. umumnya agar semua kalangan bisa, baiklah tanpa banyak bicara langsung saja ke pembahasan.

1. login ke winbox agar dapat me-remote router nya
2. pastikan router telah tersambung ke internet dengan mensetting address dan gateway terlebih dahulu.
3. untuk memulai melimit bandwith, kita membuat dua mangle terlebih dahulu seperti langkah dibawah ini

>masuk ke menu ip > firewall lalu pilih tab mangle dan klik add (+)
>lalu buat mangle pertama dengan konfigurasi seperti ini

```
chain : forward
src. address : ip ether berapa yang akan kalian limit, misal ether 2 dengan ip 10.10.10.1/30 maka penulisan nya adalah 10.10.10.0/30
action : mark connection
new connection mark : user1
passthrought : centang 
```

>lalu klik ok.
>dan buat lagi mangle kedua dengan menekan tombol add (+) masih di ip > firewall > mangle dengan konfigurasi seperti ini

```
chain : forward
connection mark : user1
action : mark packet
new mark packet : to-user1
passthrought : centang
```


>lalu klik ok

<p>4. untuk mangle sudah selesai, sekarang menuju queue tree nya. untuk queue tree kita juga membuat dua yaitu untuk upload dan download dengan konfigurasi seperti dibawah ini</p>

>klik pada menu queue > queue tree lalu klik tombol add (+) untuk menambahkan queue tree upload
>dan lakukan seperti dibawah ini

```
name : up
parent : ether yang menjadi input misal wlan1 karena saya menggunakan hotspot android untuk menjadi input nya jika kalian dari isp maka isikan ether1
packet marks : to-user1
max limit : 512k atau sesuai kbm dan keinginan kalian
```

>lalu klik ok
>lalu klik tombol add (+) untuk menambah kan queue tree download dan lakukan konfigurasi seperti dibawah ini

```
name : down
parent : ether yang akan kamu limit bandwith nya misal mau ether2 ya isi kan ether2
packet marks : to-user1
max limit : 1024k atau sesuai kbm dan keinginan kalian
```


>lalu klik ok

<p>5. sudah selesai untuk konfigurasi queue tree nya langkah terakhir adalah uji coba nya, silakan kalian untuk streaming, browsing dll. Apakah indikator pada queue tree berjalan ? jik berjalan sepert gambar dibawah ini maka anda berhasil melakukan setting atau konfigurasi queue tree nya</p>


nah, begitu cara setting atau konfigurasi bandwith management dengan queue tree. semoga bermanfaat, jangan lupa untuk tinggalkan komentar jika ada saran, masukan, trouble kita bahas bersama di komentar, dll. sekian dari saya sampai jumpa di tutor berikut nya sampai  jumpa dan terimakasih :D