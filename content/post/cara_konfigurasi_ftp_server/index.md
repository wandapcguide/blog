---
title: "Cara konfigurasi ntp server"
date: 2017-11-20T14:35:54+07:00
draft: false
---

hai guys, apa kabar ? semoga sehat ya. kali ini saya akan mengarhcive tugas tugas sekolah saya yaitu tentang konfigurasi debian. pada kali ini saya akan membahas tentang ntp. apa itu sih ntp ? NTP (Network Time Protocol) adalah protokol yang digunakan untuk sinkronisasi waktu di dalam sebuah jaringan, baik pada jaringan LAN (Local Area Network) maupun pada jaringan Internet. ntp sendiri menggunakan port UDP 123 untuk jalur komunikasi nya. berikut adalah cara konfigurasi ntp pada debian server kalian baik debian 5,6,7,8 kalian. 

ketikan ini untuk menginstall packet ntp dan ntpdate 
```
apt-get install ntp ntpdate 
```

lalu untuk konfigurasi ntp nya ketikan in
```
nano /etc/ntp.conf
```

sekrol kebawah dan cari kata kata ini
```
server 0.debian.pool.ntp.org iburst
server 1.debian.pool.ntp.org iburst
server 2.debian.pool.ntp.org iburst
server 3.debian.pool.ntp.org iburst
```

lalu kasih tanda # didepan katanya dan tambahkan kode ini
```
server 127.127.1.0
fudge 127.127.1.0 staratum 1
```

sehingga menjadi seperti ini 
```
#server 0.debian.pool.ntp.org iburst
#server 1.debian.pool.ntp.org iburst
#server 2.debian.pool.ntp.org iburst
#server 3.debian.pool.ntp.org iburst
server 127.127.1.0
fudge 127.127.1.0 staratum 1 
```

save, lalu restart ntp nya dengan perintah 
```
/etc/init.d/ntp restart
```

untuk menguji nya kalian harus ke komputer klient, dan lakukan di pengaturan date and time kalau windows 7 klik jam >  change date and time settings.. > dan pilih internet time lalu klik advanced setings dan isikan ip dari ip server debian kamu lalu klik update now, jika berhasil atau success  seperti gambar di bawah ini

<center><img class="special-img-class" src="/ntp/1.png" /></center>

