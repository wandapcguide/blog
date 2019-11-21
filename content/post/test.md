---
title: "Konfigurasi limit ekstensi download file pada mikrotik"
date: 2018-03-02T17:05:12+07:00
draft: false
---

hi guys, gimana kabar nya ? sehat kan pasti. kali ini saya akan membawakan materi atau tips untuk melimit download bedasarkan ekstensi file seperti mp3, iso, mp4, rar, zip, exe, dan berbagai macam jenis file lainya atau biasa disebut sama anak smk yaitu konfigurasi limit eksteni. yap, konfigurasi ini masih masuk kedalam bandwith management ( menurut ane ) soalnya dia membatasi packet packet yang keluar untuk mendownload file sehingga kecepatan yang dihasilkan kecil atau lelet.


jangan lupa baca juga : cara konfigurasi queue tree di mikrotik


cara ini berguna bagi kalian semua baik anak smk untuk mata pelajaran nya, atau untuk umum yang mau belajar mikrotik atau menjadi kan mikrotik sebagai hotspot dan ingin me limit dengan metode ini sangat bisa sekali. baiklah tanpa  banyak bicara kita langsung aja ke pembahasan.


1. login ke winbox agar dapat me-remote router nya

2. pastikan router telah tersambung ke internet dengan mensetting address dan gateway terlebih dahulu.

3. untuk melimit ekstensi kita harus membuat layer 7 protocol terlebih dahulu yaitu untuk memanggil nama ekstensi yang akan kita limit dengan cara sepert ini

>buka menu ip > firewall  lalu klik pada tab layer7protocol lalu klik tombol add (+) dan isikan seperti ini ( kita ambil contoh akan memblok mp3 )

>name :  mp3

>regexp : \.(iso)

>lalu klik ok

<p>4. lalu kita membuat mangle yaitu di menu ip > firewall </p>

lalu klik pada tab mangle, karena di konfigurasi ini kita masih berhubungan dengan mangle dan queue tree. dan buat lah 2 mangle seperti dibawah ini

>a. mangle pertama ( ip > firewall > mangle klik add (+) )

>chain : forward

>src address : ip ether berapa yang akan kalian limit ekstensi donwload nya, misal ether 2 dengan ip 10.10.10.1/30 maka penulisan nya adalah 10.10.10.0/30

>layer7protocol : mp3

>action : mark connection

>new mark connection : musik

>passtrought : centang

>lalu klik ok

>b. mangle kedua ( ip > firewall > mangle klik add (+) )

>chain : forward

>connection mark : musik

>action : mark packet

>new mark packet : to-musik

>passtrought : centang

>lalu klik ok

<p>5. lalu untuk memanggil mangle tersebut kita memerlukan queue tree</p>

lalu kita ke menu queue > queue tree
dan buat queue tree seperti ini

>name : mp3

>parent : global

>packet marks : to-musik

>max limit : 64 atau sesuai kbm dan keinginan kalian semakin kecil maka akan semakin lelet speed nya karena akan di 1/8 jadi 64k / 8 = 8Kb/s speed nya

>lalu klik ok

<p>6. sudah selesai untuk konfigurasi limit ekstensi nya langkah terakhir adalah uji coba nya, silakan kalian untuk download file sesuai apa yang anda konfigurasi kan tadi. Apakah indikator pada queue tree berjalan ? jika berjalan sepert gambar dibawah ini maka anda berhasil melakukan setting atau konfigurasi limit ekstensi nya</p>

<center><img class="special-img-class" src="/limit-ekstensi/1.png" /></center>

<p>7. lebih berhasil lagi apa bila download dibatalkan maka indikator tidak berjalan seprti ini. maka anda telah sukses sepenuh nya dalam mengkonfigurasi limit ekstensi bedasarkan file.</p>

<center><img class="special-img-class" src="/limit-ekstensi/2.png" /></center>

note : hanya berlaku situs downlod atau hosting yang masih berbasis http jadi jika kalia mendownload di situs atau site hosting file yang https tidak akan jalan


nah, begitu cara konfigurasi limit ekstensi (mp3, iso, mp4, 3gp segala macem, dll) atau limit download di mikrotik. semoga bermanfaat, jangan lupa untuk tinggalkan komentar jika ada saran, masukan, trouble kita bahas bersama di komentar, dll. sekian dari saya sampai jumpa di tutor berikut nya sampai  jumpa dan terimakasih :D