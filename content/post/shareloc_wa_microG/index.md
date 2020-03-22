---
title: "Cara agar dapat share location di whatsapp pada microG"
date: 2020-03-23T00:13:06+07:00
draft: false
comments: true
---
hallo guys, apa kabar nya ? semoga sehat selalu ya. masih membahas tentang microG nih, bagi kalian yang baru menggunakan micorG pasti akan menemukan banyak problem diantaranya ini, yaitu tidak bisa share location di aplikasi WA. jangan menyerah ya, karena di dunia ini tidak ada yang mudah jika belum kita ketahui caranya :D


tidak dapat sync contact yang tersimpan di google ? [baca disini](https://wanda4agustian.blogspot.com/2020/02/cara-sync-nomor-contact-yang-tersimpan.html)
"nah lalu masa saya harus pindah ke "telegram" misalnya, kan rekan rekan saya banyak yang menggunakan WA". tenang, anda masih bisa kok me-share lokasi anda, berikut ini cara cara nya.


1. download Termux di browser atau terminal emulator apa pun.

2. lalu install termux nya atau terminal nya

3. buka Terminal nya dan ketikan
```
su
```

4. kemudian ijinkan akses root dan setelah itu ketikan ini
```
pm grant com.google.android.gms android.permission.ACCESS_FINE_LOCATION

pm grant com.google.android.gms android.permission.ACCESS_COARSE_LOCATION
```

5. kemudian tunggu beberapa saat dan coba cek wa dan lakukan share location kepada kerabat anda.


dan tara, sekarang anda sudah bisa men-share lokasi anda.. hal tsb sudah saya test pada android 10 havoc OS dengan ponsel asus zenfone max pro m1. jika apabila ada yang ingin di tanyakan silakan tinggalkan komentar dibawah. 
