---
title: "Cara Login email pada aplikasi email dari LineageOS based ROM"
date: 2020-03-23T00:30:11+07:00
draft: false
comments: true
---
halo guys, apa kabar nya semua ? semoga sehat selalu ya, Baik orang nya dan juga ponsel nya. Kali ini di kesempatan ini saya ingin berbagi kepada kalian khususnya yang menggunakan custom ROM, karena apa disini saya ingin membagikan cara bagaimana sih login email di aplikasi bawaan email dari custom rom LineageOS. dari pada kalian download lagi aplikasi client email yang lain lebih baik gunakan yang sudah disediakan karena lebih hemat ruang.


jadi untuk login dengan aplikasi ini lebih mudah nya untuk konfigurasi manual, karena kalo otomatis tidak jarang kalian di hadapkan kepada error atau tidak bisa login. untuk karena itu kita harus memperhatikan email dari mana yang kita gunakan, disini saya ambil tiga contoh saja yaitu Gmail, Yahoo mail, dan Outlook. lalu apa yang harus di perhatikan ? adalah protokol nya karena setiap layanan dari masing masing perusahaan yang saya sebutkan tiga tadi memiliki support protokol yang berbeda beda. ada Gmail yang mendukung IMAP, Yahoo mail yang mendukung POP3 dan IMAP, dan outlook yang hanya support POP3 saja. untuk mengetahui lebih lanjut apa itu protokol silakan cek [DISINI](wandapcguide.github.io)


lantas disini saya akan mengambil contoh bagi yang menggunakan Gmail, berikut panduan nya :
1. masukan email terlebih dahulu kemudian klik manual setup, seperti gambar dibawah ini
{{< image src="/login-email/1.png" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
2. lalu pilih PERSONAL (IMAP)
{{< image src="/login-email/2.png" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
3.  kemudian masukan sandi anda
4. lalu kelian akan masuk kedalam menu incoming server dan isikan seperti dibawah ini :
```
server : imap.gmail.com
Security Type : SSL/TLS
port : 993
```
5. klik next, maka kalian akan memasuki menu outgoing server. maka masukan ini :
```
smtp server : smtp.gmail.com
security type : SSL/TLS
port : 465
lalu hilangkan ceklis pada "Require signin"
```
{{< image src="/login-email/3.png" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
6. klik next, dan kalian akan memasuki menu account options dan kemudian rubah sync frequency menjadi "Automatic (push)"
7. klik next, dan tiba lah di final step. kemudian isi nama kalian sebagai tampilan pada pesan terkirim atau outgoing.
8. dan tara.. sudah selesai.
{{< image src="/login-email/4.png" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}
bagaimana ? mudah kan ?? jika kalian menggunakan email dari gmail silakan menyesuaikan, karena saya tidak menggunakan dari layanan lain. dan jika ada pertanyaan, silakan tinggal kan di kolom komentar agar kita belajar bersama sama. sekian dari saya, jangan lupa komentar ya! 